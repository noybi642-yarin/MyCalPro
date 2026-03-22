import { useState, useEffect, useRef } from "react";

// Load Vitality fonts
if (typeof document !== "undefined" && !document.getElementById("vitality-fonts")) {
  const link = document.createElement("link");
  link.id = "vitality-fonts";
  link.rel = "stylesheet";
  link.href = "https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:ital,wght@0,400;0,500;0,700;0,800;0,900;1,900&family=Inter:wght@400;500;600;700&display=swap";
  document.head.appendChild(link);
}

// ─── Design tokens (Vitality theme) ─────────────────────────────────────────
const T = {
  primary:       "#006a35",
  primaryDim:    "#005c2d",
  primaryFixed:  "#75f39c",
  primaryFixedDim:"#67e48f",
  onPrimary:     "#cdffd4",
  primaryContainer:"#75f39c",
  onPrimaryContainer:"#00592b",
  secondary:     "#8c4a00",
  secondaryDim:  "#7b4000",
  secondaryContainer:"#ffc69a",
  onSecondaryContainer:"#6f3a00",
  tertiary:      "#4b5d70",
  tertiaryContainer:"#ccdff6",
  surface:       "#f5f6f7",
  surfaceBright: "#ffffff",
  surfaceContainer:"#e6e8ea",
  surfaceContainerLow:"#eff1f2",
  surfaceContainerHigh:"#e0e3e4",
  surfaceContainerHighest:"#dadddf",
  onSurface:     "#2c2f30",
  onSurfaceVariant:"#595c5d",
  outline:       "#757778",
  outlineVariant:"#abadae",
  error:         "#b31b25",
  errorContainer:"#fb5151",
  font: '"Plus Jakarta Sans", "Inter", system-ui, sans-serif',
};

// Legacy alias kept for backward compat with existing code
const C = {
  green: { 50:"#dcfce7", 100:"#bbf7d0", 200:"#86efac", 400:T.primary, 600:T.primaryDim, 900:"#14532d" },
  amber: { 50:"#fef3c7", 100:"#fde68a", 400:T.secondary, 600:T.secondaryDim, 900:"#451a03" },
  coral: { 50:"#fff1f2", 100:"#ffe4e6", 400:"#f43f5e", 600:"#e11d48", 900:"#881337" },
  blue:  { 50:"#eff6ff", 100:"#dbeafe", 400:"#3b82f6", 600:"#1d4ed8", 900:"#1e3a8a" },
  gray:  { 50:T.surface, 100:T.surfaceContainerHigh, 400:T.onSurfaceVariant, 600:T.onSurface, 900:"#0c0f10" },
  teal:  { 50:"#f0fdf4", 100:"#dcfce7", 400:T.tertiary, 600:"#374151", 900:"#052e16" },
};

// ─── Food database – Israeli brands + global staples ────────────────────────
// Each item: { id, name, brand?, cal, p, c, f, unit, cat, aliases[], defaultQty? }
// aliases = extra search terms (nicknames, typos, English, partial names)
const FOOD_DB = [
  // ── Israeli Snacks / Osem / Strauss ──────────────────────────────────────
  { id:101, name:"במבה (אסם)",         brand:"אסם",    cal:544, p:9,  c:57, f:31,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["במבה","bamba","במבא","חטיף בוטנים","במבה אסם","peanut snack"] },
  { id:102, name:"ביסלי גריל (אסם)",   brand:"אסם",    cal:468, p:9,  c:64, f:20,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["ביסלי","bisli","ביסלי גריל","bisli grill","ביסלי בצל","ביסלי פיצה"] },
  { id:103, name:"ביסלי בצל (אסם)",    brand:"אסם",    cal:465, p:8,  c:65, f:19,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["ביסלי בצל","bisli onion"] },
  { id:104, name:"פריגת שוקולד",        brand:"פריגת",  cal:460, p:5,  c:66, f:20,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["פריגת","prigat","עוגיית שוקולד פריגת"] },
  { id:105, name:"שוקוקרים (אסם)",      brand:"אסם",    cal:520, p:7,  c:60, f:28,  unit:"100g", cat:"חטיף",     defaultQty:25,
    aliases:["שוקוקרים","chocokranz","שוקוקרנץ","שוקוקרנס"] },
  { id:106, name:"קרקרים (אסם)",        brand:"אסם",    cal:422, p:10, c:71, f:11,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["קרקרים","crackers","קרקר","kracker"] },
  { id:107, name:"עוגיות אוראו",        brand:"מונדלז", cal:473, p:5,  c:70, f:21,  unit:"100g", cat:"חטיף",     defaultQty:33,
    aliases:["אוראו","oreo","עוגיות שוקולד","oreos"] },
  { id:108, name:"ויפר שוקולד",         brand:"אלית",   cal:512, p:6,  c:61, f:27,  unit:"100g", cat:"חטיף",     defaultQty:35,
    aliases:["ויפר","wafer","וופר","ויפל","wafle"] },
  { id:109, name:"שוקולד מילקה",        brand:"מונדלז", cal:535, p:7,  c:59, f:30,  unit:"100g", cat:"חטיף",     defaultQty:45,
    aliases:["מילקה","milka","שוקולד חלב","milk chocolate"] },
  { id:110, name:"שוקולד עלית",         brand:"אלית",   cal:530, p:8,  c:57, f:31,  unit:"100g", cat:"חטיף",     defaultQty:45,
    aliases:["שוקולד עלית","elite chocolate","אלית"] },

  // ── Dairy – Israeli ───────────────────────────────────────────────────────
  { id:201, name:"קוטג' 5% (תנובה)",   brand:"תנובה",  cal:98,  p:11, c:3,  f:5,   unit:"100g", cat:"חלבון",    defaultQty:200,
    aliases:["קוטג","קוטג'","cottage","קוטג 5","cotage","קוטג 9","קוטג תנובה"] },
  { id:202, name:"גבינה בולגרית 5%",   brand:"טרה",    cal:175, p:15, c:1,  f:12,  unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["בולגרית","גבינה לבנה","bulgarian","בולגרי","גבינה בולגרית"] },
  { id:203, name:"לאבנה 5%",            brand:"כרמל",   cal:142, p:7,  c:4,  f:11,  unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["לאבנה","labneh","לבנה","גבינת שמנת ערבית"] },
  { id:204, name:"יוגורט 1.5% (דנונה)",brand:"דנונה",  cal:59,  p:4,  c:7,  f:1.5, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["יוגורט","yogurt","דנונה","danone","יוגורט טבעי","יוגורט 1.5"] },
  { id:205, name:"שמנת חמוצה 15%",      brand:"תנובה",  cal:161, p:3,  c:4,  f:15,  unit:"100g", cat:"שומנים",   defaultQty:50,
    aliases:["שמנת חמוצה","שמנת","sour cream","שמנת תנובה"] },
  { id:206, name:"גבינה צהובה 28%",     brand:"תנובה",  cal:364, p:23, c:1,  f:30,  unit:"100g", cat:"חלבון",    defaultQty:30,
    aliases:["גבינה צהובה","yellow cheese","גבינה","צ'דר","cheddar","גבינה צהובה תנובה"] },
  { id:207, name:"ריקוטה",              brand:"",        cal:174, p:11, c:3,  f:13,  unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["ריקוטה","ricotta"] },
  { id:208, name:"מוצרלה 22%",          brand:"",        cal:280, p:18, c:2,  f:22,  unit:"100g", cat:"חלבון",    defaultQty:50,
    aliases:["מוצרלה","mozzarella","מוצרה","גבינת פיצה"] },

  // ── Proteins / Meat / Fish ────────────────────────────────────────────────
  { id:301, name:"חזה עוף מבושל",       brand:"",        cal:165, p:31, c:0,  f:3.6, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["חזה עוף","עוף","chicken breast","chicken","עוף מבושל","פילה עוף","עוף צלוי"] },
  { id:302, name:"שניצל עוף מטוגן",     brand:"",        cal:228, p:22, c:12, f:10,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["שניצל","schnitzel","שניצל עוף","שניצל מטוגן","שניצלון"] },
  { id:303, name:"בשר בקר טחון 15%",    brand:"",        cal:215, p:18, c:0,  f:15,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["בשר טחון","קציצות","המבורגר","beef mince","ground beef","פטי","burger"] },
  { id:304, name:"סטייק אנטריקוט",      brand:"",        cal:271, p:26, c:0,  f:18,  unit:"100g", cat:"חלבון",    defaultQty:200,
    aliases:["אנטריקוט","סטייק","steak","entrecote","ריב איי","ribeye"] },
  { id:305, name:"טונה בשמן (מסונן)",   brand:"",        cal:184, p:26, c:0,  f:9,   unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["טונה","tuna","טונה בשמן","tuna can","קופסת טונה"] },
  { id:306, name:"סלמון מבושל",          brand:"",        cal:208, p:20, c:0,  f:13,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["סלמון","salmon","פילה סלמון","סלמון אפוי","סלמון צלוי"] },
  { id:307, name:"ביצה שלמה",            brand:"",        cal:78,  p:6,  c:0.6,f:5,   unit:"יחידה",cat:"חלבון",    defaultQty:1,
    aliases:["ביצה","ביצים","egg","eggs","ביצה קשה","ביצה מקושקשת","חביתה"] },
  { id:308, name:"חביתה (2 ביצים)",      brand:"",        cal:196, p:14, c:2,  f:15,  unit:"מנה",  cat:"חלבון",    defaultQty:1,
    aliases:["חביתה","omelet","אומלט","ביצים מקושקשות"] },

  // ── Carbs / Bread / Grains ─────────────────────────────────────────────────
  { id:401, name:"אורז לבן מבושל",      brand:"",        cal:130, p:2.7,c:28, f:0.3, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["אורז","rice","אורז לבן","אורז מבושל","white rice"] },
  { id:402, name:"אורז מלא מבושל",      brand:"",        cal:112, p:2.6,c:23, f:0.9, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["אורז מלא","brown rice","אורז חום"] },
  { id:403, name:"פיתה",                 brand:"",        cal:275, p:9,  c:55, f:1.5, unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["פיתה","pita","פיתות","לחמניה ערבית"] },
  { id:404, name:"לחם אחיד (פרוסה)",    brand:"אנגל",    cal:67,  p:2.5,c:12, f:1,   unit:"פרוסה",cat:"פחמימות",  defaultQty:2,
    aliases:["לחם","לחם אחיד","לחם לבן","bread","לחם אנגל","פרוסת לחם","טוסט"] },
  { id:405, name:"לחם מלא (פרוסה)",     brand:"",        cal:80,  p:3.5,c:14, f:1.5, unit:"פרוסה",cat:"פחמימות",  defaultQty:2,
    aliases:["לחם מלא","whole bread","לחם שחור","לחם כוסמין"] },
  { id:406, name:"שיבולת שועל",          brand:"",        cal:389, p:17, c:66, f:7,   unit:"100g", cat:"פחמימות",  defaultQty:80,
    aliases:["שיבולת שועל","oats","oatmeal","גרנולה","קוואקר","quaker","דגני בוקר","פורידג'"] },
  { id:407, name:"פסטה מבושלת",          brand:"",        cal:158, p:5.8,c:31, f:0.9, unit:"100g", cat:"פחמימות",  defaultQty:200,
    aliases:["פסטה","pasta","ספגטי","spaghetti","פנה","penne","פוזילי","fusilli","מקרוני","macaroni"] },
  { id:408, name:"קוסקוס מבושל",         brand:"",        cal:112, p:3.8,c:23, f:0.2, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["קוסקוס","couscous","כוסכוס"] },
  { id:409, name:"קינואה מבושלת",        brand:"",        cal:120, p:4.4,c:22, f:1.9, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["קינואה","quinoa","קינוה"] },
  { id:410, name:"בטטה מבושלת",          brand:"",        cal:86,  p:1.6,c:20, f:0.1, unit:"100g", cat:"פחמימות",  defaultQty:200,
    aliases:["בטטה","sweet potato","בטטה אפויה","סוויט פוטייטו"] },

  // ── Vegetables ────────────────────────────────────────────────────────────
  { id:501, name:"עגבנייה",              brand:"",        cal:18,  p:0.9,c:3.9,f:0.2, unit:"100g", cat:"ירקות",    defaultQty:120,
    aliases:["עגבנייה","עגבניה","tomato","עגבניות","עגבנייה שרי","cherry tomato"] },
  { id:502, name:"מלפפון",               brand:"",        cal:15,  p:0.7,c:3.6,f:0.1, unit:"100g", cat:"ירקות",    defaultQty:120,
    aliases:["מלפפון","cucumber","מלפפונים"] },
  { id:503, name:"גזר",                  brand:"",        cal:41,  p:0.9,c:10, f:0.2, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["גזר","carrot","carrots","גזרים"] },
  { id:504, name:"ברוקולי",              brand:"",        cal:34,  p:2.8,c:7,  f:0.4, unit:"100g", cat:"ירקות",    defaultQty:150,
    aliases:["ברוקולי","broccoli","ברוקולה"] },
  { id:505, name:"תירס מבושל",           brand:"",        cal:96,  p:3.4,c:21, f:1.5, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["תירס","corn","תירס מבושל","תירס קפוא"] },
  { id:506, name:"סלט ירקות",            brand:"",        cal:30,  p:1.5,c:5,  f:0.5, unit:"100g", cat:"ירקות",    defaultQty:150,
    aliases:["סלט","salad","סלט ירקות","ישראלי","סלט ישראלי","chopped salad"] },
  { id:507, name:"תרד",                  brand:"",        cal:23,  p:2.9,c:3.6,f:0.4, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["תרד","spinach","תרד טרי"] },
  { id:508, name:"בצל",                  brand:"",        cal:40,  p:1.1,c:9.3,f:0.1, unit:"100g", cat:"ירקות",    defaultQty:80,
    aliases:["בצל","onion","בצלים","onions"] },
  { id:509, name:"שום",                  brand:"",        cal:149, p:6.4,c:33, f:0.5, unit:"100g", cat:"ירקות",    defaultQty:10,
    aliases:["שום","garlic","שן שום"] },
  { id:510, name:"פלפל אדום",            brand:"",        cal:31,  p:1,  c:7.6,f:0.3, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["פלפל","פלפל אדום","pepper","red pepper","bell pepper","פלפל ירוק","פלפל צהוב"] },

  // ── Fruits ────────────────────────────────────────────────────────────────
  { id:601, name:"בננה",                 brand:"",        cal:89,  p:1.1,c:23, f:0.3, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["בננה","banana","בנאנה","בננות"] },
  { id:602, name:"תפוח",                 brand:"",        cal:52,  p:0.3,c:14, f:0.2, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["תפוח","apple","תפוחים","granny smith"] },
  { id:603, name:"אבוקדו",               brand:"",        cal:160, p:2,  c:9,  f:15,  unit:"100g", cat:"שומנים",   defaultQty:100,
    aliases:["אבוקדו","avocado","אבוקדוס"] },
  { id:604, name:"ענבים",                brand:"",        cal:67,  p:0.6,c:17, f:0.4, unit:"100g", cat:"פירות",    defaultQty:150,
    aliases:["ענבים","grapes","grape","ענב"] },
  { id:605, name:"אבטיח",                brand:"",        cal:30,  p:0.6,c:7.6,f:0.2, unit:"100g", cat:"פירות",    defaultQty:300,
    aliases:["אבטיח","watermelon","watermellon"] },
  { id:606, name:"תות שדה",              brand:"",        cal:32,  p:0.7,c:7.7,f:0.3, unit:"100g", cat:"פירות",    defaultQty:150,
    aliases:["תות","תות שדה","strawberry","strawberries","תותים"] },
  { id:607, name:"מנגו",                 brand:"",        cal:60,  p:0.8,c:15, f:0.4, unit:"100g", cat:"פירות",    defaultQty:150,
    aliases:["מנגו","mango","מנגוס"] },
  { id:608, name:"תמר מג'הול",           brand:"",        cal:282, p:1.8,c:75, f:0.2, unit:"100g", cat:"פירות",    defaultQty:24,
    aliases:["תמר","תמרים","date","dates","מג'הול","medjool","מג'הול"] },

  // ── Spreads & Condiments ──────────────────────────────────────────────────
  { id:701, name:"חומוס מוכן",           brand:"",        cal:166, p:8.9,c:14, f:9.6, unit:"100g", cat:"ממרח",     defaultQty:80,
    aliases:["חומוס","hummus","חומוס ביתי","חומוס מוכן","חומוס מקנה"] },
  { id:702, name:"טחינה גולמית",          brand:"",        cal:570, p:17, c:21, f:50,  unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["טחינה","tahini","טחינה גולמית","tehina","תהינה"] },
  { id:703, name:"ממרח חמאת בוטנים",      brand:"",        cal:588, p:22, c:22, f:50,  unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["חמאת בוטנים","peanut butter","pb","חב\"ב","skippy","jif"] },
  { id:704, name:"ממרח שוקולד (נוטלה)",   brand:"פררו",   cal:539, p:6,  c:57, f:31,  unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["נוטלה","nutella","נוטלה שוקולד","ממרח שוקולד"] },
  { id:705, name:"מיונז",                 brand:"",        cal:680, p:1,  c:1,  f:75,  unit:"100g", cat:"ממרח",     defaultQty:20,
    aliases:["מיונז","mayo","mayonnaise","מאיו"] },
  { id:706, name:"קטשופ",                 brand:"",        cal:112, p:1.5,c:26, f:0.2, unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["קטשופ","ketchup","קצ'אפ"] },
  { id:707, name:"שמן זית",               brand:"",        cal:884, p:0,  c:0,  f:100, unit:"100ml",cat:"שומנים",   defaultQty:15,
    aliases:["שמן זית","olive oil","שמן","oil"] },

  // ── Legumes & Protein Foods ───────────────────────────────────────────────
  { id:801, name:"עדשים מבושלות",          brand:"",        cal:116, p:9,  c:20, f:0.4, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["עדשים","lentils","עדשה","עדשים ירוקות","עדשים כתומות"] },
  { id:802, name:"שעועית לבנה מבושלת",    brand:"",        cal:127, p:8.7,c:22, f:0.5, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["שעועית","beans","שעועית לבנה","פול","faba bean"] },
  { id:803, name:"חומוס (גרגרים מבושל)",  brand:"",        cal:164, p:8.9,c:27, f:2.6, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["גרגרי חומוס","chickpeas","גרגירי חומוס"] },
  { id:804, name:"טופו",                   brand:"",        cal:76,  p:8,  c:1.9,f:4.8, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["טופו","tofu","שעועית סויה"] },
  { id:805, name:"פולי אדמה (אדממה)",     brand:"",        cal:121, p:11, c:8.9,f:5.2, unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["אדממה","edamame","פולי סויה","פול ירוק"] },

  // ── Drinks ───────────────────────────────────────────────────────────────
  { id:901, name:"קפה שחור",              brand:"",        cal:2,   p:0.3,c:0,  f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["קפה","coffee","קפה שחור","אספרסו","espresso","קפה נמס","nescafe","נסקפה","אמריקנו","americano"] },
  { id:902, name:"קפה עם חלב (לאטה)",    brand:"",        cal:90,  p:4,  c:9,  f:3.5, unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["לאטה","קפה חלב","latte","coffee milk","קפוצ'ינו","cappuccino","קפצ'ינו","פלאט וייט","flat white"] },
  { id:903, name:"מיץ תפוזים טבעי",       brand:"",        cal:45,  p:0.7,c:10, f:0.2, unit:"100ml",cat:"שתייה",    defaultQty:200,
    aliases:["מיץ תפוזים","orange juice","מיץ","oj"] },
  { id:904, name:"קוקה קולה (330ml)",     brand:"קוקה קולה",cal:139,p:0,  c:35, f:0,   unit:"פחית", cat:"שתייה",    defaultQty:1,
    aliases:["קולה","קוקה קולה","cola","coke","coca cola","קוקה","פפסי","pepsi"] },
  { id:905, name:"קוקה קולה זירו",        brand:"קוקה קולה",cal:1,  p:0,  c:0,  f:0,   unit:"פחית", cat:"שתייה",    defaultQty:1,
    aliases:["קולה זירו","זירו","zero","coke zero","diet coke","קולה דיאט"] },
  { id:906, name:"חלב 3%",               brand:"תנובה",   cal:61,  p:3.2,c:4.8,f:3.2, unit:"100ml",cat:"שתייה",    defaultQty:200,
    aliases:["חלב","milk","חלב 3","חלב תנובה"] },
  { id:907, name:"מים",                   brand:"",        cal:0,   p:0,  c:0,  f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מים","water"] },

  // ── Israeli Classics ──────────────────────────────────────────────────────
  { id:1001, name:"פלאפל (כדור)",         brand:"",        cal:57,  p:2.3,c:5.5,f:3,   unit:"כדור", cat:"ישראלי",   defaultQty:5,
    aliases:["פלאפל","falafel","כדורי פלאפל","פאלאפל"] },
  { id:1002, name:"שקשוקה",               brand:"",        cal:140, p:7,  c:8,  f:9,   unit:"100g", cat:"ישראלי",   defaultQty:300,
    aliases:["שקשוקה","shakshuka","שקשוקה עם ביצה","שקשוקה ישראלית"] },
  { id:1003, name:"שאורמה (100g)",        brand:"",        cal:217, p:18, c:4,  f:14,  unit:"100g", cat:"ישראלי",   defaultQty:200,
    aliases:["שאורמה","שוארמה","shawarma","שורמה"] },
  { id:1004, name:"קבב בקר",              brand:"",        cal:242, p:20, c:4,  f:16,  unit:"100g", cat:"ישראלי",   defaultQty:150,
    aliases:["קבב","kabab","kebab","קבב בקר","קבאב"] },
  { id:1005, name:"שניצל ירושלמי",        brand:"",        cal:310, p:19, c:22, f:16,  unit:"100g", cat:"ישראלי",   defaultQty:150,
    aliases:["שניצל ירושלמי","jerusalem schnitzel"] },

  // ── Nuts & Seeds ──────────────────────────────────────────────────────────
  { id:1101, name:"שקדים",               brand:"",        cal:579, p:21, c:22, f:50,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["שקדים","almonds","almond","שקד"] },
  { id:1102, name:"אגוזי מלך",           brand:"",        cal:654, p:15, c:14, f:65,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["אגוזי מלך","walnuts","walnut","אגוז"] },
  { id:1103, name:"גרעיני חמניות",        brand:"",        cal:584, p:21, c:20, f:51,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["גרעינים","sunflower seeds","גרעיני חמניות","גרעיני דלעת","seeds"] },

  // ── Fast Food ─────────────────────────────────────────────────────────────
  { id:1201, name:"המבורגר (רגיל)",       brand:"",        cal:354, p:17, c:29, f:18,  unit:"מנה",  cat:"מזון מהיר",defaultQty:1,
    aliases:["המבורגר","hamburger","burger","בורגר","קצ'יינה","קיינה"] },
  { id:1202, name:'פיצה (פרוסה, 1/8)',    brand:"",        cal:266, p:11, c:33, f:10,  unit:"פרוסה",cat:"מזון מהיר",defaultQty:2,
    aliases:["פיצה","pizza","פיצה מרגריטה","פרוסת פיצה","פיצה גבינה"] },
  { id:1203, name:"ספגטי בולונז",         brand:"",        cal:185, p:11, c:22, f:6,   unit:"100g", cat:"מזון מהיר",defaultQty:300,
    aliases:["בולונז","bolognese","ספגטי בולונז","פסטה בולונז","מינסה"] },

  // ── Breakfast ─────────────────────────────────────────────────────────────
  { id:1301, name:"גרנולה",               brand:"",        cal:471, p:10, c:64, f:20,  unit:"100g", cat:"ארוחת בוקר",defaultQty:50,
    aliases:["גרנולה","granola","מיוסלי","muesli"] },
  { id:1302, name:"חמאה",                 brand:"",        cal:717, p:0.9,c:0.1,f:81,  unit:"100g", cat:"ממרח",     defaultQty:10,
    aliases:["חמאה","butter","חמאה מלוחה"] },
  { id:1303, name:"ריבה",                 brand:"",        cal:278, p:0.4,c:69, f:0.1, unit:"100g", cat:"ממרח",     defaultQty:20,
    aliases:["ריבה","jam","marmalade","ריבת תות","ריבת מישמיש"] },

  // ── Soups ─────────────────────────────────────────────────────────────────
  { id:1401, name:"מרק עוף",              brand:"",        cal:72,  p:5,  c:5,  f:3,   unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק עוף","chicken soup","מרק","soup"] },
  { id:1402, name:"מרק עדשים",            brand:"",        cal:95,  p:5.5,c:14, f:2,   unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק עדשים","lentil soup"] },
  { id:1403, name:"מרק בצל",              brand:"",        cal:46,  p:1.5,c:8,  f:1.5, unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק בצל","onion soup"] },
  { id:1404, name:"מרק עגבניות",          brand:"",        cal:65,  p:2,  c:13, f:0.5, unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק עגבניות","tomato soup"] },
  { id:1405, name:"מרק גזר",              brand:"",        cal:55,  p:1,  c:11, f:1.2, unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק גזר","carrot soup"] },

  // ── Jewish / Holiday Foods ────────────────────────────────────────────────
  { id:1501, name:"מצה (יחידה גדולה)",    brand:"",        cal:112, p:3,  c:24, f:0.4, unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["מצה","מצות","matza","matzah","matzot","מצה רגילה","מצה עבה","מצה דקה","לחם עוני"] },
  { id:1502, name:"מצה עם חמאה וריבה",   brand:"",        cal:235, p:4,  c:36, f:9,   unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["מצה עם חמאה","מצה עם ריבה","matza butter"] },
  { id:1503, name:"קניידלך (כדור)",        brand:"",        cal:73,  p:2.5,c:11, f:2,   unit:"כדור", cat:"יהודי",    defaultQty:3,
    aliases:["קניידלך","קניידל","kneidlach","kneidel","קנידלך","matzo ball","matzah ball","כדורי מצה","כדור מצה","matzaball"] },
  { id:1504, name:"גפילטע פיש (פרוסה)",   brand:"",        cal:80,  p:9,  c:6,  f:2,   unit:"פרוסה",cat:"יהודי",    defaultQty:2,
    aliases:["גפילטע פיש","gefilte fish","גפילטע","דג ממולא","gefiltefish"] },
  { id:1505, name:"חריימה (דג ברוטב)",    brand:"",        cal:130, p:14, c:6,  f:5,   unit:"100g", cat:"יהודי",    defaultQty:200,
    aliases:["חריימה","chraime","דג חריף","דג ברוטב עגבניות"] },
  { id:1506, name:"מלוואח",               brand:"",        cal:380, p:8,  c:45, f:19,  unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["מלוואח","מלאוח","malawach","מאלאוואח"] },
  { id:1507, name:"ג'חנון",               brand:"",        cal:320, p:7,  c:38, f:16,  unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["ג'חנון","ג'חנין","jachnun","jachnum","ג'חנון תימני"] },
  { id:1508, name:"בורקס גבינה",          brand:"",        cal:298, p:8,  c:30, f:17,  unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["בורקס","בורקס גבינה","burekas","bourekas","בורקס תפוח אדמה","בורקס פטריות"] },
  { id:1509, name:"סמבוסק",               brand:"",        cal:280, p:7,  c:28, f:16,  unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["סמבוסק","sambusak","סמבוסק גבינה","סמבוסק בשר"] },
  { id:1510, name:"לביבות (לטקס)",        brand:"",        cal:145, p:3,  c:18, f:7,   unit:"יחידה",cat:"יהודי",    defaultQty:3,
    aliases:["לביבות","לטקס","latkes","לביבות תפוח אדמה","latke"] },
  { id:1511, name:"סופגנייה",             brand:"",        cal:290, p:4,  c:38, f:14,  unit:"יחידה",cat:"יהודי",    defaultQty:1,
    aliases:["סופגנייה","סופגניה","sufganiya","sufganiyah","דונאט","donut","doughnut","ג'לי דונאט"] },
  { id:1512, name:"חמין/שולנט",           brand:"",        cal:210, p:10, c:24, f:8,   unit:"100g", cat:"יהודי",    defaultQty:300,
    aliases:["חמין","שולנט","cholent","hamin","שולנט בשר","חמין קלאסי"] },
  { id:1513, name:"קוגל אטריות",          brand:"",        cal:220, p:5,  c:32, f:8,   unit:"100g", cat:"יהודי",    defaultQty:150,
    aliases:["קוגל","כוגל","kugel","קוגל אטריות","noodle kugel"] },

  // ── Sweets & Candies ──────────────────────────────────────────────────────
  { id:1601, name:"גומי (100g)",           brand:"",        cal:330, p:6,  c:77, f:0,   unit:"100g", cat:"ממתקים",   defaultQty:30,
    aliases:["גומי","גומיות","gummy","gummies","גומי דובים","haribo","הריבו","דובוני גומי","worms","תולעי גומי","gummy bears","גומי בטעמים"] },
  { id:1602, name:"סוכריות (100g)",        brand:"",        cal:394, p:0,  c:98, f:0,   unit:"100g", cat:"ממתקים",   defaultQty:20,
    aliases:["סוכריות","candy","lollipop","סוכריה","candies","hard candy"] },
  { id:1603, name:"מרשמלו",               brand:"",        cal:318, p:2,  c:81, f:0,   unit:"100g", cat:"ממתקים",   defaultQty:30,
    aliases:["מרשמלו","marshmallow","מרשמלוס","marshmallows"] },
  { id:1604, name:"ארטיק שוקולד (64g)",   brand:"גליל",    cal:156, p:2,  c:18, f:8,   unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["ארטיק","ארטיק שוקולד","אסקימו","פופסיקל","ice cream bar","גלידת שוקולד"] },
  { id:1605, name:"גלידת וניל בגביע",     brand:"",        cal:207, p:3.5,c:24, f:11,  unit:"100ml",cat:"ממתקים",   defaultQty:100,
    aliases:["גלידה","גלידת וניל","ice cream","vanilla ice cream","גביע גלידה"] },
  { id:1606, name:"שוקולד מריר 70%",      brand:"",        cal:598, p:7.8,c:46, f:43,  unit:"100g", cat:"ממתקים",   defaultQty:25,
    aliases:["שוקולד מריר","dark chocolate","70%","שוקולד 70"] },
  { id:1607, name:"חלבה",                 brand:"",        cal:516, p:12, c:59, f:27,  unit:"100g", cat:"ממתקים",   defaultQty:40,
    aliases:["חלבה","halva","halwa","חלוה"] },
  { id:1608, name:"עוגת שוקולד (פרוסה)",  brand:"",        cal:352, p:5,  c:50, f:16,  unit:"פרוסה",cat:"ממתקים",   defaultQty:1,
    aliases:["עוגת שוקולד","chocolate cake","עוגה","cake","עוגה שוקולדית"] },
  { id:1609, name:"בראוני",               brand:"",        cal:390, p:5,  c:52, f:19,  unit:"100g", cat:"ממתקים",   defaultQty:60,
    aliases:["בראוני","brownie","brownies"] },
  { id:1610, name:"עוגיות שוקו-ביסקו",   brand:"אלית",    cal:490, p:6,  c:68, f:22,  unit:"100g", cat:"ממתקים",   defaultQty:30,
    aliases:["שוקו ביסקו","שוקוביסקו","חברים","elite cookies"] },
  { id:1611, name:"ארז (חטיף אורז)",      brand:"שלגון",   cal:380, p:5,  c:85, f:2,   unit:"100g", cat:"חטיף",     defaultQty:25,
    aliases:["ארז","rice snack","חטיף אורז","אורז מנופח"] },
  { id:1612, name:"צ'יפס מלוח (100g)",    brand:"",        cal:536, p:7,  c:53, f:35,  unit:"100g", cat:"חטיף",     defaultQty:50,
    aliases:["צ'יפס","chips","ציפס","פחיפס","crisps","potato chips","לייز","lays","פרינגלס","pringles","doritos","דוריטוס"] },

  // ── McDonald's Israel ─────────────────────────────────────────────────────
  { id:1701, name:"מק מחבת קלאסי (McDouble)", brand:"מקדונלדס", cal:390, p:22, c:33, f:18, unit:"מנה", cat:"מקדונלדס", defaultQty:1,
    aliases:["מק מחבת","מק דאבל","mcdouble","מקדונלד","מקדונלדס","mcdonalds","מק","mcdonald"] },
  { id:1702, name:"ביג מק",               brand:"מקדונלדס", cal:550, p:25, c:46, f:30,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["ביג מק","big mac","bigmac","ביגמק"] },
  { id:1703, name:"מק צ'יקן",             brand:"מקדונלדס", cal:395, p:15, c:40, f:20,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["מק צ'יקן","mcchicken","מק צ'יקין","chicken burger מק"] },
  { id:1704, name:"צ'יז בורגר (מקדונלדס)",brand:"מקדונלדס", cal:300, p:15, c:32, f:12,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["צ'יז בורגר","cheeseburger","צ'יזבורגר","cheese burger מק"] },
  { id:1705, name:"מק נאגטס ×6",          brand:"מקדונלדס", cal:270, p:15, c:18, f:15,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["נאגטס","nuggets","מק נאגטס","mcnuggets","6 נאגטס","נאגטס עוף"] },
  { id:1706, name:"מק נאגטס ×9",          brand:"מקדונלדס", cal:405, p:22, c:27, f:22,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["9 נאגטס","9 nuggets"] },
  { id:1707, name:'צ\'יפס גדול (מקדונלדס)',brand:"מקדונלדס", cal:490, p:6,  c:63, f:24,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["צ'יפס גדול","large fries","french fries","פריז","large chips מק"] },
  { id:1708, name:'צ\'יפס בינוני (מקדונלדס)',brand:"מקדונלדס",cal:340, p:4,  c:44, f:16,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["צ'יפס בינוני","medium fries","פריז בינוני"] },
  { id:1709, name:"מק פלנט (טבעוני)",     brand:"מקדונלדס", cal:430, p:22, c:38, f:20,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["מק פלנט","mcplant","plant burger","ביגמק טבעוני","טבעוני מקדונלדס"] },
  { id:1710, name:'מקפלורי M&M',           brand:"מקדונלדס", cal:492, p:9,  c:80, f:14,  unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["מקפלורי","mcflurry","מק פלורי","mc flurry","m&m מקדונלדס"] },
  { id:1711, name:"שייק מנגו (בינוני)",   brand:"מקדונלדס", cal:430, p:8,  c:85, f:6,   unit:"מנה",  cat:"מקדונלדס", defaultQty:1,
    aliases:["שייק מנגו","mango shake","שייק","milkshake","מק שייק"] },

  // ── Burger King Israel ────────────────────────────────────────────────────
  { id:1801, name:"וואופר",               brand:"בורגר קינג",cal:657, p:28, c:49, f:40,  unit:"מנה",  cat:"בורגר קינג",defaultQty:1,
    aliases:["וואופר","whopper","וופר","בורגר קינג","burger king","ווופר"] },
  { id:1802, name:"וואופר עם גבינה",      brand:"בורגר קינג",cal:740, p:31, c:50, f:46,  unit:"מנה",  cat:"בורגר קינג",defaultQty:1,
    aliases:["וואופר גבינה","whopper cheese","whopper with cheese"] },
  { id:1803, name:"צ'יפס בינוני (BK)",   brand:"בורגר קינג",cal:380, p:4,  c:48, f:19,  unit:"מנה",  cat:"בורגר קינג",defaultQty:1,
    aliases:["צ'יפס bk","bk fries","בורגר קינג צ'יפס"] },
  { id:1804, name:"אניבל (ישראלי)",       brand:"בורגר קינג",cal:540, p:24, c:42, f:30,  unit:"מנה",  cat:"בורגר קינג",defaultQty:1,
    aliases:["אניבל","anibal","double burger bk"] },

  // ── Pizza Chains (Israel) ─────────────────────────────────────────────────
  { id:1901, name:"פיצה האט – פרוסה גדולה (אמריקאי)", brand:"פיצה האט", cal:298, p:13, c:34, f:12, unit:"פרוסה", cat:"פיצה", defaultQty:2,
    aliases:["פיצה האט","pizza hut","פיצהאט","פיצה הט","hut pizza"] },
  { id:1902, name:"דומינוס – פרוסה (גבינה)",brand:"דומינוס",  cal:272, p:11, c:33, f:10,  unit:"פרוסה",cat:"פיצה",    defaultQty:2,
    aliases:["דומינוס","dominos","domino's","דומינו","דומינוס פיצה","dominos pizza"] },
  { id:1903, name:"פיצה מרגריטה (ביתית)", brand:"",        cal:260, p:11, c:33, f:9,   unit:"פרוסה",cat:"פיצה",    defaultQty:2,
    aliases:["פיצה מרגריטה","margherita","פיצה קלאסית","פיצה רגילה"] },
  { id:1904, name:"פיצה פסטרמי",          brand:"",        cal:295, p:14, c:31, f:13,  unit:"פרוסה",cat:"פיצה",    defaultQty:2,
    aliases:["פיצה פסטרמי","pastrami pizza","פסטרמי"] },
  { id:1905, name:"פיצה פטריות",          brand:"",        cal:250, p:11, c:31, f:9,   unit:"פרוסה",cat:"פיצה",    defaultQty:2,
    aliases:["פיצה פטריות","mushroom pizza","פיצה עם פטריות"] },
  { id:1906, name:"קלזונה",               brand:"",        cal:540, p:22, c:58, f:24,  unit:"יחידה",cat:"פיצה",    defaultQty:1,
    aliases:["קלזונה","calzone","קלצונה"] },
  { id:1907, name:"פיצה בולקה",           brand:"",        cal:170, p:6,  c:24, f:6,   unit:"יחידה",cat:"פיצה",    defaultQty:2,
    aliases:["בולקה","bulka","פיצה בולקה","pizza roll"] },

  // ── KFC Israel ────────────────────────────────────────────────────────────
  { id:2001, name:"כנף עוף KFC",          brand:"KFC",    cal:190, p:12, c:10, f:12,  unit:"יחידה",cat:"KFC",      defaultQty:2,
    aliases:["kfc","קיאף","כנף kfc","kfc chicken","קנטקי","kentucky","kfc wing"] },
  { id:2002, name:"פילה עוף KFC (קריספי)",brand:"KFC",    cal:420, p:26, c:28, f:22,  unit:"יחידה",cat:"KFC",      defaultQty:1,
    aliases:["פילה kfc","kfc fillet","קריספי kfc","crispy chicken kfc"] },
  { id:2003, name:'פופקורן עוף (מנה, 100g)',brand:"KFC",  cal:295, p:20, c:20, f:14,  unit:"מנה",  cat:"KFC",      defaultQty:1,
    aliases:["פופקורן","popcorn chicken","kfc popcorn","פופקורן עוף"] },
  { id:2004, name:"צ'יפס KFC",            brand:"KFC",    cal:360, p:5,  c:48, f:17,  unit:"מנה",  cat:"KFC",      defaultQty:1,
    aliases:["צ'יפס kfc","kfc fries"] },

  // ── Burger / Shakes / Local Israeli Chains ────────────────────────────────
  { id:2101, name:"בורגר ספיידי",         brand:"ספיידי",  cal:620, p:30, c:45, f:35,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["ספיידי","speedy","בורגר ישראלי","ספידי"] },
  { id:2102, name:"שיפודי הדקל (שיפוד עוף)",brand:"",     cal:380, p:28, c:18, f:22,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["שיפוד","שיפודים","שיפוד עוף","grilled chicken skewer","שיפוד בקר"] },
  { id:2103, name:"אסאדו (בשר צלוי)",     brand:"",        cal:320, p:26, c:0,  f:23,  unit:"100g", cat:"מסעדות",   defaultQty:200,
    aliases:["אסאדו","asado","בשר צלוי","גריל"] },
  { id:2104, name:"פיתה עם פלאפל",        brand:"",        cal:410, p:12, c:58, f:15,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["פלאפל בפיתה","פיתה עם פלאפל","פיתה פלאפל"] },
  { id:2105, name:"שאורמה בפיתה",         brand:"",        cal:520, p:28, c:48, f:22,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["שאורמה בפיתה","שוארמה בפיתה","shawarma pita"] },

  // ── Sushi ─────────────────────────────────────────────────────────────────
  { id:2201, name:"מגש סושי (8 פיסות)",   brand:"",        cal:296, p:12, c:50, f:4,   unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["סושי","sushi","מגש סושי","מגש","nori"] },
  { id:2202, name:"ניגירי סלמון (2 יח')", brand:"",        cal:140, p:10, c:18, f:3,   unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["ניגירי","nigiri","ניגירי סלמון"] },
  { id:2203, name:"ראמן (קערה)",           brand:"",        cal:430, p:20, c:55, f:12,  unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["ראמן","ramen","ראמן עוף","ramen noodles"] },
  { id:2204, name:"פד-תאי",               brand:"",        cal:400, p:18, c:50, f:12,  unit:"100g", cat:"סושי",     defaultQty:300,
    aliases:["פד-תאי","pad thai","פאד תאי","מוקפץ"] },

  // ── Israeli Breakfast items ───────────────────────────────────────────────
  { id:2301, name:"שקשוקה (מנה)",         brand:"",        cal:420, p:21, c:24, f:27,  unit:"מנה",  cat:"ישראלי",   defaultQty:1,
    aliases:["שקשוקה","shakshuka","שקשוקה עם פיתה"] },
  { id:2302, name:"ביצה עם לחם (2 ביצים)",brand:"",        cal:340, p:18, c:26, f:16,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["ביצים עם לחם","ביצה ולחם","egg toast","toast egg"] },
  { id:2303, name:"פנקייק (יחידה)",        brand:"",        cal:158, p:4,  c:28, f:4,   unit:"יחידה",cat:"ארוחת בוקר",defaultQty:3,
    aliases:["פנקייק","pancake","pancakes","פנקייקים","חביתית"] },
  { id:2304, name:"וופל",                  brand:"",        cal:291, p:7.9,c:37, f:13,  unit:"יחידה",cat:"ארוחת בוקר",defaultQty:1,
    aliases:["וופל","waffle","וופלים","waffles","וופל בלגי"] },
  { id:2305, name:"חביתת ירקות",           brand:"",        cal:215, p:12, c:8,  f:15,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["חביתת ירקות","vegetable omelet","חביתה עם ירקות"] },
  { id:2306, name:"כריך טונה",             brand:"",        cal:310, p:20, c:28, f:11,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["כריך טונה","tuna sandwich","סנדוויץ טונה","כריך"] },
  { id:2307, name:"כריך גבינה צהובה",      brand:"",        cal:290, p:14, c:29, f:13,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["כריך גבינה","cheese sandwich","סנדוויץ גבינה"] },

  // ── More Snacks / Israeli ─────────────────────────────────────────────────
  { id:2401, name:"טבעולה (תבל)",         brand:"תבל",     cal:498, p:8,  c:59, f:26,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["טבעולה","tivo","טבעולה תבל","cheeto","tzivola"] },
  { id:2402, name:"צ'יטוס",               brand:"פריטו-לי",cal:520, p:6,  c:63, f:27,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["צ'יטוס","cheetos","צ'יטוז","cheeto","flamin hot"] },
  { id:2403, name:"עוגיות אמה",            brand:"",        cal:460, p:6,  c:65, f:20,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["עוגיות אמה","ima cookies","עוגיות ביתיות"] },
  { id:2404, name:"ניילה",                 brand:"עלית",    cal:490, p:7,  c:67, f:22,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["ניילה","nilla","עוגיות ניילה"] },
  { id:2405, name:"אצבעות בודפסט",        brand:"עלית",    cal:475, p:6,  c:68, f:20,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["בודפסט","budapest","אצבעות","אצבעות שוקולד"] },
  { id:2406, name:"פצפוצים",              brand:"",        cal:380, p:6,  c:80, f:3,   unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["פצפוצים","popcorn","פופקורן","popped corn","פצפוץ"] },
  { id:2407, name:"פרצלים",               brand:"",        cal:380, p:9,  c:80, f:2,   unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["פרצלים","pretzels","pretzel","ברצלים"] },
  { id:2408, name:"חטיף גבינה (Cheesybits)",brand:"אסם",   cal:510, p:12, c:55, f:27,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["צ'יזיביטס","cheesybits","חטיף גבינה","גבינה מנופחת"] },

  // ── Protein / Sports ──────────────────────────────────────────────────────
  { id:2501, name:"חלבון מי גבינה (שייק)", brand:"",        cal:120, p:25, c:3,  f:1.5, unit:"מנה",  cat:"ספורט",    defaultQty:1,
    aliases:["פרוטאין","protein","whey","וויי","פרוטין שייק","protein shake","חלבון אבקה","אבקת חלבון"] },
  { id:2502, name:"חטיף חלבון (בר)",       brand:"",        cal:200, p:20, c:22, f:5,   unit:"יחידה",cat:"ספורט",    defaultQty:1,
    aliases:["פרוטאין בר","protein bar","חטיף חלבון","בר חלבון","קינדר בואנו פרוטאין"] },
  { id:2503, name:"אבקת קריאטין",          brand:"",        cal:0,   p:0,  c:0,  f:0,   unit:"כפית", cat:"ספורט",    defaultQty:1,
    aliases:["קריאטין","creatine","אבקת קריאטין"] },
  { id:2504, name:"שייק בננה-קוטג' (ביתי)",brand:"",        cal:320, p:28, c:38, f:4,   unit:"מנה",  cat:"ספורט",    defaultQty:1,
    aliases:["שייק קוטג","שייק בננה","שייק חלבון ביתי","smoothie"] },

  // ── More Proteins ─────────────────────────────────────────────────────────
  { id:2601, name:"ירך עוף (ללא עור)",    brand:"",        cal:177, p:23, c:0,  f:9,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["ירך עוף","chicken thigh","ירך","thigh"] },
  { id:2602, name:"כנפיים (מנה, 200g)",   brand:"",        cal:430, p:40, c:0,  f:30,  unit:"מנה",  cat:"חלבון",    defaultQty:1,
    aliases:["כנפיים","chicken wings","wings","כנפי עוף","ווינגז"] },
  { id:2603, name:"נקניק עוף (יחידה)",    brand:"",        cal:140, p:8,  c:2,  f:12,  unit:"יחידה",cat:"חלבון",    defaultQty:2,
    aliases:["נקניק","נקניקייה","sausage","hot dog","הוט דוג","נקניק עוף","נקניקיה"] },
  { id:2604, name:"פסטרמה (100g)",        brand:"",        cal:116, p:16, c:2,  f:5,   unit:"100g", cat:"חלבון",    defaultQty:80,
    aliases:["פסטרמה","pastrami","פסטרמי","cold cuts"] },
  { id:2605, name:"בייקון (רצועה)",       brand:"",        cal:541, p:37, c:1,  f:42,  unit:"100g", cat:"חלבון",    defaultQty:30,
    aliases:["בייקון","bacon","חזיר מעושן"] },
  { id:2606, name:"דג ניל (טיאפיה)",      brand:"",        cal:96,  p:20, c:0,  f:2,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["טיאפיה","tilapia","דג ניל","דג לבן"] },
  { id:2607, name:"דג מוסר ים",           brand:"",        cal:124, p:19, c:0,  f:5,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["מוסר ים","sea bass","דג מוסר","bass"] },

  // ── Vegetables extra ──────────────────────────────────────────────────────
  { id:2701, name:"פטריות שמפיניון",      brand:"",        cal:22,  p:3.1,c:3.3,f:0.3, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["פטריות","mushrooms","שמפיניון","פטריה","mushroom"] },
  { id:2702, name:"חציל",                 brand:"",        cal:25,  p:1,  c:6,  f:0.2, unit:"100g", cat:"ירקות",    defaultQty:150,
    aliases:["חציל","eggplant","aubergine","חצילים"] },
  { id:2703, name:"קישוא",                brand:"",        cal:17,  p:1.2,c:3.1,f:0.3, unit:"100g", cat:"ירקות",    defaultQty:150,
    aliases:["קישוא","zucchini","courgette","קישואים"] },
  { id:2704, name:"כרובית",               brand:"",        cal:25,  p:1.9,c:5,  f:0.3, unit:"100g", cat:"ירקות",    defaultQty:150,
    aliases:["כרובית","cauliflower","כרוביות"] },
  { id:2705, name:"כרוב",                 brand:"",        cal:25,  p:1.3,c:6,  f:0.1, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["כרוב","cabbage","כרוב לבן","כרוב סגול","red cabbage"] },
  { id:2706, name:"בטטה צלויה",           brand:"",        cal:90,  p:2,  c:21, f:0.1, unit:"100g", cat:"ירקות",    defaultQty:200,
    aliases:["בטטה צלויה","roasted sweet potato","בטטה בתנור"] },
  { id:2707, name:"תפוח אדמה מבושל",      brand:"",        cal:87,  p:1.9,c:20, f:0.1, unit:"100g", cat:"פחמימות",  defaultQty:200,
    aliases:["תפוח אדמה","פטאטס","potato","potatoes","תפ\"א","תפא","אלו","aloo"] },
  { id:2708, name:"צ'יפס ביתי (אפוי)",   brand:"",        cal:150, p:3,  c:30, f:2,   unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["צ'יפס ביתי","oven chips","צ'יפס אפוי","home fries"] },

  // ── Drinks extra ──────────────────────────────────────────────────────────
  { id:2801, name:"רד בול (250ml)",        brand:"רד בול",  cal:110, p:1,  c:28, f:0,   unit:"פחית", cat:"שתייה",    defaultQty:1,
    aliases:["רד בול","red bull","אנרגי","energy drink","אנרגייזר","monster","מונסטר"] },
  { id:2802, name:"פוקס (250ml)",          brand:"פוקס",    cal:0,   p:0,  c:0,  f:0,   unit:"פחית", cat:"שתייה",    defaultQty:1,
    aliases:["פוקס","fox drink","פוקס שתייה"] },
  { id:2803, name:"מיץ ענבים (200ml)",     brand:"",        cal:130, p:0.5,c:32, f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מיץ ענבים","grape juice","מיץ"] },
  { id:2804, name:"שייק פירות (250ml)",    brand:"",        cal:160, p:2,  c:38, f:0.5, unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["שייק פירות","fruit shake","smoothie","סמוטי","שייק"] },
  { id:2805, name:"יין אדום (כוס 150ml)", brand:"",        cal:125, p:0.1,c:4,  f:0,   unit:"כוס",  cat:"אלכוהול",  defaultQty:1,
    aliases:["יין","wine","יין אדום","red wine","יין לבן","white wine","כוס יין"] },
  { id:2806, name:"בירה (330ml)",          brand:"",        cal:143, p:1.1,c:13, f:0,   unit:"פחית", cat:"אלכוהול",  defaultQty:1,
    aliases:["בירה","beer","גולדסטאר","goldstar","נשר","nesher","קארלסברג","carlsberg","הייניקן","heineken"] },
  { id:2807, name:"חלב שוקולד (250ml)",   brand:"",        cal:210, p:8,  c:32, f:6,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["חלב שוקולד","שוקולד חם","cocoa","קקאו","מילו","milo","שוקומילק"] },
  { id:2808, name:"תה (כוס)",              brand:"",        cal:2,   p:0,  c:0.5,f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["תה","tea","תה ירוק","green tea","תה שחור","black tea","תה נענע","mint tea","herbal tea"] },
  // ══════════════════════════════════════════════════════════════════════════
  // BATCH 2 – 250 additional products
  // ══════════════════════════════════════════════════════════════════════════

  // ── More Israeli Branded Snacks ───────────────────────────────────────────
  { id:3001, name:"ספירלות גבינה (אסם)",  brand:"אסם",    cal:488, p:11, c:57, f:24,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["ספירלות","spirals","spiralot","ספירלות גבינה","cheese spirals"] },
  { id:3002, name:"טאיסטי (אסם)",          brand:"אסם",    cal:495, p:7,  c:62, f:24,  unit:"100g", cat:"חטיף",     defaultQty:30,
    aliases:["טאיסטי","tasty","tasty snack"] },
  { id:3003, name:"ביסלי פלאפל",           brand:"אסם",    cal:462, p:9,  c:63, f:20,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["ביסלי פלאפל","falafel bisli"] },
  { id:3004, name:"ביסלי פיצה",            brand:"אסם",    cal:460, p:8,  c:64, f:19,  unit:"100g", cat:"חטיף",     defaultQty:40,
    aliases:["ביסלי פיצה","pizza bisli"] },
  { id:3005, name:"שלגון גלידה",            brand:"שלגון",  cal:212, p:3,  c:27, f:10,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["שלגון","shalagon","ice cream bar"] },
  { id:3006, name:"מגנום קלאסיק",          brand:"וול'ס",  cal:280, p:4,  c:24, f:19,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["מגנום","magnum","magnum classic"] },
  { id:3007, name:"קיטקט",                 brand:"נסטלה",  cal:107, p:1.4,c:13, f:5.6, unit:"יחידה",cat:"ממתקים",   defaultQty:2,
    aliases:["קיטקט","kit kat","kitkat","קיט קט"] },
  { id:3008, name:"סניקרס",                brand:"מארס",   cal:250, p:4,  c:33, f:12,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["סניקרס","snickers"] },
  { id:3009, name:"מארס בר",               brand:"מארס",   cal:228, p:2.4,c:35, f:9,   unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["מארס","mars","mars bar"] },
  { id:3010, name:"טוויקס",               brand:"מארס",   cal:250, p:2.5,c:34, f:12,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["טוויקס","twix"] },
  { id:3011, name:"באונטי",               brand:"מארס",   cal:271, p:2.3,c:32, f:15,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["באונטי","bounty","קוקוס שוקולד"] },
  { id:3012, name:"קרמבו",                brand:"עלית",    cal:104, p:1.1,c:17, f:3.6, unit:"יחידה",cat:"ממתקים",   defaultQty:2,
    aliases:["קרמבו","krembo","krembow"] },
  { id:3013, name:"עוגת גבינה (פרוסה)",   brand:"",        cal:321, p:6,  c:27, f:21,  unit:"פרוסה",cat:"ממתקים",   defaultQty:1,
    aliases:["עוגת גבינה","cheesecake","cheese cake"] },
  { id:3014, name:"טירמיסו",              brand:"",        cal:283, p:5.9,c:25, f:18,  unit:"100g", cat:"ממתקים",   defaultQty:150,
    aliases:["טירמיסו","tiramisu"] },
  { id:3015, name:"מקרון",                brand:"",        cal:90,  p:1.5,c:14, f:3.5, unit:"יחידה",cat:"ממתקים",   defaultQty:2,
    aliases:["מקרון","macaron","macaroon"] },
  { id:3016, name:"קאפקייק שוקולד",       brand:"",        cal:305, p:3.5,c:42, f:14,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["קאפקייק","cupcake","מאפין שוקולד"] },
  { id:3017, name:"מאפין אוכמניות",       brand:"",        cal:270, p:4,  c:40, f:11,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["מאפין","muffin","blueberry muffin"] },
  { id:3018, name:"מוס שוקולד",           brand:"",        cal:285, p:4.5,c:30, f:17,  unit:"100g", cat:"ממתקים",   defaultQty:100,
    aliases:["מוס שוקולד","chocolate mousse","מוס"] },
  { id:3019, name:"שטרודל תפוחים",        brand:"",        cal:268, p:3.5,c:42, f:10,  unit:"100g", cat:"ממתקים",   defaultQty:100,
    aliases:["שטרודל","strudel","apple strudel"] },
  { id:3020, name:"עוגת דבש",             brand:"",        cal:310, p:4,  c:55, f:9,   unit:"100g", cat:"ממתקים",   defaultQty:80,
    aliases:["עוגת דבש","honey cake","lekach","לקח"] },

  // ── Israeli Dairy Extended ────────────────────────────────────────────────
  { id:3101, name:"יוגורט תות שטראוס",   brand:"שטראוס",  cal:96,  p:3.5,c:17, f:1.8, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["יוגורט תות","strawberry yogurt"] },
  { id:3102, name:"גבינת פטה",            brand:"",        cal:264, p:14, c:4,  f:21,  unit:"100g", cat:"חלבון",    defaultQty:50,
    aliases:["פטה","feta","גבינת פטה","feta cheese"] },
  { id:3103, name:"גבינת עיזים",          brand:"",        cal:364, p:22, c:1,  f:30,  unit:"100g", cat:"חלבון",    defaultQty:40,
    aliases:["גבינת עיזים","goat cheese","goat"] },
  { id:3104, name:"גבינה כחולה",          brand:"",        cal:353, p:21, c:2,  f:29,  unit:"100g", cat:"חלבון",    defaultQty:30,
    aliases:["גבינה כחולה","blue cheese","גורגונזולה","gorgonzola","roquefort"] },
  { id:3105, name:"שמנת מתוקה 38%",      brand:"",        cal:340, p:2.1,c:3.4,f:36,  unit:"100ml",cat:"שומנים",   defaultQty:30,
    aliases:["שמנת מתוקה","heavy cream","קצפת","whipping cream"] },
  { id:3106, name:"גבינה פרמז'ן",        brand:"",        cal:431, p:38, c:4,  f:29,  unit:"100g", cat:"חלבון",    defaultQty:20,
    aliases:["פרמז'ן","parmesan","parmezan","פרמזן"] },
  { id:3107, name:"חלב גוט דל שומן",     brand:"גוט",     cal:46,  p:3.4,c:5,  f:1,   unit:"100ml",cat:"חלבון",    defaultQty:200,
    aliases:["חלב גוט","gut milk","חלב 1%","חלב דל שומן","חלב 0%"] },

  // ── Grains & Breads Extended ──────────────────────────────────────────────
  { id:3201, name:"לחם שיפון",            brand:"",        cal:259, p:8.5,c:48, f:3.3, unit:"100g", cat:"פחמימות",  defaultQty:60,
    aliases:["לחם שיפון","rye bread","שיפון"] },
  { id:3202, name:"לחמניה בולקה",         brand:"",        cal:266, p:9,  c:50, f:3.2, unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["לחמניה","roll","בולקה","bun"] },
  { id:3203, name:"קרואסון חמאה",         brand:"",        cal:406, p:8.2,c:46, f:21,  unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["קרואסון","croissant","crescent"] },
  { id:3204, name:"בייגל ירושלמי",        brand:"",        cal:270, p:9,  c:53, f:2.5, unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["בייגל","bagel","ביגל","ka'ak"] },
  { id:3205, name:"טורטייה קמח",          brand:"",        cal:307, p:8.1,c:52, f:7.4, unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["טורטייה","tortilla","wrap","ראפ"] },
  { id:3206, name:"נאן הודי",             brand:"",        cal:310, p:9,  c:55, f:6.2, unit:"יחידה",cat:"פחמימות",  defaultQty:1,
    aliases:["נאן","naan","nan","לחם הודי"] },
  { id:3207, name:"פריכיות אורז",         brand:"",        cal:387, p:7.9,c:82, f:2.8, unit:"100g", cat:"פחמימות",  defaultQty:30,
    aliases:["פריכיות","rice cakes","rice cake"] },
  { id:3208, name:"כוסמת מבושלת",         brand:"",        cal:92,  p:3.4,c:20, f:0.6, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["כוסמת","buckwheat","גרופן"] },
  { id:3209, name:"פולנטה מבושלת",        brand:"",        cal:70,  p:1.5,c:15, f:0.5, unit:"100g", cat:"פחמימות",  defaultQty:200,
    aliases:["פולנטה","polenta","semolina","סולת"] },
  { id:3210, name:"קינואה מבושלת",        brand:"",        cal:120, p:4.4,c:22, f:1.9, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["קינואה","quinoa"] },
  { id:3211, name:"חלה (פרוסה)",          brand:"",        cal:270, p:8,  c:52, f:3,   unit:"פרוסה",cat:"ארוחת בוקר",defaultQty:2,
    aliases:["חלה","challah","לחם שבת"] },
  { id:3212, name:"ברגול מבושל",          brand:"",        cal:83,  p:3.1,c:18, f:0.2, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["ברגול","bulgur","בורגול","bourghoul"] },
  { id:3213, name:"אמרנט מבושל",          brand:"",        cal:102, p:3.8,c:19, f:1.6, unit:"100g", cat:"פחמימות",  defaultQty:150,
    aliases:["אמרנט","amaranth"] },

  // ── Fruits Extended ───────────────────────────────────────────────────────
  { id:3301, name:"אפרסק",                brand:"",        cal:39,  p:0.9,c:10, f:0.3, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["אפרסק","peach","nectarine","נקטרינה"] },
  { id:3302, name:"שזיף",                 brand:"",        cal:46,  p:0.7,c:11, f:0.3, unit:"יחידה",cat:"פירות",    defaultQty:2,
    aliases:["שזיף","plum"] },
  { id:3303, name:"מלון",                 brand:"",        cal:34,  p:0.8,c:8.2,f:0.2, unit:"100g", cat:"פירות",    defaultQty:200,
    aliases:["מלון","melon","cantaloupe"] },
  { id:3304, name:"אננס",                 brand:"",        cal:50,  p:0.5,c:13, f:0.1, unit:"100g", cat:"פירות",    defaultQty:150,
    aliases:["אננס","pineapple"] },
  { id:3305, name:"קיווי",                brand:"",        cal:61,  p:1.1,c:15, f:0.5, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["קיווי","kiwi"] },
  { id:3306, name:"אוכמניות",             brand:"",        cal:57,  p:0.7,c:14, f:0.3, unit:"100g", cat:"פירות",    defaultQty:100,
    aliases:["אוכמניות","blueberries","blueberry"] },
  { id:3307, name:"פטל",                  brand:"",        cal:52,  p:1.2,c:12, f:0.7, unit:"100g", cat:"פירות",    defaultQty:100,
    aliases:["פטל","raspberries","raspberry"] },
  { id:3308, name:"דובדבן",               brand:"",        cal:50,  p:1,  c:12, f:0.3, unit:"100g", cat:"פירות",    defaultQty:100,
    aliases:["דובדבן","cherries","cherry"] },
  { id:3309, name:"אשכולית",              brand:"",        cal:42,  p:0.8,c:11, f:0.1, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["אשכולית","grapefruit","גרייפרוט","pomelo"] },
  { id:3310, name:"תפוז",                 brand:"",        cal:47,  p:0.9,c:12, f:0.1, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["תפוז","orange","קלמנטינה","clementine","מנדרינה","tangerine"] },
  { id:3311, name:"לימון",                brand:"",        cal:29,  p:1.1,c:9,  f:0.3, unit:"יחידה",cat:"פירות",    defaultQty:1,
    aliases:["לימון","lemon","ליים","lime"] },
  { id:3312, name:"תאנה טרייה",           brand:"",        cal:74,  p:0.7,c:19, f:0.3, unit:"יחידה",cat:"פירות",    defaultQty:2,
    aliases:["תאנה","fig","figs"] },
  { id:3313, name:"פפאיה",               brand:"",        cal:43,  p:0.5,c:11, f:0.3, unit:"100g", cat:"פירות",    defaultQty:150,
    aliases:["פפאיה","papaya"] },
  { id:3314, name:"פסיפלורה",             brand:"",        cal:97,  p:2.2,c:23, f:0.7, unit:"100g", cat:"פירות",    defaultQty:50,
    aliases:["פסיפלורה","passion fruit","גרנדיה"] },
  { id:3315, name:"צימוקים",              brand:"",        cal:300, p:3.1,c:79, f:0.5, unit:"100g", cat:"פירות",    defaultQty:30,
    aliases:["צימוקים","raisins"] },
  { id:3316, name:"משמש מיובש",           brand:"",        cal:241, p:3.4,c:63, f:0.5, unit:"100g", cat:"פירות",    defaultQty:30,
    aliases:["משמש מיובש","dried apricots","משמש","apricot"] },
  { id:3317, name:"ליצ'י",               brand:"",        cal:66,  p:0.8,c:17, f:0.4, unit:"100g", cat:"פירות",    defaultQty:100,
    aliases:["ליצ'י","lychee","litchi"] },

  // ── Vegetables Extended ───────────────────────────────────────────────────
  { id:3401, name:"ארטישוק",              brand:"",        cal:53,  p:2.9,c:12, f:0.2, unit:"יחידה",cat:"ירקות",    defaultQty:1,
    aliases:["ארטישוק","artichoke"] },
  { id:3402, name:"אספרגוס",             brand:"",        cal:20,  p:2.2,c:3.7,f:0.1, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["אספרגוס","asparagus"] },
  { id:3403, name:"סלרי",                brand:"",        cal:14,  p:0.7,c:3,  f:0.2, unit:"100g", cat:"ירקות",    defaultQty:50,
    aliases:["סלרי","celery","כרפס"] },
  { id:3404, name:"אפונה ירוקה",         brand:"",        cal:81,  p:5.4,c:14, f:0.4, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["אפונה","peas","green peas"] },
  { id:3405, name:"שעועית ירוקה",        brand:"",        cal:31,  p:1.8,c:7,  f:0.1, unit:"100g", cat:"ירקות",    defaultQty:120,
    aliases:["שעועית ירוקה","green beans"] },
  { id:3406, name:"כרישה",               brand:"",        cal:61,  p:1.5,c:14, f:0.3, unit:"100g", cat:"ירקות",    defaultQty:80,
    aliases:["כרישה","leek"] },
  { id:3407, name:"פלפל צ'ילי",          brand:"",        cal:40,  p:1.9,c:8.8,f:0.4, unit:"100g", cat:"ירקות",    defaultQty:20,
    aliases:["צ'ילי","chili","פלפל חריף","jalapeno","habanero"] },
  { id:3408, name:"ג'ינג'ר שורש",        brand:"",        cal:80,  p:1.8,c:18, f:0.8, unit:"100g", cat:"ירקות",    defaultQty:10,
    aliases:["ג'ינג'ר","ginger","זנגביל"] },
  { id:3409, name:"בוק צ'וי",            brand:"",        cal:13,  p:1.5,c:2.2,f:0.2, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["בוק צ'וי","bok choy","pak choi","כרוב סיני"] },
  { id:3410, name:"רוקולה",              brand:"",        cal:25,  p:2.6,c:3.7,f:0.7, unit:"100g", cat:"ירקות",    defaultQty:50,
    aliases:["רוקולה","arugula","rocket"] },
  { id:3411, name:"עגבניות מיובשות",     brand:"",        cal:258, p:14, c:55, f:3,   unit:"100g", cat:"ירקות",    defaultQty:30,
    aliases:["עגבניות מיובשות","sun dried tomatoes","dried tomatoes"] },
  { id:3412, name:"זיתים שחורים (10 יח')",brand:"",      cal:115, p:0.8,c:6,  f:11,  unit:"100g", cat:"ירקות",    defaultQty:40,
    aliases:["זיתים","olives","olive","זית"] },
  { id:3413, name:"כרוב",                brand:"",        cal:25,  p:1.3,c:6,  f:0.1, unit:"100g", cat:"ירקות",    defaultQty:100,
    aliases:["כרוב","cabbage","red cabbage","כרוב סגול"] },

  // ── Legumes & Plant Proteins Extended ────────────────────────────────────
  { id:3501, name:"שעועית שחורה מבושלת", brand:"",        cal:132, p:8.9,c:24, f:0.5, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["שעועית שחורה","black beans"] },
  { id:3502, name:"שעועית אדומה מבושלת", brand:"",        cal:127, p:8.7,c:23, f:0.5, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["שעועית אדומה","kidney beans","red beans"] },
  { id:3503, name:"מאש ירוק מבושל",      brand:"",        cal:105, p:7,  c:19, f:0.4, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["מאש","mung beans","מונג בינס"] },
  { id:3504, name:"טמפה",               brand:"",         cal:193, p:19, c:9,  f:11,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["טמפה","tempeh"] },
  { id:3505, name:"סייטן",              brand:"",         cal:370, p:75, c:14, f:1.9, unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["סייטן","seitan","wheat gluten"] },

  // ── Nuts & Seeds Extended ─────────────────────────────────────────────────
  { id:3601, name:"קשיו",               brand:"",         cal:553, p:18, c:30, f:44,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["קשיו","cashew","cashews"] },
  { id:3602, name:"פיסטוקים",           brand:"",         cal:562, p:20, c:28, f:45,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["פיסטוק","pistachios","pistachio"] },
  { id:3603, name:"מקדמיה",             brand:"",         cal:718, p:7.9,c:14, f:76,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["מקדמיה","macadamia"] },
  { id:3604, name:"גרעיני דלעת",        brand:"",         cal:446, p:19, c:54, f:19,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["גרעיני דלעת","pumpkin seeds","pepitas"] },
  { id:3605, name:"גרעיני שומשום",      brand:"",         cal:573, p:17, c:23, f:50,  unit:"100g", cat:"אגוזים",   defaultQty:15,
    aliases:["שומשום","sesame","sesame seeds"] },
  { id:3606, name:"זרעי פשתן",          brand:"",         cal:534, p:18, c:29, f:42,  unit:"100g", cat:"אגוזים",   defaultQty:15,
    aliases:["פשתן","flaxseed","linseed"] },
  { id:3607, name:"זרעי צ'יה",          brand:"",         cal:486, p:17, c:42, f:31,  unit:"100g", cat:"אגוזים",   defaultQty:20,
    aliases:["צ'יה","chia","chia seeds"] },
  { id:3608, name:"חמאת שקדים",         brand:"",         cal:614, p:21, c:19, f:56,  unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["חמאת שקדים","almond butter"] },
  { id:3609, name:"אגוזי ברזיל",        brand:"",         cal:659, p:14, c:12, f:67,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["אגוזי ברזיל","brazil nuts"] },
  { id:3610, name:"אגוז פקאן",          brand:"",         cal:691, p:9,  c:14, f:72,  unit:"100g", cat:"אגוזים",   defaultQty:30,
    aliases:["פקאן","pecan","pecans"] },

  // ── Sauces & Condiments Extended ──────────────────────────────────────────
  { id:3701, name:"חרדל",               brand:"",         cal:66,  p:3.7,c:8,  f:3.3, unit:"100g", cat:"ממרח",     defaultQty:15,
    aliases:["חרדל","mustard","dijon"] },
  { id:3702, name:"רוטב סויה",          brand:"",         cal:53,  p:8.1,c:4.9,f:0.1, unit:"100ml",cat:"ממרח",     defaultQty:15,
    aliases:["רוטב סויה","soy sauce","soya","tamari","teriyaki"] },
  { id:3703, name:"סרירצ'ה",            brand:"",         cal:93,  p:1.9,c:18, f:1.5, unit:"100g", cat:"ממרח",     defaultQty:10,
    aliases:["סרירצ'ה","sriracha","tabasco","hot sauce"] },
  { id:3704, name:"גואקמולה",           brand:"",         cal:150, p:1.9,c:8.6,f:13,  unit:"100g", cat:"ממרח",     defaultQty:80,
    aliases:["גואקמולה","guacamole","guac"] },
  { id:3705, name:"פסטו",               brand:"",         cal:433, p:6,  c:5,  f:44,  unit:"100g", cat:"ממרח",     defaultQty:30,
    aliases:["פסטו","pesto"] },
  { id:3706, name:"דבש",                brand:"",         cal:304, p:0.3,c:82, f:0,   unit:"100g", cat:"ממרח",     defaultQty:20,
    aliases:["דבש","honey"] },
  { id:3707, name:"סילאן",              brand:"",         cal:310, p:0.5,c:80, f:0,   unit:"100g", cat:"ממרח",     defaultQty:20,
    aliases:["סילאן","silan","date syrup","date honey","דבש תמרים"] },
  { id:3708, name:"ממרח זיתים",         brand:"",         cal:445, p:1.2,c:5,  f:47,  unit:"100g", cat:"ממרח",     defaultQty:20,
    aliases:["ממרח זיתים","olive tapenade","tapenade","אוליבדה"] },
  { id:3709, name:"רוטב עגבניות",       brand:"",         cal:80,  p:1.5,c:14, f:2,   unit:"100g", cat:"ממרח",     defaultQty:80,
    aliases:["רוטב עגבניות","tomato sauce","marinara","napolitana"] },
  { id:3710, name:"חומץ תפוחים",        brand:"",         cal:21,  p:0,  c:0.9,f:0,   unit:"100ml",cat:"ממרח",     defaultQty:15,
    aliases:["חומץ תפוחים","apple cider vinegar","acv","חומץ"] },

  // ── International / World Cuisine ─────────────────────────────────────────
  { id:3801, name:"קארי עוף",            brand:"",         cal:180, p:18, c:8,  f:9,   unit:"100g", cat:"מסעדות",   defaultQty:300,
    aliases:["קארי","curry","thai curry","קארי עוף"] },
  { id:3802, name:"תג'ין עוף",           brand:"",         cal:195, p:19, c:14, f:8,   unit:"100g", cat:"מסעדות",   defaultQty:300,
    aliases:["תג'ין","tagine","moroccan","מרוקאי"] },
  { id:3803, name:"מוסקה יוונית",        brand:"",         cal:185, p:9,  c:14, f:11,  unit:"100g", cat:"מסעדות",   defaultQty:250,
    aliases:["מוסקה","moussaka","greek moussaka"] },
  { id:3804, name:"לזניה בשר",           brand:"",         cal:200, p:11, c:18, f:9,   unit:"100g", cat:"מסעדות",   defaultQty:300,
    aliases:["לזניה","lasagna","lasagne"] },
  { id:3805, name:"פלאוו אורז",          brand:"",         cal:175, p:4.5,c:30, f:4.5, unit:"100g", cat:"מסעדות",   defaultQty:250,
    aliases:["פלאוו","pilaf","rice pilaf"] },
  { id:3806, name:"ביריאני",             brand:"",         cal:200, p:8,  c:32, f:5,   unit:"100g", cat:"מסעדות",   defaultQty:300,
    aliases:["ביריאני","biryani","אורז הודי"] },
  { id:3807, name:"גיוזה (6 יח')",      brand:"",         cal:225, p:10, c:28, f:8,   unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["גיוזה","gyoza","potstickers"] },
  { id:3808, name:"ספרינג רול מטוגן",  brand:"",          cal:175, p:4.5,c:17, f:10,  unit:"יחידה",cat:"סושי",     defaultQty:3,
    aliases:["ספרינג רול","spring roll"] },
  { id:3809, name:"פריד ראיס",          brand:"",          cal:163, p:5,  c:26, f:4.5, unit:"100g", cat:"סושי",     defaultQty:300,
    aliases:["פריד ראיס","fried rice","אורז מוקפץ"] },
  { id:3810, name:"נודלס מוקפץ",        brand:"",          cal:138, p:4.5,c:22, f:3.5, unit:"100g", cat:"סושי",     defaultQty:250,
    aliases:["נודלס","noodles","lo mein","chow mein"] },
  { id:3811, name:"קליפורניה רול (8 יח')",brand:"",        cal:255, p:9,  c:38, f:7,   unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["קליפורניה","california roll"] },
  { id:3812, name:"סשימי סלמון (5 יח')", brand:"",         cal:180, p:22, c:0,  f:10,  unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["סשימי","sashimi"] },
  { id:3813, name:"ראמן עוף",            brand:"",         cal:430, p:20, c:55, f:12,  unit:"מנה",  cat:"סושי",     defaultQty:1,
    aliases:["ראמן","ramen"] },
  { id:3814, name:"פד תאי",             brand:"",          cal:400, p:18, c:50, f:12,  unit:"100g", cat:"סושי",     defaultQty:300,
    aliases:["פד-תאי","pad thai","פאד תאי"] },

  // ── Pasta Varieties ───────────────────────────────────────────────────────
  { id:3901, name:"פנה ברוטב עגבניות",   brand:"",         cal:168, p:6,  c:30, f:3,   unit:"100g", cat:"פחמימות",  defaultQty:300,
    aliases:["פנה","penne","pasta tomato"] },
  { id:3902, name:"ספגטי קרבונרה",       brand:"",         cal:340, p:13, c:42, f:13,  unit:"100g", cat:"פחמימות",  defaultQty:300,
    aliases:["קרבונרה","carbonara","spaghetti carbonara"] },
  { id:3903, name:"פסטה אלפרדו",         brand:"",         cal:380, p:12, c:40, f:18,  unit:"100g", cat:"פחמימות",  defaultQty:300,
    aliases:["אלפרדו","alfredo"] },
  { id:3904, name:"גנוצ'י ברוטב",        brand:"",         cal:190, p:5,  c:33, f:4.5, unit:"100g", cat:"פחמימות",  defaultQty:250,
    aliases:["גנוצ'י","gnocchi"] },
  { id:3905, name:"לינגוויני פירות ים",  brand:"",         cal:210, p:14, c:28, f:5,   unit:"100g", cat:"פחמימות",  defaultQty:300,
    aliases:["לינגוויני","linguine","seafood pasta"] },

  // ── Meat Extended ─────────────────────────────────────────────────────────
  { id:4001, name:"פילה הודו",            brand:"",         cal:135, p:29, c:0,  f:1,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["הודו","turkey","turkey breast"] },
  { id:4002, name:"כבד עוף",             brand:"",          cal:172, p:24, c:1,  f:8,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["כבד עוף","chicken liver","כבד","liver"] },
  { id:4003, name:"פילה בקר",            brand:"",          cal:218, p:28, c:0,  f:12,  unit:"100g", cat:"חלבון",    defaultQty:200,
    aliases:["פילה בקר","beef fillet","filet mignon","tenderloin"] },
  { id:4004, name:"כתף כבש",             brand:"",          cal:258, p:25, c:0,  f:17,  unit:"100g", cat:"חלבון",    defaultQty:200,
    aliases:["כבש","lamb","lamb shoulder"] },
  { id:4005, name:"שפונדרה (Short Rib)", brand:"",          cal:295, p:22, c:0,  f:23,  unit:"100g", cat:"חלבון",    defaultQty:200,
    aliases:["שפונדרה","short rib","ריב"] },
  { id:4006, name:"בשר עגל",             brand:"",          cal:172, p:30, c:0,  f:5,   unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["עגל","veal"] },
  { id:4007, name:"חזה ברווז",           brand:"",          cal:201, p:23, c:0,  f:11,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["ברווז","duck","duck breast"] },

  // ── Fish Extended ─────────────────────────────────────────────────────────
  { id:4101, name:"קוד (בקלה)",          brand:"",          cal:82,  p:18, c:0,  f:0.7, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["קוד","cod","בקלה"] },
  { id:4102, name:"מקרל",                brand:"",          cal:205, p:19, c:0,  f:14,  unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["מקרל","mackerel"] },
  { id:4103, name:"שרימפס מבושל",        brand:"",          cal:99,  p:24, c:0,  f:0.3, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["שרימפס","shrimp","prawns","גמבה"] },
  { id:4104, name:"סרדינים בשמן",        brand:"",          cal:208, p:25, c:0,  f:12,  unit:"100g", cat:"חלבון",    defaultQty:100,
    aliases:["סרדינים","sardines"] },
  { id:4105, name:"הליבוט",              brand:"",          cal:111, p:23, c:0,  f:2.3, unit:"100g", cat:"חלבון",    defaultQty:150,
    aliases:["הליבוט","halibut"] },
  { id:4106, name:"אנשובי (בצבצן)",      brand:"",          cal:131, p:20, c:0,  f:4.8, unit:"100g", cat:"חלבון",    defaultQty:30,
    aliases:["אנשובי","anchovy","anchovies"] },

  // ── Israeli / Middle Eastern Extended ─────────────────────────────────────
  { id:4201, name:"מוג'דרה",             brand:"",          cal:145, p:5.5,c:26, f:3,   unit:"100g", cat:"ישראלי",   defaultQty:250,
    aliases:["מוג'דרה","mujadara","עדשים ואורז"] },
  { id:4202, name:"קיבה (כובה)",         brand:"",          cal:260, p:14, c:22, f:12,  unit:"יחידה",cat:"ישראלי",   defaultQty:2,
    aliases:["קיבה","kibbeh","כובה","kubba"] },
  { id:4203, name:"ספיחה (לחמג'ון)",     brand:"",          cal:315, p:14, c:35, f:14,  unit:"יחידה",cat:"ישראלי",   defaultQty:1,
    aliases:["ספיחה","sfiha","lahmacun","לחמג'ון"] },
  { id:4204, name:"ורד גפן (דולמה)",    brand:"",           cal:190, p:7,  c:22, f:8,   unit:"100g", cat:"ישראלי",   defaultQty:200,
    aliases:["ורד גפן","stuffed grape leaves","דולמה","dolma"] },
  { id:4205, name:"טאבולה",             brand:"",            cal:75,  p:2.5,c:12, f:2.3, unit:"100g", cat:"ישראלי",   defaultQty:150,
    aliases:["טאבולה","tabbouleh","tabouleh"] },
  { id:4206, name:"פול מדמס",           brand:"",            cal:110, p:7.6,c:18, f:0.5, unit:"100g", cat:"ישראלי",   defaultQty:200,
    aliases:["פול מדמס","ful medames","פול ערבי"] },

  // ── Breakfast Extended ────────────────────────────────────────────────────
  { id:4301, name:"ביצת עין",            brand:"",           cal:90,  p:6.3,c:0.4,f:7,   unit:"יחידה",cat:"ארוחת בוקר",defaultQty:2,
    aliases:["ביצת עין","fried egg","sunny side up"] },
  { id:4302, name:"פנקייק",              brand:"",            cal:158, p:4,  c:28, f:4,   unit:"יחידה",cat:"ארוחת בוקר",defaultQty:3,
    aliases:["פנקייק","pancake","חביתית"] },
  { id:4303, name:"וופל",               brand:"",             cal:291, p:7.9,c:37, f:13,  unit:"יחידה",cat:"ארוחת בוקר",defaultQty:1,
    aliases:["וופל","waffle","waffles","בלגי"] },
  { id:4304, name:"גרנולה עם יוגורט",  brand:"",             cal:320, p:12, c:48, f:10,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["גרנולה יוגורט","granola yogurt"] },
  { id:4305, name:"אקאי בול",           brand:"",             cal:420, p:8,  c:58, f:18,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["אקאי","acai bowl","acai"] },
  { id:4306, name:"טוסט אבוקדו",        brand:"",             cal:310, p:7,  c:28, f:18,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["טוסט אבוקדו","avocado toast"] },
  { id:4307, name:"בייגל עם גבינת שמנת",brand:"",            cal:340, p:12, c:44, f:13,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["בייגל גבינה שמנת","cream cheese bagel","bagel cream cheese"] },
  { id:4308, name:"שקשוקה ירוקה",       brand:"",             cal:175, p:10, c:12, f:11,  unit:"100g", cat:"ארוחת בוקר",defaultQty:300,
    aliases:["שקשוקה ירוקה","green shakshuka"] },
  { id:4309, name:"כריך BLT",           brand:"",             cal:420, p:18, c:38, f:21,  unit:"מנה",  cat:"ארוחת בוקר",defaultQty:1,
    aliases:["BLT","blt sandwich","bacon lettuce tomato"] },
  { id:4310, name:"עוגיות שיבולת שועל", brand:"",             cal:452, p:8,  c:67, f:18,  unit:"100g", cat:"ממתקים",   defaultQty:40,
    aliases:["עוגיות שיבולת שועל","oatmeal cookies","oat cookies"] },

  // ── Fast Food Extended ────────────────────────────────────────────────────
  { id:4401, name:"בורגר ישראלי מסעדה", brand:"",             cal:580, p:27, c:42, f:32,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["smash burger","סמאש בורגר","בורגר מסעדה"] },
  { id:4402, name:"קסדייה עוף",          brand:"",             cal:480, p:28, c:38, f:22,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["קסדייה","quesadilla","chicken quesadilla"] },
  { id:4403, name:"נאצ'וס",             brand:"",              cal:580, p:10, c:62, f:34,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["נאצ'וס","nachos"] },
  { id:4404, name:"טאקו עוף",           brand:"",              cal:218, p:15, c:22, f:8,   unit:"יחידה",cat:"מסעדות",   defaultQty:2,
    aliases:["טאקו","taco","chicken taco"] },
  { id:4405, name:"בוריטו בשר",         brand:"",              cal:490, p:25, c:55, f:17,  unit:"יחידה",cat:"מסעדות",   defaultQty:1,
    aliases:["בוריטו","burrito","beef burrito"] },
  { id:4406, name:"פיש אנד צ'יפס",     brand:"",              cal:520, p:24, c:48, f:26,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["פיש אנד צ'יפס","fish and chips"] },
  { id:4407, name:"צ'יקן טיקה מסאלה",  brand:"",              cal:195, p:17, c:12, f:9,   unit:"100g", cat:"מסעדות",   defaultQty:300,
    aliases:["טיקה מסאלה","tikka masala","chicken tikka"] },
  { id:4408, name:"שאורמה בלחמניה",     brand:"",              cal:560, p:30, c:46, f:26,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["שאורמה לחמניה","shawarma roll","שוארמה לחמניה"] },
  { id:4409, name:"שניצל מסעדה",        brand:"",              cal:560, p:38, c:30, f:32,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["שניצל מסעדה","restaurant schnitzel"] },
  { id:4410, name:"עוף בתנור (מנה)",    brand:"",              cal:290, p:28, c:5,  f:18,  unit:"מנה",  cat:"מסעדות",   defaultQty:1,
    aliases:["עוף בתנור","roast chicken","roasted chicken"] },

  // ── Soups Extended ────────────────────────────────────────────────────────
  { id:4501, name:"מרק מינסטרונה",      brand:"",              cal:82,  p:3.5,c:14, f:2,   unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מינסטרונה","minestrone","מרק ירקות"] },
  { id:4502, name:"מרק דלעת",           brand:"",              cal:62,  p:1.5,c:12, f:1.5, unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק דלעת","pumpkin soup"] },
  { id:4503, name:"מרק תרד ושמנת",      brand:"",              cal:95,  p:3,  c:7,  f:6,   unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["מרק תרד","spinach soup"] },
  { id:4504, name:"בורשט",              brand:"",              cal:50,  p:2,  c:9,  f:1,   unit:"100ml",cat:"מרק",      defaultQty:300,
    aliases:["בורשט","borscht","beet soup"] },
  { id:4505, name:"מרק פו וייטנמי",    brand:"",               cal:90,  p:6,  c:12, f:2,   unit:"100ml",cat:"מרק",      defaultQty:350,
    aliases:["פו","pho","vietnamese soup"] },
  { id:4506, name:"מרק מיסו",           brand:"",              cal:40,  p:2.5,c:5,  f:1.3, unit:"100ml",cat:"מרק",      defaultQty:250,
    aliases:["מרק מיסו","miso soup","מיסו"] },

  // ── Drinks Extended ───────────────────────────────────────────────────────
  { id:4601, name:"לימונדה (200ml)",    brand:"",               cal:100, p:0,  c:26, f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["לימונדה","lemonade"] },
  { id:4602, name:"מיץ תפוחים",        brand:"",               cal:96,  p:0.1,c:24, f:0.2, unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מיץ תפוחים","apple juice"] },
  { id:4603, name:"מים מוגזים",         brand:"",               cal:0,   p:0,  c:0,  f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מים מוגזים","sparkling water","סודה"] },
  { id:4604, name:"ווסקי (שוט)",        brand:"",               cal:70,  p:0,  c:0,  f:0,   unit:"שוט",  cat:"אלכוהול",  defaultQty:1,
    aliases:["ווסקי","whisky","whiskey","בורבון","bourbon","scotch"] },
  { id:4605, name:"וודקה (שוט)",        brand:"",               cal:64,  p:0,  c:0,  f:0,   unit:"שוט",  cat:"אלכוהול",  defaultQty:1,
    aliases:["וודקה","vodka"] },
  { id:4606, name:"מרגריטה (קוקטייל)", brand:"",               cal:168, p:0.2,c:14, f:0.1, unit:"כוס",  cat:"אלכוהול",  defaultQty:1,
    aliases:["מרגריטה","margarita","קוקטייל"] },
  { id:4607, name:"חלב שיבולת שועל",   brand:"",               cal:47,  p:1,  c:7.5,f:1.5, unit:"100ml",cat:"שתייה",    defaultQty:200,
    aliases:["חלב שיבולת שועל","oat milk","oatly","חלב צמחי"] },
  { id:4608, name:"חלב שקדים",          brand:"",               cal:24,  p:0.5,c:3,  f:1.1, unit:"100ml",cat:"שתייה",    defaultQty:200,
    aliases:["חלב שקדים","almond milk"] },
  { id:4609, name:"קפה קר (קולד ברו)", brand:"",               cal:5,   p:0.5,c:1,  f:0,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["קפה קר","cold brew","קולד ברו","ice coffee","קפה קפוא"] },
  { id:4610, name:"מאצ'ה לאטה",        brand:"",               cal:140, p:3,  c:16, f:6,   unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מאצ'ה","matcha","matcha latte"] },
  { id:4611, name:"ספרייט (330ml)",     brand:"",               cal:139, p:0,  c:35, f:0,   unit:"פחית", cat:"שתייה",    defaultQty:1,
    aliases:["ספרייט","sprite","פאנטה","fanta","7up"] },
  { id:4612, name:"מיץ גזר",            brand:"",               cal:110, p:1.5,c:26, f:0.2, unit:"כוס",  cat:"שתייה",    defaultQty:1,
    aliases:["מיץ גזר","carrot juice"] },

  // ── Sports Extended ───────────────────────────────────────────────────────
  { id:4701, name:"BCAA (אבקה)",        brand:"",               cal:20,  p:5,  c:0,  f:0,   unit:"מנה",  cat:"ספורט",    defaultQty:1,
    aliases:["bcaa","BCAA","amino acids","חומצות אמינו"] },
  { id:4702, name:"גטורייד (500ml)",    brand:"גטורייד",        cal:130, p:0,  c:34, f:0,   unit:"בקבוק",cat:"ספורט",    defaultQty:1,
    aliases:["גטורייד","gatorade","powerade","sports drink","משקה ספורט"] },
  { id:4703, name:"מסה גיינר",          brand:"",               cal:380, p:28, c:52, f:5,   unit:"מנה",  cat:"ספורט",    defaultQty:1,
    aliases:["מסה","mass gainer","גיינר","bulk"] },

  // ── Miscellaneous ─────────────────────────────────────────────────────────
  { id:4801, name:"שמן קוקוס",          brand:"",               cal:892, p:0,  c:0,  f:99,  unit:"100g", cat:"שומנים",   defaultQty:10,
    aliases:["שמן קוקוס","coconut oil"] },
  { id:4802, name:"קוקוס מגורד",        brand:"",               cal:354, p:3.3,c:15, f:33,  unit:"100g", cat:"אגוזים",   defaultQty:20,
    aliases:["קוקוס מגורד","shredded coconut","קוקוס"] },
  { id:4803, name:"שמרים תזונתיים",     brand:"",               cal:325, p:40, c:35, f:6,   unit:"100g", cat:"תבלינים",  defaultQty:10,
    aliases:["שמרים תזונתיים","nutritional yeast","nooch"] },
  { id:4804, name:"כורכום",             brand:"",               cal:354, p:8,  c:65, f:10,  unit:"100g", cat:"תבלינים",  defaultQty:5,
    aliases:["כורכום","turmeric"] },
  { id:4805, name:"לוקסוס גלידה",       brand:"אסם",            cal:248, p:3,  c:30, f:13,  unit:"יחידה",cat:"ממתקים",   defaultQty:1,
    aliases:["לוקסוס","luxus","גלידת לוקסוס"] },
  { id:4806, name:"חמין שולנט",         brand:"",               cal:210, p:10, c:24, f:8,   unit:"100g", cat:"יהודי",    defaultQty:300,
    aliases:["חמין","שולנט","cholent","hamin"] },
  { id:4807, name:"לביבות תפוח אדמה",  brand:"",               cal:145, p:3,  c:18, f:7,   unit:"יחידה",cat:"יהודי",    defaultQty:3,
    aliases:["לביבות","latkes","לביבה","potato pancakes"] },
  { id:4808, name:"קוגל אטריות",        brand:"",               cal:220, p:5,  c:32, f:8,   unit:"100g", cat:"יהודי",    defaultQty:150,
    aliases:["קוגל","kugel","noodle kugel"] },
  { id:4809, name:"עוגיות שיבולת שועל", brand:"",               cal:452, p:8,  c:67, f:18,  unit:"100g", cat:"ממתקים",   defaultQty:40,
    aliases:["עוגיות שיבולת שועל","oatmeal cookies","oat cookies"] },
  { id:4810, name:"שקשוקה (מנה מלאה)",  brand:"",               cal:420, p:21, c:24, f:27,  unit:"מנה",  cat:"ישראלי",   defaultQty:1,
    aliases:["שקשוקה מנה","shakshuka full"] },
];

// ─── Smart fuzzy search ───────────────────────────────────────────────────────
function normalizeHebrew(s) {
  // Strip nikud, normalize some common letter confusions
  return s
    .trim()
    .toLowerCase()
    .replace(/[\u0591-\u05C7]/g, "") // remove nikud
    .replace(/'/g, "'");
}

function searchFoods(query) {
  if (!query || query.trim().length === 0) return FOOD_DB.slice(0, 8);
  const q = normalizeHebrew(query);

  const scored = FOOD_DB.map(food => {
    const name = normalizeHebrew(food.name);
    const brand = normalizeHebrew(food.brand || "");
    const allTerms = [name, brand, ...(food.aliases || []).map(normalizeHebrew)];

    let score = 0;

    // Exact match on alias or name = highest
    if (allTerms.some(t => t === q)) score = 100;
    // Name starts with query
    else if (name.startsWith(q)) score = 90;
    // Any alias starts with query
    else if (allTerms.some(t => t.startsWith(q))) score = 80;
    // Name includes query as word
    else if (name.includes(q)) score = 70;
    // Any alias includes query as substring
    else if (allTerms.some(t => t.includes(q))) score = 60;
    // Partial match: every char in query appears in name in order (fuzzy)
    else if (fuzzyMatch(q, name)) score = 40;
    // Partial match in aliases
    else if (allTerms.some(t => fuzzyMatch(q, t))) score = 30;

    return { food, score };
  });

  return scored
    .filter(s => s.score > 0)
    .sort((a, b) => b.score - a.score)
    .slice(0, 10)
    .map(s => s.food);
}

function fuzzyMatch(query, target) {
  if (query.length < 2) return false;
  let qi = 0;
  for (let i = 0; i < target.length && qi < query.length; i++) {
    if (target[i] === query[qi]) qi++;
  }
  return qi === query.length;
}

// Simulated barcode / photo scan results
const SCAN_RESULTS = {
  barcode: [
    { name:"חטיף בוטנים מלוחים", cal:567, p:26, c:16, f:49, unit:"100g", brand:"תנובה" },
    { name:"יוגורט תות 1.5%",    cal:88,  p:3.5,c:15, f:1.5,unit:"100g", brand:"שטראוס" },
    { name:"ביסקוויטים",          cal:470, p:7,  c:72, f:17, unit:"100g", brand:"עלית" },
  ],
  photo: [
    { name:"גבינה בולגרית",       cal:280, p:18, c:1,  f:22, unit:"100g", brand:"טרה", confidence:92 },
    { name:"חמאת בוטנים",          cal:588, p:22, c:22, f:50, unit:"100g", brand:"נטו", confidence:87 },
    { name:"לחם אחיד",             cal:240, p:8,  c:46, f:2,  unit:"100g", brand:"אנגל", confidence:78 },
  ],
  meal: [
    { items:[
      { name:"אורז לבן",     cal:150, p:3,  c:32, f:0.4,qty:120 },
      { name:"שניצל עוף",    cal:230, p:28, c:12, f:8,  qty:150 },
      { name:"סלט ירקות",    cal:35,  p:2,  c:5,  f:1,  qty:120 },
    ], confidence:81 },
    { items:[
      { name:"פסטה",         cal:170, p:6,  c:33, f:1,  qty:120 },
      { name:"רוטב עגבניות", cal:80,  p:2,  c:14, f:2.5,qty:80  },
      { name:"פרמזן",        cal:60,  p:5,  c:0,  f:4,  qty:15  },
    ], confidence:75 },
  ],
};

// ─── Calculations ────────────────────────────────────────────────────────────
function calcBMR({ age, gender, weight, height }) {
  if (gender === "male")
    return 88.36 + 13.4 * weight + 4.8 * height - 5.7 * age;
  return 447.6 + 9.2 * weight + 3.1 * height - 4.3 * age;
}
const ACTIVITY_FACTORS = {
  sedentary: 1.2, light: 1.375, moderate: 1.55, active: 1.725, very_active: 1.9,
};
function calcTDEE(bmr, activity) {
  return Math.round(bmr * (ACTIVITY_FACTORS[activity] || 1.55));
}
function calcGoals({ tdee, goal }) {
  let cal = tdee;
  if (goal === "lose") cal = tdee - 400;
  if (goal === "gain") cal = tdee + 300;
  return {
    cal: Math.round(cal),
    p: Math.round((cal * 0.30) / 4),
    c: Math.round((cal * 0.40) / 4),
    f: Math.round((cal * 0.30) / 9),
  };
}

// ─── Default data ────────────────────────────────────────────────────────────
const todayKey = () => new Date().toISOString().split("T")[0];

const DEFAULT_PROFILE = {
  name:"", age:30, gender:"male", height:175, weight:80,
  targetWeight:75, activity:"moderate", goal:"lose", diet:"regular",
  trainingDays:3, onboarded:false,
};

const DEFAULT_DIARY = {};

// ─── Icon components ─────────────────────────────────────────────────────────
const Icon = ({ d, size=20, color="currentColor", strokeWidth=1.5 }) => (
  <svg width={size} height={size} viewBox="0 0 24 24" fill="none"
    stroke={color} strokeWidth={strokeWidth} strokeLinecap="round" strokeLinejoin="round">
    <path d={d}/>
  </svg>
);
const HomeIcon  = () => <Icon d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/>;
const BookIcon  = () => <Icon d="M2 3h6a4 4 0 014 4v14a3 3 0 00-3-3H2z M22 3h-6a4 4 0 00-4 4v14a3 3 0 013-3h7z"/>;
const ChartIcon = () => <Icon d="M18 20V10 M12 20V4 M6 20v-6"/>;
const PlusIcon  = () => <Icon d="M12 5v14 M5 12h14" strokeWidth={2}/>;
const UserIcon  = () => <Icon d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2 M12 11a4 4 0 100-8 4 4 0 000 8z"/>;
const CamIcon   = () => <Icon d="M23 19a2 2 0 01-2 2H3a2 2 0 01-2-2V8a2 2 0 012-2h4l2-3h6l2 3h4a2 2 0 012 2z M12 17a4 4 0 100-8 4 4 0 000 8z"/>;
const ScanIcon  = () => <Icon d="M3 9V5h4 M21 9V5h-4 M3 15v4h4 M21 15v4h-4 M7 12h10"/>;
const TrashIcon = () => <Icon d="M3 6h18 M8 6V4h8v2 M19 6l-1 14H6L5 6"/>;
const EditIcon  = () => <Icon d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7 M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4z"/>;
const CheckIcon = () => <Icon d="M20 6L9 17l-5-5" strokeWidth={2}/>;
const BackIcon  = () => <Icon d="M19 12H5 M12 19l-7-7 7-7"/>;

// ─── Helpers ─────────────────────────────────────────────────────────────────
const pct = (val, max) => Math.min(100, Math.round((val / (max||1)) * 100));
const fmt = (n) => Math.round(n);

function ProgressBar({ value, max, color, bg, height=8 }) {
  const p  = pct(value, max);
  const c  = color || T.primary;
  const bg2= bg    || T.surfaceContainerHighest;
  return (
    <div style={{ background:bg2, borderRadius:99, height, overflow:"hidden" }}>
      <div style={{
        width:`${Math.min(100,p)}%`, height:"100%", borderRadius:99,
        background: p > 100 ? T.error : c,
        transition:"width .6s cubic-bezier(.4,0,.2,1)"
      }}/>
    </div>
  );
}

function MacroTag({ label, val, goal, color }) {
  return (
    <div style={{ flex:1, minWidth:0 }}>
      <div style={{ display:"flex", justifyContent:"space-between", marginBottom:4 }}>
        <span style={{ fontSize:12, color:T.onSurfaceVariant }}>{label}</span>
        <span style={{ fontSize:12, fontWeight:600, color }}>{fmt(val)}g</span>
      </div>
      <ProgressBar value={val} max={goal} color={color} bg={color+"22"} height={6}/>
      <div style={{ fontSize:11, color:T.outlineVariant, marginTop:2 }}>/{goal}g</div>
    </div>
  );
}

// ─── Main App ─────────────────────────────────────────────────────────────────
export default function App() {
  const [profile, setProfile] = useState(() => {
    try { return JSON.parse(localStorage.getItem("nt_profile")) || DEFAULT_PROFILE; }
    catch { return DEFAULT_PROFILE; }
  });
  const [diary, setDiary] = useState(() => {
    try { return JSON.parse(localStorage.getItem("nt_diary")) || DEFAULT_DIARY; }
    catch { return DEFAULT_DIARY; }
  });
  const [tab, setTab] = useState("home");
  const [addModal, setAddModal] = useState(null); // null | "method" | "manual" | "barcode" | "photo" | "meal"

  // Persist
  useEffect(() => {
    localStorage.setItem("nt_profile", JSON.stringify(profile));
  }, [profile]);
  useEffect(() => {
    localStorage.setItem("nt_diary", JSON.stringify(diary));
  }, [diary]);

  const bmr    = calcBMR(profile);
  const tdee   = calcTDEE(bmr, profile.activity);
  const goals  = calcGoals({ tdee, goal: profile.goal });

  const today  = todayKey();
  const entries = diary[today] || [];

  const totals = entries.reduce(
    (a, e) => ({ cal:a.cal+e.cal, p:a.p+e.p, c:a.c+e.c, f:a.f+e.f }),
    { cal:0, p:0, c:0, f:0 }
  );

  function addEntry(entry) {
    const e = { ...entry, id:Date.now(), time: new Date().toLocaleTimeString("he-IL",{hour:"2-digit",minute:"2-digit"}) };
    setDiary(d => ({ ...d, [today]: [...(d[today]||[]), e] }));
    setAddModal(null);
  }
  function removeEntry(id) {
    setDiary(d => ({ ...d, [today]: (d[today]||[]).filter(e => e.id !== id) }));
  }

  if (!profile.onboarded)
    return <Onboarding onDone={p => setProfile({ ...p, onboarded:true })} />;

  // ── Top App Bar ──────────────────────────────────────────────────────────
  const tabMeta = {
    home:     { label:"יומן היום" },
    diary:    { label:"יומן אוכל" },
    progress: { label:"התקדמות" },
    profile:  { label:"הפרופיל שלי" },
  };

  return (
    <div dir="rtl" style={{ fontFamily:T.font, maxWidth:480, margin:"0 auto",
      minHeight:"100vh", display:"flex", flexDirection:"column", background:T.surface }}>

      {/* Frosted top bar */}
      <header style={{
        position:"fixed", top:0, left:"50%", transform:"translateX(-50%)",
        width:"100%", maxWidth:480, zIndex:100,
        background:"rgba(245,246,247,0.85)", backdropFilter:"blur(12px)",
        borderBottom:`1px solid ${T.outlineVariant}22`,
      }}>
        <div style={{ height:64, display:"flex", alignItems:"center",
          justifyContent:"space-between", padding:"0 20px" }}>
          <div style={{ display:"flex", alignItems:"center", gap:12 }}>
            <div style={{ width:32, height:32, borderRadius:10, background:T.primary,
              display:"flex", alignItems:"center", justifyContent:"center", fontSize:18 }}>🥗</div>
            <span style={{ fontSize:22, fontWeight:900, color:T.primary,
              letterSpacing:"-0.5px", fontStyle:"italic" }}>Vitality</span>
          </div>
          <span style={{ fontSize:13, fontWeight:700, color:T.primary }}>
            {new Date().toLocaleDateString("he-IL",{day:"numeric",month:"short"})}
          </span>
        </div>
      </header>

      {/* Body */}
      <div style={{ flex:1, overflowY:"auto", paddingBottom:100, paddingTop:64 }}>
        {tab === "home"     && <HomeDashboard   profile={profile} goals={goals} totals={totals} entries={entries} onAdd={()=>setAddModal("method")} />}
        {tab === "diary"    && <DiaryView        entries={entries} goals={goals} totals={totals} onAdd={()=>setAddModal("method")} onRemove={removeEntry} />}
        {tab === "progress" && <ProgressView     profile={profile} diary={diary} goals={goals} bmr={bmr} tdee={tdee} />}
        {tab === "profile"  && <ProfileView      profile={profile} goals={goals} bmr={bmr} tdee={tdee} onUpdate={setProfile} />}
      </div>

      {/* Frosted bottom nav */}
      <nav style={{
        position:"fixed", bottom:0, left:"50%", transform:"translateX(-50%)",
        width:"100%", maxWidth:480, zIndex:100,
        background:"rgba(255,255,255,0.92)", backdropFilter:"blur(20px)",
        borderTop:`1px solid ${T.outlineVariant}22`,
        borderRadius:"28px 28px 0 0",
        boxShadow:"0 -4px 24px rgba(0,0,0,0.05)",
        display:"flex", padding:"12px 8px 24px",
      }}>
        {[
          { id:"home",     emoji:"📋", label:"יומן" },
          { id:"diary",    emoji:"📖", label:"מעקב" },
          { id:"progress", emoji:"📈", label:"התקדמות" },
          { id:"profile",  emoji:"👤", label:"פרופיל" },
        ].map(({ id, emoji, label }) => {
          const active = tab === id;
          return (
            <button key={id} onClick={() => setTab(id)} style={{
              flex:1, background:"none", border:"none", cursor:"pointer",
              display:"flex", flexDirection:"column", alignItems:"center", gap:4,
              padding:"6px 0", transition:"transform .15s",
              transform: active ? "scale(1.1)" : "scale(1)",
            }}>
              <div style={{
                width:40, height:40, borderRadius:14,
                background: active ? T.primaryContainer : "transparent",
                display:"flex", alignItems:"center", justifyContent:"center",
                fontSize:18, transition:"background .2s",
              }}>{emoji}</div>
              <span style={{
                fontSize:10, fontWeight:700,
                letterSpacing:"0.05em", textTransform:"uppercase",
                color: active ? T.primary : T.onSurfaceVariant,
              }}>{label}</span>
            </button>
          );
        })}
      </nav>

      {/* Add Food Modal */}
      {addModal && (
        <AddModal mode={addModal} onMode={setAddModal} onAdd={addEntry} onClose={() => setAddModal(null)} />
      )}
    </div>
  );
}

// ─── Onboarding ──────────────────────────────────────────────────────────────
function Onboarding({ onDone }) {
  const [step, setStep] = useState(0);
  const [data, setData] = useState({ ...DEFAULT_PROFILE });
  const set = (k,v) => setData(d=>({...d,[k]:v}));

  const steps = [
    { title:"שלום! 👋", subtitle:"בוא נכיר קצת", fields:[
      { k:"name",   label:"שם",   type:"text",   placeholder:"איך קוראים לך?" },
      { k:"age",    label:"גיל",  type:"number", min:10, max:99 },
      { k:"gender", label:"מין",  type:"select", opts:[{v:"male",l:"זכר"},{v:"female",l:"נקבה"}] },
    ]},
    { title:"גוף ומשקל", subtitle:"המדדים שלך", fields:[
      { k:"height",       label:'גובה (ס"מ)',        type:"number", min:100, max:250 },
      { k:"weight",       label:"משקל נוכחי (ק\"ג)", type:"number", min:30,  max:300 },
      { k:"targetWeight", label:"משקל יעד (ק\"ג)",   type:"number", min:30,  max:300 },
    ]},
    { title:"פעילות & מטרה", subtitle:"ספר לי עוד", fields:[
      { k:"activity",     label:"רמת פעילות", type:"select", opts:[
        {v:"sedentary",   l:"יושבני – כמעט ללא פעילות"},
        {v:"light",       l:"קל – 1-3 אימונים בשבוע"},
        {v:"moderate",    l:"מתון – 3-5 אימונים"},
        {v:"active",      l:"פעיל – 6-7 אימונים"},
        {v:"very_active", l:"מאוד פעיל – עבודה פיזית"},
      ]},
      { k:"goal", label:"המטרה שלי", type:"select", opts:[
        {v:"lose",  l:"ירידה במשקל 🔥"},
        {v:"gain",  l:"עלייה במסת שריר 💪"},
        {v:"maintain", l:"שמירה על המצב הקיים ⚖️"},
      ]},
      { k:"diet", label:"העדפות תזונה", type:"select", opts:[
        {v:"regular",   l:"רגיל"},
        {v:"vegetarian",l:"צמחוני"},
        {v:"vegan",     l:"טבעוני"},
        {v:"kosher",    l:"כשר"},
        {v:"glutenfree",l:"ללא גלוטן"},
      ]},
    ]},
  ];

  const s = steps[step];
  const isLast = step === steps.length - 1;

  const bmr   = calcBMR(data);
  const tdee  = calcTDEE(bmr, data.activity);
  const goals = calcGoals({ tdee, goal:data.goal });

  return (
    <div dir="rtl" style={{ minHeight:"100vh", background:T.surface,
      display:"flex", alignItems:"center", justifyContent:"center", padding:20,
      fontFamily:T.font }}>
      <div style={{ width:"100%", maxWidth:420 }}>

        {/* Logo */}
        <div style={{ textAlign:"center", marginBottom:32 }}>
          <div style={{ display:"inline-flex", alignItems:"center", gap:12 }}>
            <div style={{ width:44, height:44, borderRadius:14, background:T.primary,
              display:"flex", alignItems:"center", justifyContent:"center", fontSize:22 }}>🥗</div>
            <span style={{ fontSize:28, fontWeight:900, color:T.primary,
              letterSpacing:"-1px", fontStyle:"italic" }}>Vitality</span>
          </div>
        </div>

        {/* Step indicator */}
        <div style={{ display:"flex", gap:6, marginBottom:24, justifyContent:"center" }}>
          {steps.map((_,i) => (
            <div key={i} style={{ width:i===step?28:8, height:8, borderRadius:99,
              background:i<=step ? T.primary : "#d3d1c7",
              transition:"all .3s" }}/>
          ))}
        </div>

        <div style={{ background:T.surfaceBright, borderRadius:24, padding:28,
          boxShadow:"0 4px 32px rgba(0,0,0,0.06)" }}>
          <h2 style={{ margin:"0 0 4px", fontSize:24, fontWeight:900,
            color:T.onSurface, letterSpacing:"-0.5px", fontFamily:T.font }}>{s.title}</h2>
          <p style={{ margin:"0 0 24px", color:T.onSurfaceVariant, fontSize:14 }}>{s.subtitle}</p>

          {s.fields.map(f => (
            <div key={f.k} style={{ marginBottom:16 }}>
              <label style={{ display:"block", fontSize:13, color:T.onSurfaceVariant, marginBottom:6, fontWeight:600 }}>{f.label}</label>
              {f.type === "select" ? (
                <select value={data[f.k]} onChange={e=>set(f.k,e.target.value)}
                  style={{ width:"100%", padding:"12px 14px", borderRadius:12,
                    border:`1.5px solid ${T.outlineVariant}`, fontSize:14,
                    background:T.surfaceContainerLow, color:T.onSurface,
                    cursor:"pointer", fontFamily:T.font }}>
                  {f.opts.map(o => <option key={o.v} value={o.v}>{o.l}</option>)}
                </select>
              ) : (
                <input type={f.type} value={data[f.k]} min={f.min} max={f.max}
                  placeholder={f.placeholder}
                  onChange={e=>set(f.k, f.type==="number" ? +e.target.value : e.target.value)}
                  style={{ width:"100%", padding:"12px 14px", borderRadius:12,
                    border:`1.5px solid ${T.outlineVariant}`,
                    fontSize:14, background:T.surfaceContainerLow,
                    boxSizing:"border-box", fontFamily:T.font }}/>
              )}
            </div>
          ))}

          {/* Preview on last step */}
          {isLast && data.weight > 0 && (
            <div style={{ background:T.primaryContainer+"66", borderRadius:12, padding:16, marginTop:8, marginBottom:8 }}>
              <div style={{ fontSize:12, color:T.primary, fontWeight:700, marginBottom:8 }}>היעדים היומיים שלך:</div>
              <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:8 }}>
                {[
                  { l:"קלוריות", v:goals.cal, u:"קק\"ל" },
                  { l:"חלבון",   v:goals.p,   u:"g" },
                  { l:"פחמימות", v:goals.c,   u:"g" },
                  { l:"שומנים",  v:goals.f,   u:"g" },
                ].map(m => (
                  <div key={m.l} style={{ background:T.surfaceBright, borderRadius:8, padding:"8px 12px", textAlign:"center" }}>
                    <div style={{ fontSize:18, fontWeight:800, color:T.primaryDim }}>{m.v}<span style={{fontSize:11}}>{m.u}</span></div>
                    <div style={{ fontSize:11, color:T.onSurfaceVariant }}>{m.l}</div>
                  </div>
                ))}
              </div>
            </div>
          )}

          <div style={{ display:"flex", gap:10, marginTop:8 }}>
            {step > 0 && (
              <button onClick={()=>setStep(s=>s-1)}
                style={{ flex:"0 0 52px", height:52, border:`1.5px solid ${T.outlineVariant}`,
                  borderRadius:16, background:T.surfaceContainerLow, cursor:"pointer",
                  display:"flex", alignItems:"center", justifyContent:"center" }}>
                <BackIcon/>
              </button>
            )}
            <button onClick={() => isLast ? onDone(data) : setStep(s=>s+1)}
              style={{ flex:1, height:52, background:T.primary, color:"#fff", border:"none",
                borderRadius:16, fontWeight:800, fontSize:15, cursor:"pointer",
                fontFamily:T.font, letterSpacing:"-0.2px" }}>
              {isLast ? "בוא נתחיל! 🚀" : "המשך →"}
            </button>
          </div>
        </div>
      </div>
    </div>
  );
}

// ─── Nutrition Knowledge Cards ────────────────────────────────────────────────
const KNOWLEDGE_CARDS = [
  { type:"fact",  emoji:"🧬", title:"חלבון בונה שריר", text:"הגוף צריך כ-1.6–2.2 גרם חלבון לכל ק"ג משקל גוף כדי לבנות ולשמר שריר. ארוחה עם 30–40g חלבון מגרה את הסינתזה האנבולית בצורה מקסימלית." },
  { type:"tip",   emoji:"💧", title:"מים מגבירים חילוף חומרים", text:"שתיית 500מ"ל מים מגבירה את קצב חילוף החומרים ב-30% למשך כ-40 דקות. שתו כוס מים לפני כל ארוחה." },
  { type:"fact",  emoji:"🕐", title:"עיתוי חלבון חשוב פחות ממה שחשבתם", text:"מחקרים מראים שהסה"כ היומי של חלבון חשוב הרבה יותר מ"חלון ההזדמנויות" של 30 דקות אחרי אימון. חלקו חלבון לאורך כל היום." },
  { type:"myth",  emoji:"❌", title:"מיתוס: שומן מוביל להשמנה", text:"שומנים בריאים (אבוקדו, שקדים, שמן זית) חיוניים לייצור הורמונים ולספיגת ויטמינים. הבעיה היא עודף קלורי — לא שומן כשלעצמו." },
  { type:"tip",   emoji:"🌙", title:"ארוחת ערב לא מרעה?", text:"שעת האכילה פחות חשובה מהכמות הכוללת. אם יש לכם גירעון קלורי, אכילה בלילה לא תגרום להשמנה. הגוף לא "יודע" מה השעה." },
  { type:"fact",  emoji:"🔥", title:"חלבון שורף יותר קלוריות", text:"לעכל חלבון עולה לגוף 25–30% מהקלוריות שלו. לעומת זאת, שומן שורף רק 0–3% ופחמימות 5–10%. זה נקרא אפקט תרמי של מזון." },
  { type:"tip",   emoji:"🥗", title:"אכלו ירוקים ראשונים", text:"אכילת סיבים וירקות בתחילת הארוחה מאטה ספיגת סוכר, מפחיתה את הספייק הגליקמי ועוזרת להרגשת שובע מהירה יותר." },
  { type:"fact",  emoji:"😴", title:"שינה משפיעה על הרעב", text:"חוסר שינה מעלה את הורמון הגרלין (רעב) ב-15% ומוריד לפטין (שובע). 7–9 שעות שינה חיוניות לוויסות משקל." },
  { type:"myth",  emoji:"💊", title:"מיתוס: פחמימות הן האויב", text:"פחמימות מורכבות (קינואה, אורז מלא, בטטה) הן דלק מעולה לפעילות גופנית ולמוח. ה-WHO ממליץ שפחמימות יהוו 45–65% מהקלוריות." },
  { type:"tip",   emoji:"🍳", title:"בישול בבית = שליטה אמיתית", text:"מחקר של NEJM מצא שאנשים שמבשלים בבית 5+ פעמים בשבוע צורכים בממוצע 137 קלוריות פחות ביום. זה עד 14 ק"ג בשנה!" },
  { type:"fact",  emoji:"🫀", title:"סיבים תזונתיים — מהגיבורים הנסתרים", text:"רוב הישראלים אוכלים רק 15g סיבים ביום, בעוד ההמלצה היא 25–35g. סיבים משמינים חיידקי מעי, מורידים כולסטרול ומפחיתים סוכר בדם." },
  { type:"tip",   emoji:"📸", title:"צילום = מודעות", text:"מחקרים מראים שצילום מה שאוכלים מגדיל מודעות קלורית ב-20% ומפחית אכילת יתר. אפליקציית מעקב היא כלי מחקרי-מוכח." },
  { type:"fact",  emoji:"🏋️", title:"שריר שורף יותר", text:"ק"ג אחד של שריר שורף 13 קלוריות ביום במנוחה, לעומת 4–5 קלוריות לק"ג שומן. אימוני כוח מגבירים BMR לאורך זמן." },
  { type:"myth",  emoji:"🧃", title:"מיתוס: מיץ טבעי = בריאות", text:"כוס מיץ תפוזים (200מ"ל) מכילה 22g סוכר — כמעט כמו קולה. האכלו תפוז שלם: תקבלו סיבים, פחות סוכר, ויותר שובע." },
  { type:"tip",   emoji:"⏰", title:"הפסקה בין ביס לביס", text:"המוח צריך 15–20 דקות לרשום שובע. אכילה איטית מפחיתה צריכה קלורית ב-10–15% ללא מאמץ. הורידו את הסכו"ם בין ביסים." },
  { type:"fact",  emoji:"🫐", title:"נוגדי חמצון אמיתיים", text:"אוכמניות, ענבים אדומים ותה ירוק מכילים פוליפנולים שמגנים על תאים. אבל ויטמינים בכמוסות לא תמיד יעילים כמו אותם נוגדים מאוכל אמיתי." },
  { type:"tip",   emoji:"🧂", title:"מלח נסתר בכל מקום", text:"80% מהנתרן שאנחנו אוכלים מגיע ממזון מעובד — לא מהמלחייה. לחם, גבינות, רטבים ואפילו דגני בוקר הם מקורות עיקריים." },
  { type:"fact",  emoji:"🫙", title:"מותג "לייט" לא תמיד אומר פחות קלוריות", text:"מוצרים "דל שומן" לעיתים מכילים יותר סוכר כדי לפצות על הטעם. קראו תוויות — הסתכלו על כל 100g, לא על גודל מנה." },
];

function NutritionCard({ card }) {
  const colors = {
    fact: { bg:T.tertiaryContainer, border:"#bed1e7", label:"עובדה", labelBg:T.tertiary, text:"#2b3d4f" },
    tip:  { bg:T.primaryContainer+"66", border:T.primaryFixedDim, label:"טיפ", labelBg:T.primary, text:T.primaryDim },
    myth: { bg:T.secondaryContainer+"55", border:"#ffb375", label:"מיתוס", labelBg:T.secondary, text:T.secondaryDim },
  };
  const s = colors[card.type];
  return (
    <div style={{ background:s.bg, border:`1.5px solid ${s.border}`, borderRadius:16,
      padding:"14px 16px", minWidth:260, maxWidth:300, flexShrink:0, scrollSnapAlign:"start" }}>
      <div style={{ display:"flex", alignItems:"center", gap:8, marginBottom:8 }}>
        <span style={{ fontSize:22 }}>{card.emoji}</span>
        <span style={{ fontSize:10, fontWeight:800, background:s.labelBg, color:"#fff",
          borderRadius:99, padding:"2px 8px" }}>{card.label}</span>
      </div>
      <div style={{ fontWeight:800, fontSize:14, color:s.text, marginBottom:6 }}>{card.title}</div>
      <div style={{ fontSize:12.5, color:s.text, opacity:0.8, lineHeight:1.55 }}>{card.text}</div>
    </div>
  );
}

function KnowledgeStrip({ goal }) {
  const scrollRef = React.useRef(null);
  const [cardIdx, setCardIdx] = React.useState(() => Math.floor(Math.random() * KNOWLEDGE_CARDS.length));

  const visible = [];
  for (let i = 0; i < KNOWLEDGE_CARDS.length; i++) {
    visible.push(KNOWLEDGE_CARDS[(cardIdx + i) % KNOWLEDGE_CARDS.length]);
  }

  return (
    <div style={{ marginBottom:20 }}>
      <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:8 }}>
        <span style={{ fontSize:13, fontWeight:700, color:T.onSurfaceVariant }}>ידע & טיפים</span>
        <button onClick={() => setCardIdx(i => (i+1) % KNOWLEDGE_CARDS.length)}
          style={{ fontSize:12, color:T.primary, background:"none", border:"none",
            cursor:"pointer", fontWeight:700 }}>עוד ←</button>
      </div>
      <div ref={scrollRef} style={{ display:"flex", gap:12, overflowX:"auto", paddingBottom:8,
        scrollSnapType:"x mandatory", scrollbarWidth:"none", msOverflowStyle:"none",
        WebkitOverflowScrolling:"touch" }}>
        {visible.slice(0,5).map((c,i) => <NutritionCard key={i} card={c}/>)}
      </div>
    </div>
  );
}

// ─── Animated Macro Arc Visualization ────────────────────────────────────────
function MacroArcViz({ totals, goals }) {
  const size = 200;
  const cx = 100, cy = 108, r = 80, stroke = 14;
  const gap = 0.04; // radians gap between arcs
  const startAngle = Math.PI; // start from bottom-left (half circle)
  const totalArcAngle = Math.PI; // half circle
  
  // Three segments filling a semicircle
  const macros = [
    { key:"p", label:"חלבון",   val:totals.p, goal:goals.p, color:"#3b82f6",  trackColor:T.tertiaryContainer },
    { key:"c", label:"פחמימות", val:totals.c, goal:goals.c, color:T.secondary, trackColor:T.secondaryContainer+"55" },
    { key:"f", label:"שומנים",  val:totals.f, goal:goals.f, color:"#f43f5e", trackColor:"#fff1f2" },
  ];
  
  const segAngle = (totalArcAngle - gap * 2) / 3;
  
  function arc(cx, cy, r, startA, endA) {
    const x1 = cx + r * Math.cos(startA);
    const y1 = cy + r * Math.sin(startA);
    const x2 = cx + r * Math.cos(endA);
    const y2 = cy + r * Math.sin(endA);
    const large = Math.abs(endA - startA) > Math.PI ? 1 : 0;
    return `M ${x1} ${y1} A ${r} ${r} 0 ${large} 1 ${x2} ${y2}`;
  }

  return (
    <div style={{ position:"relative", width:size, margin:"0 auto -20px" }}>
      <svg width={size} height={size*0.65} viewBox={`0 0 ${size} ${size*0.65}`}>
        {macros.map((m, i) => {
          const segStart = startAngle + i * (segAngle + gap);
          const segEnd   = segStart + segAngle;
          const fill     = Math.min(1, m.val / (m.goal || 1));
          const fillEnd  = segStart + segAngle * fill;
          return (
            <g key={m.key}>
              {/* Track */}
              <path d={arc(cx, cy, r, segStart, segEnd)}
                fill="none" stroke={m.trackColor} strokeWidth={stroke} strokeLinecap="round"/>
              {/* Fill */}
              {fill > 0.01 && (
                <path d={arc(cx, cy, r, segStart, fillEnd)}
                  fill="none" stroke={m.color} strokeWidth={stroke} strokeLinecap="round"
                  style={{ transition:"stroke-dashoffset .8s ease" }}/>
              )}
              {/* End dot */}
              {fill > 0.05 && (
                <circle
                  cx={cx + r * Math.cos(fillEnd)}
                  cy={cy + r * Math.sin(fillEnd)}
                  r={stroke/2 - 1} fill={m.color}/>
              )}
            </g>
          );
        })}
        {/* Center label */}
        <text x={cx} y={cy - 22} textAnchor="middle" fontSize="28" fontWeight="900" fill=T.onSurface>
          {fmt(totals.cal)}
        </text>
        <text x={cx} y={cy - 6} textAnchor="middle" fontSize="11" fill="#aaa">קק"ל</text>
      </svg>
      {/* Legend below arc */}
      <div style={{ display:"flex", justifyContent:"space-around", marginTop:-4 }}>
        {macros.map(m => (
          <div key={m.key} style={{ textAlign:"center" }}>
            <div style={{ fontSize:13, fontWeight:800, color:m.color }}>{fmt(m.val)}<span style={{fontSize:10}}>g</span></div>
            <div style={{ fontSize:10, color:T.outlineVariant }}>{m.label}</div>
            <div style={{ fontSize:10, color:"#ccc" }}>/{m.goal}g</div>
          </div>
        ))}
      </div>
    </div>
  );
}

// ─── Home Dashboard ───────────────────────────────────────────────────────────
function HomeDashboard({ profile, goals, totals, entries, onAdd }) {
  const calLeft  = Math.max(0, goals.cal - totals.cal);
  const over     = totals.cal > goals.cal;
  const goalLabel = { lose:"ירידה במשקל 🔥", gain:"עלייה במסה 💪", maintain:"שמירה ⚖️" }[profile.goal];
  const meals    = groupByMeal(entries);
  const calPct   = pct(totals.cal, goals.cal);

  // Time-based greeting
  const hour = new Date().getHours();
  const greeting = hour < 12 ? "בוקר טוב" : hour < 17 ? "שלום" : "ערב טוב";

  return (
    <div style={{ padding:"0 0 0" }}>
      {/* Hero section – Vitality style */}
      <div style={{ padding:"28px 24px 0" }}>
        <div style={{ marginBottom:20 }}>
          <div style={{ display:"flex", alignItems:"baseline", justifyContent:"space-between", marginBottom:6 }}>
            <h2 style={{ margin:0, fontSize:26, fontWeight:900, letterSpacing:"-0.5px",
              color:T.onSurface, fontFamily:T.font }}>
              יומן היום
            </h2>
            <span style={{ fontSize:13, fontWeight:700, color:T.primary }}>
              {new Date().toLocaleDateString("he-IL",{weekday:"long",day:"numeric",month:"long"})}
            </span>
          </div>
          <p style={{ margin:0, fontSize:14, color:T.onSurfaceVariant, fontWeight:500, lineHeight:1.5 }}>
            {greeting}, <strong style={{color:T.onSurface}}>{profile.name || "משתמש"}</strong>{" — "}
            {over
              ? <span>חרגת ב-<span style={{color:T.error, fontWeight:700}}>{fmt(totals.cal - goals.cal)} קק"ל</span> מהיעד היומי</span>
              : <span>צרכת <span style={{color:T.primary, fontWeight:700}}>{fmt(totals.cal)} קק"ל</span>. נותרו עוד {fmt(calLeft)} קק"ל</span>
            }
          </p>
        </div>

      <div style={{ padding:"0 0px", position:"relative", zIndex:10 }}>
        {/* ── Bento grid: Arc + 3 macro tiles ─────────────────────── */}
        <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr", gap:12, marginBottom:12 }}>
          {/* Arc tile spans all 3 cols */}
          <div style={{ gridColumn:"1/-1", background:T.surfaceBright, borderRadius:16,
            padding:"20px 20px 16px", boxShadow:"0 2px 12px rgba(0,0,0,0.04)" }}>
            <MacroArcViz totals={totals} goals={goals} />
            {/* Calorie progress bar */}
            <div style={{ marginTop:14 }}>
              <div style={{ display:"flex", justifyContent:"space-between", marginBottom:6 }}>
                <span style={{ fontSize:12, color:T.onSurfaceVariant, fontWeight:500 }}>
                  {over ? `חריגה של ${fmt(totals.cal - goals.cal)} קק"ל` : `נותרו ${fmt(calLeft)} קק"ל`}
                </span>
                <span style={{ fontSize:12, fontWeight:800,
                  color: over ? T.error : calPct >= 90 ? T.secondaryDim : T.primary }}>
                  {calPct}%
                </span>
              </div>
              <div style={{ height:6, background:T.surfaceContainerHighest, borderRadius:99, overflow:"hidden" }}>
                <div style={{
                  height:"100%", width:`${Math.min(100,calPct)}%`, borderRadius:99,
                  background: over ? T.error : calPct > 85 ? T.secondary : T.primary,
                  transition:"width .8s cubic-bezier(.4,0,.2,1)"
                }}/>
              </div>
            </div>
          </div>

          {/* 3 macro bento tiles */}
          {[
            { label:"PROTEIN", heLabel:"חלבון",   val:totals.p, goal:goals.p, barColor:T.primary },
            { label:"CARBS",   heLabel:"פחמימות", val:totals.c, goal:goals.c, barColor:T.secondaryDim },
            { label:"FATS",    heLabel:"שומנים",  val:totals.f, goal:goals.f, barColor:T.tertiary },
          ].map(m => {
            const p2 = pct(m.val, m.goal);
            return (
              <div key={m.label} style={{ background:T.surfaceBright, borderRadius:16,
                padding:"14px 14px 12px", boxShadow:"0 2px 8px rgba(0,0,0,0.03)",
                display:"flex", flexDirection:"column", justifyContent:"space-between", minHeight:110 }}>
                <span style={{ fontSize:9, fontWeight:700, letterSpacing:"0.12em",
                  textTransform:"uppercase", color:T.onSurfaceVariant }}>{m.label}</span>
                <div style={{ display:"flex", alignItems:"flex-end", justifyContent:"space-between",
                  marginTop:"auto", paddingTop:8 }}>
                  <span style={{ fontSize:22, fontWeight:900, color:T.onSurface,
                    letterSpacing:"-0.5px" }}>{fmt(m.val)}<span style={{fontSize:12,fontWeight:500}}>g</span></span>
                  <div style={{ width:36, height:4, background:T.surfaceContainerHighest, borderRadius:99, overflow:"hidden" }}>
                    <div style={{ height:"100%", width:`${Math.min(100,p2)}%`,
                      background:m.barColor, borderRadius:99, transition:"width .6s" }}/>
                  </div>
                </div>
                <div style={{ fontSize:10, color:T.onSurfaceVariant, marginTop:4 }}>/{m.goal}g</div>
              </div>
            );
          })}
        </div>

        {/* FAB – floating add button */}
        <div style={{ position:"relative", height:0 }}>
          <button onClick={onAdd} style={{
            position:"fixed",
            bottom:96, left:"50%",
            transform:"translateX(calc(-50% - 176px))",
            width:56, height:56,
            background:T.primary, color:T.onPrimary,
            border:"none", borderRadius:"50%",
            fontWeight:900, fontSize:28,
            cursor:"pointer", zIndex:90,
            display:"flex", alignItems:"center", justifyContent:"center",
            boxShadow:"0 4px 24px rgba(0,106,53,0.35)",
            transition:"transform .2s, box-shadow .2s",
          }}>+</button>
        </div>

        {/* Meals today */}
        <div style={{ marginTop:20 }}>
          {entries.length > 0 ? (
            <>
              <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:10 }}>
                <h3 style={{ margin:0, fontSize:15, fontWeight:800, color:T.onSurface }}>ארוחות היום</h3>
                <span style={{ fontSize:12, color:T.outlineVariant }}>{entries.length} פריטים</span>
              </div>
              {Object.entries(meals).map(([meal, items]) => items.length > 0 && (
                <MealSummaryCard key={meal} meal={meal} items={items} />
              ))}
            </>
          ) : (
            <EmptyState icon="🍽️" title="לא אכלת עדיין?" subtitle="הוסף את הארוחה הראשונה שלך היום" />
          )}
        </div>

        {/* Knowledge strip */}
        <div style={{ marginTop:24, paddingBottom:8 }}>
          <KnowledgeStrip goal={profile.goal} />
        </div>
      </div>
      </div>
    </div>
  );
}

function MealSummaryCard({ meal, items }) {
  const cal  = items.reduce((a,e)=>a+e.cal,0);
  const p    = items.reduce((a,e)=>a+e.p,  0);
  const c    = items.reduce((a,e)=>a+e.c,  0);
  const f    = items.reduce((a,e)=>a+e.f,  0);
  const accentColors = {
    "ארוחת בוקר":   T.primary,
    "ארוחת צהריים": T.secondaryContainer,
    "ארוחת ערב":    T.tertiaryContainer,
    "ביניים/נשנוש": T.surfaceContainerHighest,
  };
  const accent = accentColors[meal] || T.surfaceContainerHighest;
  return (
    <article style={{ marginBottom:24 }}>
      {/* Meal header */}
      <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:10 }}>
        <h3 style={{ margin:0, fontSize:16, fontWeight:800, color:T.onSurface,
          display:"flex", alignItems:"center", gap:10, fontFamily:T.font }}>
          <span style={{ width:4, height:28, background:accent, borderRadius:99, display:"inline-block" }}/>
          {meal}
        </h3>
        <span style={{ fontSize:13, fontWeight:700, color:T.onSurfaceVariant }}>{fmt(cal)} קק"ל</span>
      </div>
      {/* Items card */}
      <div style={{ background:T.surfaceBright, borderRadius:16,
        padding:"20px 20px 16px",
        boxShadow:"0 2px 12px rgba(0,0,0,0.03)", border:`1px solid ${T.surfaceContainerHigh}` }}>
        {items.map((e, idx) => (
          <div key={e.id || idx}>
            <div style={{ display:"flex", alignItems:"flex-start", justifyContent:"space-between",
              paddingBottom:12 }}>
              <div>
                <div style={{ fontSize:16, fontWeight:700, color:T.onSurface,
                  fontFamily:T.font, marginBottom:2 }}>{e.name}</div>
                {e.time && <div style={{ fontSize:13, color:T.onSurfaceVariant }}>{e.time}</div>}
              </div>
            </div>
            <div style={{ display:"flex", gap:16,
              borderTop:`1px solid ${T.outlineVariant}22`, paddingTop:12,
              marginBottom: idx < items.length-1 ? 12 : 0 }}>
              {[["P","חל",fmt(e.p)+"g"],[" C","פח",fmt(e.c)+"g"],["F","שומ",fmt(e.f)+"g"]].map(([k,l,v])=>(
                <div key={k} style={{ display:"flex", flexDirection:"column" }}>
                  <span style={{ fontSize:9, fontWeight:700, letterSpacing:"0.1em",
                    textTransform:"uppercase", color:T.onSurfaceVariant }}>{l}</span>
                  <span style={{ fontSize:13, fontWeight:800, color:T.onSurface }}>{v}</span>
                </div>
              ))}
              <div style={{ marginRight:"auto" }}/>
              <div style={{ display:"flex", flexDirection:"column", alignItems:"flex-end" }}>
                <span style={{ fontSize:9, fontWeight:700, letterSpacing:"0.1em",
                  textTransform:"uppercase", color:T.onSurfaceVariant }}>קק"ל</span>
                <span style={{ fontSize:13, fontWeight:800, color:T.onSurface }}>{fmt(e.cal)}</span>
              </div>
            </div>
          </div>
        ))}
      </div>
    </article>
  );
}

// ─── Diary View ───────────────────────────────────────────────────────────────
function DiaryView({ entries, goals, totals, onAdd, onRemove }) {
  const meals = groupByMeal(entries);

  return (
    <div style={{ background:T.surface, minHeight:"100vh" }}>
      {/* Page header */}
      <div style={{ padding:"28px 24px 0" }}>
        <div style={{ display:"flex", alignItems:"baseline", justifyContent:"space-between", marginBottom:6 }}>
          <h2 style={{ margin:0, fontSize:26, fontWeight:900, letterSpacing:"-0.5px",
            color:T.onSurface, fontFamily:T.font }}>יומן אוכל</h2>
        </div>
        <p style={{ margin:"0 0 20px", fontSize:14, color:T.onSurfaceVariant, fontWeight:500 }}>
          צרכת <strong style={{color:T.primary}}>{fmt(totals.cal)} קק"ל</strong> מתוך{" "}
          <strong style={{color:T.onSurface}}>{goals.cal}</strong> קק"ל
        </p>

        {/* Bento summary strip */}
        <div style={{ display:"grid", gridTemplateColumns:"repeat(3,1fr)", gap:10, marginBottom:24 }}>
          {[
            { label:"PROTEIN", val:fmt(totals.p)+"g", barW: pct(totals.p,goals.p), color:T.primary },
            { label:"CARBS",   val:fmt(totals.c)+"g", barW: pct(totals.c,goals.c), color:T.secondaryDim },
            { label:"FATS",    val:fmt(totals.f)+"g", barW: pct(totals.f,goals.f), color:T.tertiary },
          ].map(m => (
            <div key={m.label} style={{ background:T.surfaceBright, borderRadius:14,
              padding:"14px 14px 10px", boxShadow:"0 1px 6px rgba(0,0,0,0.04)" }}>
              <span style={{ fontSize:9, fontWeight:700, letterSpacing:"0.12em",
                textTransform:"uppercase", color:T.onSurfaceVariant, display:"block", marginBottom:8 }}>
                {m.label}
              </span>
              <div style={{ display:"flex", alignItems:"flex-end", justifyContent:"space-between" }}>
                <span style={{ fontSize:20, fontWeight:900, color:T.onSurface }}>{m.val}</span>
                <div style={{ width:36, height:4, background:T.surfaceContainerHighest, borderRadius:99 }}>
                  <div style={{ height:"100%", width:`${Math.min(100,m.barW)}%`,
                    background:m.color, borderRadius:99 }}/>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
      <div style={{ padding:"0 24px" }}>

      {/* Meal groups – Vitality article style */}
      <div style={{ marginTop:4 }}>
        {Object.entries(meals).map(([meal, items]) => {
          const mealCal = items.reduce((a,e)=>a+e.cal,0);
          const accentColors = {
            "ארוחת בוקר":T.primary, "ארוחת צהריים":T.secondaryContainer,
            "ארוחת ערב":T.tertiaryContainer, "ביניים/נשנוש":T.surfaceContainerHighest
          };
          const accent = accentColors[meal] || T.surfaceContainerHighest;
          return (
            <article key={meal} style={{ marginBottom:28 }}>
              {/* Meal header */}
              <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:12 }}>
                <h3 style={{ margin:0, fontSize:16, fontWeight:800, color:T.onSurface,
                  display:"flex", alignItems:"center", gap:10, fontFamily:T.font }}>
                  <span style={{ width:4, height:28, background:accent,
                    borderRadius:99, display:"inline-block" }}/>
                  {meal}
                </h3>
                <span style={{ fontSize:13, fontWeight:700, color:T.onSurfaceVariant }}>
                  {items.length > 0 ? `${fmt(mealCal)} קק"ל` : ""}
                </span>
              </div>
              {items.length === 0 ? (
                <button onClick={onAdd} style={{
                  width:"100%", height:100,
                  border:`2px dashed ${T.outlineVariant}55`, borderRadius:16,
                  background:"transparent", cursor:"pointer", color:T.onSurfaceVariant,
                  display:"flex", flexDirection:"column", alignItems:"center",
                  justifyContent:"center", gap:6, fontFamily:T.font
                }}>
                  <span style={{ fontSize:22 }}>+</span>
                  <span style={{ fontSize:11, fontWeight:700, letterSpacing:"0.1em",
                    textTransform:"uppercase" }}>הוסף {meal}</span>
                </button>
              ) : (
                <div style={{ background:T.surfaceBright, borderRadius:16, padding:"4px 20px",
                  boxShadow:"0 2px 12px rgba(0,0,0,0.04)",
                  border:`1px solid ${T.surfaceContainerHigh}` }}>
                  {items.map((e,idx) => (
                    <DiaryEntry key={e.id} entry={e} onRemove={onRemove} />
                  ))}
                </div>
              )}
            </article>
          );
        })}
      </div>
      </div>
    </div>
  );
}

function DiaryEntry({ entry, onRemove }) {
  return (
    <div style={{ display:"flex", alignItems:"flex-start", justifyContent:"space-between",
      padding:"12px 0", borderBottom:`1px solid ${T.outlineVariant}18` }}>
      <div style={{ flex:1 }}>
        <div style={{ fontSize:15, fontWeight:700, color:T.onSurface,
          fontFamily:T.font, marginBottom:4 }}>{entry.name}</div>
        <div style={{ display:"flex", gap:14 }}>
          {[["P",fmt(entry.p)+"g"],["C",fmt(entry.c)+"g"],["F",fmt(entry.f)+"g"]].map(([k,v])=>(
            <div key={k} style={{ display:"flex", flexDirection:"column" }}>
              <span style={{ fontSize:9, fontWeight:700, letterSpacing:"0.1em",
                color:T.onSurfaceVariant, textTransform:"uppercase" }}>{k}</span>
              <span style={{ fontSize:12, fontWeight:800, color:T.onSurface }}>{v}</span>
            </div>
          ))}
        </div>
      </div>
      <div style={{ display:"flex", alignItems:"center", gap:12 }}>
        <span style={{ fontSize:15, fontWeight:800, color:T.primary }}>{fmt(entry.cal)}</span>
        <button onClick={()=>onRemove(entry.id)} style={{ background:"none", border:"none",
          cursor:"pointer", color:T.outlineVariant, padding:4, fontSize:16 }}>✕</button>
      </div>
    </div>
  );
}

// ─── Progress View ────────────────────────────────────────────────────────────
function ProgressView({ profile, diary, goals, bmr, tdee }) {
  const days = Object.keys(diary).sort().slice(-14);
  const dailyCals = days.map(d => ({
    date: d,
    cal: (diary[d]||[]).reduce((a,e)=>a+e.cal,0),
    p:   (diary[d]||[]).reduce((a,e)=>a+e.p,  0),
    c:   (diary[d]||[]).reduce((a,e)=>a+e.c,  0),
    f:   (diary[d]||[]).reduce((a,e)=>a+e.f,  0),
  }));
  const tracked = dailyCals.filter(d=>d.cal>0);
  const avgCal  = tracked.length > 0
    ? Math.round(tracked.reduce((a,d)=>a+d.cal,0)/tracked.length) : 0;
  const avgP    = tracked.length > 0
    ? Math.round(tracked.reduce((a,d)=>a+d.p,0)/tracked.length) : 0;
  const daysOnTarget = dailyCals.filter(d => d.cal >= goals.cal*0.9 && d.cal <= goals.cal*1.1).length;
  const streak = (() => {
    let s = 0;
    for (let i = dailyCals.length-1; i>=0; i--) {
      if (dailyCals[i].cal > 0) s++; else break;
    }
    return s;
  })();
  const weightDiff  = Math.abs(profile.weight - profile.targetWeight);
  const weightProg  = profile.goal === "lose"
    ? Math.min(100, Math.max(0, Math.round((1 - weightDiff / Math.max(1, Math.abs(profile.weight - profile.targetWeight) + 3)) * 100)))
    : 40;

  return (
    <div style={{ background:T.surface, minHeight:"100vh" }}>
      {/* Header */}
      <div style={{ background:"linear-gradient(135deg,#185FA5,#378ADD)",
        padding:"24px 20px 60px" }}>
        <h2 style={{ margin:0, fontSize:22, fontWeight:900, color:"#fff" }}>ההתקדמות שלי</h2>
        <p style={{ margin:"4px 0 0", fontSize:13, color:"rgba(255,255,255,0.7)" }}>
          {tracked.length} ימים מתועדים
        </p>
      </div>

      <div style={{ padding:"0 16px", marginTop:-40 }}>
        {/* Streak + stats */}
        <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr 1fr", gap:8, marginBottom:16 }}>
          {[
            { l:"רצף ימים", v:streak,          u:"🔥", c:"#f43f5e" },
            { l:"ביעד",     v:daysOnTarget,     u:"✅", c:T.primary },
            { l:"ממוצע",    v:avgCal||"—",      u:"קק"ל", c:T.secondary },
            { l:"חלבון ~",  v:avgP||"—",        u:"g",     c:"#3b82f6" },
          ].map(s => (
            <div key={s.l} style={{ background:T.surfaceBright, borderRadius:14, padding:"10px 8px",
              boxShadow:"0 2px 12px #0001", textAlign:"center", border:`1px solid ${T.surfaceContainerHigh}` }}>
              <div style={{ fontSize:20 }}>{s.u}</div>
              <div style={{ fontSize:18, fontWeight:900, color:s.c, lineHeight:1.1 }}>{s.v}</div>
              <div style={{ fontSize:10, color:T.outlineVariant, marginTop:2 }}>{s.l}</div>
            </div>
          ))}
        </div>

        {/* Weight journey card */}
        <div style={{ background:T.surfaceBright, borderRadius:18, padding:"18px 20px", marginBottom:14,
          boxShadow:"0 2px 12px #0001", border:`1px solid ${T.surfaceContainerHigh}` }}>
          <div style={{ fontSize:13, fontWeight:800, color:T.onSurface, marginBottom:14 }}>מסע המשקל</div>
          <div style={{ display:"flex", alignItems:"center", gap:0, marginBottom:16 }}>
            {/* Current */}
            <div style={{ textAlign:"center", minWidth:60 }}>
              <div style={{ fontSize:26, fontWeight:900, color:T.onSurface }}>{profile.weight}</div>
              <div style={{ fontSize:10, color:T.outlineVariant }}>עכשיו</div>
            </div>
            {/* Progress track */}
            <div style={{ flex:1, padding:"0 12px" }}>
              <div style={{ position:"relative", height:10, background:T.surfaceContainerHighest, borderRadius:99 }}>
                <div style={{ position:"absolute", right:0, top:0, height:"100%",
                  width:`${100 - weightProg}%`, background:`linear-gradient(90deg,${T.primaryFixed},${T.primary})`,
                  borderRadius:99, transition:"width 1s ease" }}/>
                <div style={{ position:"absolute", top:"50%", right:`${100-weightProg}%`,
                  transform:"translate(50%,-50%)",
                  width:18, height:18, borderRadius:"50%", background:T.primary,
                  border:"3px solid #fff", boxShadow:"0 0 0 2px "+T.primaryFixed }}/>
              </div>
              <div style={{ textAlign:"center", fontSize:11, color:T.onSurfaceVariant, marginTop:6 }}>
                עוד {weightDiff} ק"ג {profile.goal==="lose"?"להורדה":profile.goal==="gain"?"להעלאה":"לאיזון"}
              </div>
            </div>
            {/* Target */}
            <div style={{ textAlign:"center", minWidth:60 }}>
              <div style={{ fontSize:26, fontWeight:900, color:T.primary }}>{profile.targetWeight}</div>
              <div style={{ fontSize:10, color:T.outlineVariant }}>יעד</div>
            </div>
          </div>
          {/* BMR / TDEE mini row */}
          <div style={{ display:"flex", gap:8 }}>
            {[
              { l:"BMR", v:fmt(bmr), desc:"מנוחה", color:T.onSurfaceVariant },
              { l:"TDEE", v:tdee, desc:"עם פעילות", color:T.secondary },
              { l:"יעד", v:goals.cal, desc:"קלורי יומי", color:T.primary },
            ].map(r => (
              <div key={r.l} style={{ flex:1, background:T.surface, borderRadius:10,
                padding:"8px 10px", textAlign:"center", border:`1px solid ${T.surfaceContainerHigh}` }}>
                <div style={{ fontSize:15, fontWeight:900, color:r.color }}>{r.v}</div>
                <div style={{ fontSize:9, color:T.outlineVariant }}>{r.l} – {r.desc}</div>
              </div>
            ))}
          </div>
        </div>

        {/* Calorie chart */}
        <div style={{ background:T.surfaceBright, borderRadius:18, padding:"16px 16px 10px",
          marginBottom:14, boxShadow:"0 2px 12px #0001", border:`1px solid ${T.surfaceContainerHigh}` }}>
          <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:14 }}>
            <div style={{ fontSize:14, fontWeight:800, color:T.onSurface }}>קלוריות יומיות</div>
            <div style={{ display:"flex", gap:8, fontSize:11 }}>
              <span><span style={{ color:T.primary }}>■</span> ביעד</span>
              <span><span style={{ color:"#f43f5e" }}>■</span> מעל</span>
              <span><span style={{ color:T.primaryFixed }}>■</span> חסר</span>
            </div>
          </div>
          {dailyCals.length > 0 ? (
            <SimpleBarChart data={dailyCals} goal={goals.cal} />
          ) : (
            <EmptyState icon="📊" title="אין עדיין נתונים" subtitle="תתחיל לתעד כדי לראות גרף" />
          )}
        </div>

        {/* Macro weekly averages */}
        {tracked.length > 0 && (
          <div style={{ background:T.surfaceBright, borderRadius:18, padding:"16px 18px", marginBottom:14,
            boxShadow:"0 2px 12px #0001", border:`1px solid ${T.surfaceContainerHigh}` }}>
            <div style={{ fontSize:14, fontWeight:800, color:T.onSurface, marginBottom:12 }}>ממוצע מאקרו יומי</div>
            {[
              { l:"חלבון",   avg:Math.round(tracked.reduce((a,d)=>a+d.p,0)/tracked.length), goal:goals.p, color:"#3b82f6", bg:T.tertiaryContainer },
              { l:"פחמימות", avg:Math.round(tracked.reduce((a,d)=>a+d.c,0)/tracked.length), goal:goals.c, color:T.secondary,bg:T.secondaryContainer+"55" },
              { l:"שומנים",  avg:Math.round(tracked.reduce((a,d)=>a+d.f,0)/tracked.length), goal:goals.f, color:"#f43f5e",bg:"#fff1f2" },
            ].map(m => {
              const p2 = pct(m.avg, m.goal);
              return (
                <div key={m.l} style={{ marginBottom:10 }}>
                  <div style={{ display:"flex", justifyContent:"space-between", marginBottom:4 }}>
                    <span style={{ fontSize:13, fontWeight:700, color:m.color }}>{m.l}</span>
                    <span style={{ fontSize:12, color:T.onSurfaceVariant }}>{m.avg}g / {m.goal}g ({p2}%)</span>
                  </div>
                  <div style={{ height:8, background:m.bg, borderRadius:99 }}>
                    <div style={{ height:"100%", width:`${Math.min(100,p2)}%`,
                      background:m.color, borderRadius:99, transition:"width .8s" }}/>
                  </div>
                </div>
              );
            })}
          </div>
        )}

        {/* Insights */}
        <div style={{ background:T.primaryContainer+"66", borderRadius:18, padding:"16px 18px", marginBottom:20,
          border:`1px solid ${T.primaryContainer}` }}>
          <div style={{ fontSize:14, fontWeight:800, color:T.primaryDim, marginBottom:10 }}>💡 תובנות אישיות</div>
          <InsightLine icon="🔥" text={`TDEE שלך הוא ${tdee} קק"ל — כולל ${profile.activity === "sedentary" ? "כמעט ללא" : "פעילות"} גופנית`} />
          <InsightLine icon="📉" text={`יעד גירעון/עודף: ${Math.abs(goals.cal - tdee)} קק"ל ${goals.cal < tdee ? "גירעון" : "עודף"} מדי יום`} />
          <InsightLine icon="🥩" text={`יעד חלבון: ${goals.p}g = ${Math.round(goals.p/profile.weight*10)/10}g/ק"ג משקל גוף`} />
          {streak >= 3 && <InsightLine icon="🔥" text={`רצף של ${streak} ימים! המשיכו כך!`} />}
          {avgCal > 0 && avgCal < goals.cal * 0.8 && <InsightLine icon="⚠️" text={`הממוצע הקלורי שלכם נמוך מדי — וודאו שאתם אוכלים מספיק`} />}
        </div>
      </div>
    </div>
  );
}

function InsightLine({ icon, text }) {
  return (
    <div style={{ display:"flex", gap:10, alignItems:"flex-start", marginBottom:10,
      padding:"8px 0", borderBottom:`1px solid ${T.outlineVariant}18` }}>
      <span style={{ fontSize:16, flexShrink:0 }}>{icon}</span>
      <p style={{ margin:0, fontSize:13, color:T.onSurfaceVariant, lineHeight:1.6,
        fontWeight:500 }}>{text}</p>
    </div>
  );
}

function SimpleBarChart({ data, goal }) {
  const maxCal = Math.max(...data.map(d=>d.cal), goal, 1);
  const [hovered, setHovered] = React.useState(null);
  const chartH = 140;
  return (
    <div style={{ position:"relative" }}>
      {/* Tooltip */}
      {hovered !== null && (
        <div style={{ position:"absolute", top:-32, left:"50%", transform:"translateX(-50%)",
          background:T.onSurface, color:"#fff", borderRadius:8, padding:"4px 10px",
          fontSize:12, fontWeight:700, whiteSpace:"nowrap", zIndex:10, pointerEvents:"none" }}>
          {data[hovered]?.date?.slice(5)} — {fmt(data[hovered]?.cal)} קק"ל
        </div>
      )}
      <div style={{ display:"flex", alignItems:"flex-end", gap:3, height:chartH, position:"relative" }}>
        {/* Goal dashed line */}
        <div style={{ position:"absolute", bottom:`${(goal/maxCal)*chartH}px`, left:0, right:0,
          borderTop:`1.5px dashed ${T.primaryFixed}`, zIndex:2, pointerEvents:"none" }}>
          <span style={{ position:"absolute", right:0, top:-16, fontSize:10,
            color:T.primary, fontWeight:700, background:T.surfaceBright, padding:"0 4px" }}>יעד</span>
        </div>
        {data.map((d,i) => {
          const barH   = Math.max(d.cal > 0 ? 4 : 0, Math.round((d.cal / maxCal) * (chartH-10)));
          const over   = d.cal > goal * 1.05;
          const onGoal = !over && d.cal >= goal * 0.9;
          const bg     = over ? "#f43f5e" : onGoal ? T.primary : T.primaryFixed;
          const isHov  = hovered === i;
          return (
            <div key={i} style={{ flex:1, display:"flex", flexDirection:"column",
              alignItems:"center", gap:3, cursor:"pointer" }}
              onMouseEnter={()=>setHovered(i)} onMouseLeave={()=>setHovered(null)}
              onClick={()=>setHovered(hovered===i?null:i)}>
              <div style={{ width:"100%", height:barH,
                background: isHov ? (over ? "#e11d48" : T.primaryDim) : bg,
                borderRadius:"6px 6px 0 0",
                transition:"height .6s cubic-bezier(.4,0,.2,1), background .2s",
                boxShadow: isHov ? `0 0 0 2px ${over?"#f43f5e":T.primary}` : "none" }}/>
              <span style={{ fontSize:8, color: isHov ? "#555" : "#ccc",
                transform:"rotate(-40deg)", transformOrigin:"top right",
                whiteSpace:"nowrap", display:"block", height:14 }}>
                {d.date?.slice(5)}
              </span>
            </div>
          );
        })}
      </div>
    </div>
  );
}

// ─── Profile View ─────────────────────────────────────────────────────────────
function ProfileView({ profile, goals, bmr, tdee, onUpdate }) {
  const [editing, setEditing] = useState(false);
  const [form, setForm] = useState(profile);
  const set = (k,v) => setForm(f=>({...f,[k]:v}));

  function save() {
    onUpdate({ ...form, onboarded:true });
    setEditing(false);
  }

  const goalLabel = { lose:"ירידה במשקל 🔥", gain:"עלייה במסה 💪", maintain:"שמירה ⚖️" }[profile.goal];
  const actLabel  = { sedentary:"יושבני", light:"קל", moderate:"מתון", active:"פעיל", very_active:"מאוד פעיל" }[profile.activity];

  return (
    <div style={{ background:T.surface, minHeight:"100vh" }}>
    <div style={{ padding:"28px 24px 0" }}>
      <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:20 }}>
        <h2 style={{ margin:0, fontSize:26, fontWeight:900, letterSpacing:"-0.5px",
          color:T.onSurface, fontFamily:T.font }}>הפרופיל שלי</h2>
        <button onClick={()=>setEditing(!editing)}
          style={{ background: editing ? T.surfaceContainerLow : T.primary,
            color: editing ? T.onSurface : "#fff",
            border: editing ? `1.5px solid ${T.outlineVariant}` : "none",
            borderRadius:12, padding:"10px 18px", fontWeight:800, fontSize:13,
            cursor:"pointer", fontFamily:T.font }}>
          {editing ? "ביטול" : "ערוך פרופיל"}
        </button>
      </div>

      {/* Avatar – Vitality card */}
      <div style={{ display:"flex", alignItems:"center", gap:16, marginBottom:24,
        background:T.surfaceBright, borderRadius:20, padding:"20px",
        boxShadow:"0 2px 12px rgba(0,0,0,0.04)" }}>
        <div style={{ width:64, height:64, borderRadius:"50%", background:T.primaryContainer,
          display:"flex", alignItems:"center", justifyContent:"center",
          fontSize:28, flexShrink:0 }}>
          {profile.gender === "male" ? "👨" : "👩"}
        </div>
        <div>
          <div style={{ fontWeight:900, fontSize:20, color:T.onSurface,
            fontFamily:T.font, letterSpacing:"-0.3px" }}>{profile.name || "משתמש"}</div>
          <div style={{ fontSize:13, color:T.primary, fontWeight:700, marginTop:2 }}>{goalLabel}</div>
          <div style={{ fontSize:12, color:T.onSurfaceVariant, marginTop:1 }}>
            {profile.gender === "male" ? "גבר" : "אישה"} · {profile.age} שנים · {profile.height} ס"מ
          </div>
        </div>
      </div>

      {editing ? (
        <div style={{ background:T.surfaceBright, borderRadius:16, padding:20, border:`1px solid ${T.surfaceContainerHigh}` }}>
          {[
            { k:"weight",       l:"משקל (ק\"ג)",      t:"number" },
            { k:"targetWeight", l:"משקל יעד (ק\"ג)",  t:"number" },
            { k:"height",       l:'גובה (ס"מ)',        t:"number" },
          ].map(f => (
            <div key={f.k} style={{ marginBottom:12 }}>
              <label style={{ fontSize:13, color:T.onSurfaceVariant, fontWeight:600, display:"block", marginBottom:4 }}>{f.l}</label>
              <input type={f.t} value={form[f.k]} onChange={e=>set(f.k,+e.target.value)}
                style={{ width:"100%", padding:"13px 14px", borderRadius:12, border:`1.5px solid ${T.outlineVariant}`,
                  fontSize:15, boxSizing:"border-box", background:T.surfaceContainerLow,
                  fontFamily:T.font, color:T.onSurface }}/>
            </div>
          ))}
          <div style={{ marginBottom:12 }}>
            <label style={{ fontSize:13, color:T.onSurfaceVariant, fontWeight:600, display:"block", marginBottom:4 }}>מטרה</label>
            <select value={form.goal} onChange={e=>set("goal",e.target.value)}
              style={{ width:"100%", padding:"10px 12px", borderRadius:10, border:`1.5px solid ${T.outlineVariant}`, fontSize:14 }}>
              <option value="lose">ירידה במשקל</option>
              <option value="gain">עלייה במסה</option>
              <option value="maintain">שמירה</option>
            </select>
          </div>
          <button onClick={save} style={{ width:"100%", height:52, background:T.primary, color:"#fff",
            border:"none", borderRadius:16, fontWeight:900, fontSize:15, cursor:"pointer",
            fontFamily:T.font }}>
            שמור שינויים
          </button>
        </div>
      ) : (
        <>
          {/* Stats */}
          <div style={{ display:"grid", gridTemplateColumns:"repeat(3,1fr)", gap:10, marginBottom:16 }}>
            {[
              { l:"משקל", v:profile.weight, u:'ק"ג' },
              { l:"יעד",  v:profile.targetWeight, u:'ק"ג' },
              { l:"גובה", v:profile.height, u:'ס"מ' },
              { l:"גיל",  v:profile.age, u:"שנים" },
              { l:"BMI",  v:fmt(profile.weight/((profile.height/100)**2)), u:"" },
              { l:"פעילות",v:actLabel, u:"" },
            ].map(s => (
              <div key={s.l} style={{ background:T.surfaceBright, borderRadius:14,
                padding:"14px 12px", boxShadow:"0 1px 6px rgba(0,0,0,0.04)", minHeight:76 }}>
                <div style={{ fontSize:9, fontWeight:700, letterSpacing:"0.12em",
                  textTransform:"uppercase", color:T.onSurfaceVariant, marginBottom:6 }}>{s.l}</div>
                <div style={{ fontWeight:900, color:T.onSurface, fontFamily:T.font,
                  fontSize: String(s.v).length > 6 ? 13 : 20, letterSpacing:"-0.3px" }}>
                  {s.v}{s.u && <span style={{fontSize:11,fontWeight:500,color:T.onSurfaceVariant}}> {s.u}</span>}
                </div>
              </div>
            ))}
          </div>

          {/* Calorie breakdown */}
          <div style={{ background:T.surfaceBright, borderRadius:16, padding:"16px 18px",
            boxShadow:"0 2px 12px rgba(0,0,0,0.04)", marginBottom:16 }}>
            <div style={{ fontSize:11, fontWeight:700, letterSpacing:"0.1em",
              textTransform:"uppercase", color:T.onSurfaceVariant, marginBottom:14 }}>חישוב קלורי</div>
            {[
              { l:"BMR (מטבוליזם בסיסי)", v:fmt(bmr),  u:'קק"ל' },
              { l:"TDEE (עם פעילות)",      v:tdee,      u:'קק"ל' },
              { l:"יעד קלורי יומי",        v:goals.cal, u:'קק"ל', bold:true },
              { l:"יעד חלבון",             v:goals.p,   u:"g" },
              { l:"יעד פחמימות",           v:goals.c,   u:"g" },
              { l:"יעד שומנים",            v:goals.f,   u:"g" },
            ].map((r,i,arr) => (
              <div key={r.l} style={{ display:"flex", justifyContent:"space-between",
                alignItems:"center", padding:"10px 0",
                borderBottom: i < arr.length-1 ? `1px solid ${T.outlineVariant}22` : "none" }}>
                <span style={{ fontSize:13, color:T.onSurfaceVariant }}>{r.l}</span>
                <span style={{ fontSize: r.bold ? 16 : 14, fontWeight: r.bold ? 900 : 700,
                  color: r.bold ? T.primary : T.onSurface, fontFamily:T.font }}>
                  {r.v} <span style={{fontSize:11,fontWeight:500}}>{r.u}</span>
                </span>
              </div>
            ))}
          </div>
        </>
      )}
    </div>
  );
}

// ─── Add Food Modal ───────────────────────────────────────────────────────────
function AddModal({ mode, onMode, onAdd, onClose }) {
  return (
    <div style={{ position:"fixed", inset:0, background:"rgba(12,15,16,0.5)",
      backdropFilter:"blur(4px)", zIndex:200,
      display:"flex", alignItems:"flex-end", justifyContent:"center" }}
      onClick={e => e.target === e.currentTarget && onClose()}>
      <div style={{ background:T.surfaceBright, borderRadius:"28px 28px 0 0",
        padding:"20px 20px 48px",
        width:"100%", maxWidth:480, maxHeight:"90vh", overflowY:"auto",
        boxShadow:"0 -8px 40px rgba(0,0,0,0.15)" }}
        dir="rtl">
        <div style={{ width:40, height:4, background:T.outlineVariant,
          borderRadius:99, margin:"0 auto 20px" }}/>

        {mode === "method" && <MethodSelect onMode={onMode}/>}
        {mode === "manual"  && <ManualAdd onAdd={onAdd} onBack={()=>onMode("method")} />}
        {mode === "barcode" && <BarcodeAdd onAdd={onAdd} onBack={()=>onMode("method")} />}
        {mode === "photo"   && <PhotoAdd onAdd={onAdd} onBack={()=>onMode("method")} />}
        {mode === "meal"    && <MealAdd onAdd={onAdd} onBack={()=>onMode("method")} />}
      </div>
    </div>
  );
}

function MethodSelect({ onMode }) {
  const methods = [
    { id:"manual",  icon:"🔍", title:"חיפוש ידני",       sub:"חפש מהמאגר שלנו" },
    { id:"barcode", icon:"📷", title:"סריקת ברקוד",      sub:"סרוק מוצר ארוז" },
    { id:"photo",   icon:"📸", title:"צילום תווית",       sub:"זהה מוצר מתמונה" },
    { id:"meal",    icon:"🍽️", title:"צילום מנה",        sub:"הערכת קלוריות חכמה" },
  ];
  return (
    <div>
      <h3 style={{ margin:"0 0 20px", fontSize:22, fontWeight:900, letterSpacing:"-0.5px",
        color:T.onSurface, fontFamily:T.font }}>הוסף אוכל</h3>
      <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:10 }}>
        {methods.map(m => (
          <button key={m.id} onClick={()=>onMode(m.id)}
            style={{ background:T.surfaceContainerLow, border:`1px solid ${T.outlineVariant}33`,
              borderRadius:16, padding:"18px 14px", cursor:"pointer", textAlign:"right",
              display:"flex", flexDirection:"column", gap:8,
              transition:"background .15s",
            }}
            onMouseEnter={e=>e.currentTarget.style.background=T.surfaceContainer}
            onMouseLeave={e=>e.currentTarget.style.background=T.surfaceContainerLow}>
            <span style={{ fontSize:28 }}>{m.icon}</span>
            <div>
              <div style={{ fontWeight:800, fontSize:14, color:T.onSurface,
                fontFamily:T.font }}>{m.title}</div>
              <div style={{ fontSize:12, color:T.onSurfaceVariant, marginTop:2 }}>{m.sub}</div>
            </div>
          </button>
        ))}
      </div>
    </div>
  );
}

const CAT_COLORS = {
  "חטיף":       { bg:"#FAECE7", color:"#993C1D" },
  "חלבון":      { bg:T.tertiaryContainer, color:"#185FA5" },
  "פחמימות":    { bg:"#FAEEDA", color:T.secondaryDim },
  "שומנים":     { bg:"#EAF3DE", color:T.primaryDim },
  "ירקות":      { bg:"#E1F5EE", color:"#0F6E56" },
  "פירות":      { bg:"#FBEAF0", color:"#72243E" },
  "ממרח":       { bg:"#FAEEDA", color:T.secondaryDim },
  "שתייה":      { bg:T.tertiaryContainer, color:"#185FA5" },
  "ישראלי":     { bg:"#EAF3DE", color:T.primaryDim },
  "יהודי":      { bg:"#FBEAF0", color:"#72243E" },
  "ממתקים":     { bg:"#FBEAF0", color:"#72243E" },
  "אגוזים":     { bg:"#FAEEDA", color:T.secondaryDim },
  "מזון מהיר":  { bg:"#FAECE7", color:"#993C1D" },
  "מקדונלדס":   { bg:"#FAEEDA", color:T.secondaryDim },
  "בורגר קינג": { bg:"#FAECE7", color:"#993C1D" },
  "פיצה":       { bg:"#FAECE7", color:"#993C1D" },
  "KFC":        { bg:"#FAECE7", color:"#993C1D" },
  "מסעדות":     { bg:"#F1EFE8", color:"#5F5E5A" },
  "סושי":       { bg:"#E1F5EE", color:"#0F6E56" },
  "ספורט":      { bg:T.tertiaryContainer, color:"#185FA5" },
  "אלכוהול":    { bg:"#F1EFE8", color:"#5F5E5A" },
  "ארוחת בוקר": { bg:"#FAEEDA", color:T.secondaryDim },
  "מרק":        { bg:"#E1F5EE", color:"#0F6E56" },
};

function CatBadge({ cat }) {
  const s = CAT_COLORS[cat] || { bg:T.surfaceContainerHighest, color:"#5F5E5A" };
  return (
    <span style={{ fontSize:10, fontWeight:700, padding:"2px 7px", borderRadius:99,
      background:s.bg, color:s.color, whiteSpace:"nowrap" }}>{cat}</span>
  );
}

// Highlight matching substring in text
function HighlightMatch({ text, query }) {
  if (!query) return <>{text}</>;
  const q = query.toLowerCase();
  const idx = text.toLowerCase().indexOf(q);
  if (idx === -1) return <>{text}</>;
  return <>
    {text.slice(0, idx)}
    <mark style={{ background:"#c0dd97", borderRadius:3, padding:"0 1px" }}>{text.slice(idx, idx+q.length)}</mark>
    {text.slice(idx+q.length)}
  </>;
}

function ManualAdd({ onAdd, onBack }) {
  const [search, setSearch] = useState("");
  const [selected, setSelected] = useState(null);
  const [qty, setQty] = useState(100);
  const [mealType, setMealType] = useState("ארוחת בוקר");
  const inputRef = useRef(null);

  useEffect(() => { inputRef.current?.focus(); }, []);

  const results = searchFoods(search);

  // When user selects, prefill with smart default qty
  function select(f) {
    setSelected(f);
    const dq = f.defaultQty;
    // For per-unit items, qty=1 means 1 unit; for 100g based, use defaultQty
    setQty(f.unit === "יחידה" || f.unit === "כוס" || f.unit === "מנה" || f.unit === "פרוסה" || f.unit === "פחית" || f.unit === "כדור" ? 1 : (dq || 100));
  }

  // Scale: for unit-based items qty is count, for g/ml based it's grams
  const isUnit = selected && ["יחידה","כוס","מנה","פרוסה","פחית","כדור"].includes(selected.unit);
  const scale = isUnit ? qty : (qty / 100);

  function confirm() {
    if (!selected) return;
    const qtyLabel = isUnit ? `×${qty}` : `${qty}g`;
    onAdd({
      name: `${selected.name} (${qtyLabel})`,
      cal: Math.round(selected.cal * scale),
      p:   Math.round(selected.p   * scale * 10) / 10,
      c:   Math.round(selected.c   * scale * 10) / 10,
      f:   Math.round(selected.f   * scale * 10) / 10,
      meal: mealType,
      source: "manual",
    });
  }

  return (
    <div>
      <BackButton onClick={onBack} label="חיפוש ידני" />

      {/* Search input */}
      <div style={{ position:"relative", marginBottom:12 }}>
        <input
          ref={inputRef}
          placeholder="חפש: במבה, לאטה, שניצל, chicken..."
          value={search}
          onChange={e => { setSearch(e.target.value); setSelected(null); }}
          style={{ width:"100%", padding:"12px 44px 12px 14px", borderRadius:14,
            border:`1.5px solid ${T.outlineVariant}`, fontSize:15, boxSizing:"border-box",
            background:T.surfaceContainerLow, fontFamily:T.font, color:T.onSurface }}
        />
        <span style={{ position:"absolute", top:"50%", right:14, transform:"translateY(-50%)",
          fontSize:18, pointerEvents:"none" }}>🔍</span>
      </div>

      {/* Hint chips when empty */}
      {search.length === 0 && !selected && (
        <div style={{ marginBottom:10 }}>
          <div style={{ fontSize:11, color:T.outlineVariant, marginBottom:6, fontWeight:600 }}>חיפושים נפוצים:</div>
          <div style={{ display:"flex", flexWrap:"wrap", gap:6 }}>
            {["במבה","ביסלי","גומי","מצה","קניידלך","ביג מק","שניצל","חומוס","אבוקדו","לאטה","פיצה","קרמבו","סניקרס","וופל","שאורמה","נאגטס","קסדייה","ראמן","קינואה","פטה","קשיו","סרדינים","כוסמת"].map(hint => (
              <button key={hint} onClick={() => setSearch(hint)}
                style={{ padding:"5px 12px", borderRadius:99, border:"1px solid #e0dec8",
                  background:T.surfaceContainerLow, fontSize:13, cursor:"pointer", color:T.onSurfaceVariant }}>
                {hint}
              </button>
            ))}
          </div>
        </div>
      )}

      {!selected ? (
        <div style={{ maxHeight:320, overflowY:"auto" }}>
          {results.length === 0 && search.length > 0 ? (
            <div style={{ textAlign:"center", padding:"24px 0", color:T.outlineVariant, fontSize:13 }}>
              <div style={{ fontSize:32, marginBottom:8 }}>🤔</div>
              לא מצאנו "{search}"<br/>נסה שם אחר או הוסף ידנית
            </div>
          ) : results.map(f => (
            <button key={f.id} onClick={() => select(f)}
              style={{ width:"100%", background:T.surface, border:`1px solid ${T.outlineVariant}33`,
                borderRadius:10, padding:"10px 14px", cursor:"pointer", textAlign:"right",
                display:"flex", justifyContent:"space-between", alignItems:"center",
                marginBottom:6, gap:8 }}>
              <div style={{ flex:1, minWidth:0 }}>
                <div style={{ display:"flex", alignItems:"center", gap:6, flexWrap:"wrap" }}>
                  <span style={{ fontWeight:700, fontSize:14 }}>
                    <HighlightMatch text={f.name} query={search} />
                  </span>
                  <CatBadge cat={f.cat}/>
                </div>
                {f.brand && <div style={{ fontSize:11, color:T.outlineVariant }}>{f.brand}</div>}
                <div style={{ fontSize:12, color:T.outlineVariant, marginTop:2 }}>
                  ח:{f.p}g &nbsp;פ:{f.c}g &nbsp;ש:{f.f}g
                </div>
              </div>
              <div style={{ textAlign:"center", flexShrink:0 }}>
                <div style={{ fontWeight:800, color:T.primary, fontSize:16 }}>{f.cal}</div>
                <div style={{ fontSize:10, color:T.outlineVariant }}>קק"ל/100{f.unit==="100ml"?"ml":"g"}</div>
              </div>
            </button>
          ))}
        </div>
      ) : (
        <div>
          {/* Selected food card */}
          <div style={{ background:T.primaryContainer, borderRadius:16, padding:16, marginBottom:14 }}>
            <div style={{ display:"flex", justifyContent:"space-between", alignItems:"flex-start",
              marginBottom:8 }}>
              <div style={{ flex:1 }}>
                <div style={{ fontWeight:900, fontSize:16, color:T.onPrimaryContainer,
                  fontFamily:T.font, letterSpacing:"-0.3px", marginBottom:2 }}>{selected.name}</div>
                {selected.brand && <div style={{ fontSize:12, color:T.onPrimaryContainer,
                  opacity:0.7 }}>{selected.brand}</div>}
              </div>
              <CatBadge cat={selected.cat}/>
            </div>
            <div style={{ fontSize:12, color:T.onPrimaryContainer, opacity:0.75 }}>
              לכל 100{selected.unit==="100ml"?"ml":"g"}: {selected.cal} קק"ל &nbsp;·&nbsp;
              ח:{selected.p}g &nbsp;פ:{selected.c}g &nbsp;ש:{selected.f}g
            </div>
          </div>

          {/* Quantity */}
          <label style={{ fontSize:13, fontWeight:600, color:T.onSurfaceVariant, display:"block", marginBottom:6 }}>
            {isUnit ? `כמות (${selected.unit})` : `משקל (${selected.unit === "100ml" ? "מ\"ל" : "גרם"})`}
          </label>
          <div style={{ display:"flex", alignItems:"center", gap:8, marginBottom:12 }}>
            <button onClick={() => setQty(q => Math.max(1, q - (isUnit?1:10)))}
              style={{ width:48, height:48, borderRadius:12, border:`1.5px solid ${T.outlineVariant}`,
                background:T.surfaceContainerLow, fontSize:22, cursor:"pointer",
                fontWeight:700, color:T.onSurface }}>−</button>
            <input type="number" value={qty} min={1} onChange={e=>setQty(+e.target.value)}
              style={{ flex:1, padding:"10px 12px", borderRadius:10, border:`1.5px solid ${T.outlineVariant}`,
                fontSize:16, textAlign:"center", fontWeight:700, boxSizing:"border-box" }}/>
            <button onClick={() => setQty(q => q + (isUnit?1:10))}
              style={{ width:48, height:48, borderRadius:12, border:`1.5px solid ${T.outlineVariant}`,
                background:T.surfaceContainerLow, fontSize:22, cursor:"pointer",
                fontWeight:700, color:T.onSurface }}>+</button>
          </div>

          {/* Quick quantity chips */}
          {!isUnit && (
            <div style={{ display:"flex", gap:6, marginBottom:12, flexWrap:"wrap" }}>
              {[50,100,150,200,250,300].map(q => (
                <button key={q} onClick={()=>setQty(q)}
                  style={{ padding:"5px 12px", borderRadius:99,
                    border:`1.5px solid ${qty===q ? T.primary : "#e0dec8"}`,
                    background: qty===q ? T.primaryContainer+"66" : T.surface,
                    color: qty===q ? T.primaryDim : "#888",
                    fontSize:12, cursor:"pointer", fontWeight: qty===q ? 700 : 400 }}>
                  {q}g
                </button>
              ))}
            </div>
          )}

          <MealTypeSelect value={mealType} onChange={setMealType}/>

          {/* Totals preview */}
          <div style={{ background:T.surfaceContainerLow, borderRadius:10, padding:"10px 14px",
            marginBottom:14, display:"flex", justifyContent:"space-between", alignItems:"center" }}>
            <div style={{ fontSize:11, fontWeight:700, letterSpacing:"0.1em",
              textTransform:"uppercase", color:T.onSurfaceVariant, marginBottom:6 }}>סה"כ</div>
            <div style={{ display:"flex", alignItems:"baseline", gap:14 }}>
              <span style={{ fontWeight:900, fontSize:22, color:T.primary, fontFamily:T.font }}>
                {Math.round(selected.cal * scale)}<span style={{fontSize:12, fontWeight:500}}> קק"ל</span>
              </span>
              <span style={{ fontSize:13, color:"#3b82f6", fontWeight:700 }}>ח {Math.round(selected.p*scale*10)/10}g</span>
              <span style={{ fontSize:13, color:T.secondary, fontWeight:700 }}>פ {Math.round(selected.c*scale*10)/10}g</span>
              <span style={{ fontSize:13, color:"#f43f5e", fontWeight:700 }}>ש {Math.round(selected.f*scale*10)/10}g</span>
            </div>
          </div>

          <div style={{ display:"flex", gap:8 }}>
            <button onClick={()=>setSelected(null)} style={{ flex:1, height:52, border:`1.5px solid ${T.outlineVariant}`,
              borderRadius:16, background:T.surfaceBright, cursor:"pointer",
              fontWeight:700, fontSize:14, color:T.onSurface }}>← חזרה</button>
            <button onClick={confirm} style={{ flex:2, height:52, background:T.primary, color:"#fff",
              border:"none", borderRadius:16, fontWeight:800, fontSize:15, cursor:"pointer",
              fontFamily:T.font }}>הוסף ליומן ✓</button>
          </div>
        </div>
      )}
    </div>
  );
}

function BarcodeAdd({ onAdd, onBack }) {
  const [step, setStep] = useState("scan"); // scan | result
  const [result, setResult] = useState(null);
  const [qty, setQty] = useState(100);
  const [mealType, setMealType] = useState("ארוחת בוקר");
  const [scanning, setScanning] = useState(false);

  function simulateScan() {
    setScanning(true);
    setTimeout(() => {
      const r = SCAN_RESULTS.barcode[Math.floor(Math.random()*SCAN_RESULTS.barcode.length)];
      setResult(r);
      setStep("result");
      setScanning(false);
    }, 1800);
  }

  function confirm() {
    const scale = qty / 100;
    onAdd({
      name: result.name,
      cal: Math.round(result.cal * scale),
      p:   Math.round(result.p * scale * 10) / 10,
      c:   Math.round(result.c * scale * 10) / 10,
      f:   Math.round(result.f * scale * 10) / 10,
      meal: mealType,
      source: "barcode",
    });
  }

  return (
    <div>
      <BackButton onClick={onBack} label="סריקת ברקוד" />
      {step === "scan" ? (
        <div style={{ textAlign:"center", padding:"20px 0" }}>
          {/* Simulated scanner viewport */}
          <div style={{ width:220, height:160, border:`2px solid ${T.primary}`, borderRadius:20,
            margin:"0 auto 16px", position:"relative", background:T.surfaceContainerLow,
            display:"flex", alignItems:"center", justifyContent:"center", overflow:"hidden" }}>
            {scanning ? (
              <>
                <div style={{ position:"absolute", inset:0, background:"linear-gradient(to bottom, transparent 48%, rgba(100,180,80,.15) 49%, rgba(100,180,80,.15) 51%, transparent 52%)",
                  animation:"scanLine 1.2s ease-in-out infinite" }}/>
                <style>{`@keyframes scanLine{0%{backgroundPositionY:0%}100%{backgroundPositionY:200%}}`}</style>
                <span style={{ fontSize:32 }}>📦</span>
              </>
            ) : (
              <div>
                <ScanIcon/> 
                <p style={{ fontSize:12, color:T.outlineVariant, margin:"8px 0 0" }}>כוון לברקוד</p>
              </div>
            )}
            {/* Corner indicators */}
            {["top-right","top-left","bottom-right","bottom-left"].map(c => {
              const [v,h] = c.split("-");
              return <div key={c} style={{ position:"absolute", [v]:6, [h]:6,
                width:18, height:18,
                borderTop: v==="top" ? `3px solid ${T.primary}` : "none",
                borderBottom: v==="bottom" ? `3px solid ${T.primary}` : "none",
                borderRight: h==="right" ? `3px solid ${T.primary}` : "none",
                borderLeft: h==="left" ? `3px solid ${T.primary}` : "none",
              }}/>;
            })}
          </div>
          <p style={{ color:T.onSurfaceVariant, fontSize:13, marginBottom:16 }}>לחץ לסימולציה של סריקה</p>
          <button onClick={simulateScan} disabled={scanning}
            style={{ background: scanning ? T.surfaceContainerHigh : T.primary, color:"#fff", border:"none",
              borderRadius:16, padding:"14px 36px", fontWeight:800, fontSize:15,
              cursor: scanning ? "not-allowed":"pointer", fontFamily:T.font }}>
            {scanning ? "סורק..." : "סרוק ברקוד 📷"}
          </button>
        </div>
      ) : (
        <div>
          <div style={{ background:T.primaryContainer, borderRadius:16, padding:16, marginBottom:14 }}>
            <div style={{ fontSize:10, fontWeight:700, letterSpacing:"0.1em",
              textTransform:"uppercase", color:T.onPrimaryContainer, opacity:0.75, marginBottom:6 }}>✓ מוצר זוהה</div>
            <div style={{ fontWeight:900, fontSize:17, color:T.onPrimaryContainer,
              fontFamily:T.font, letterSpacing:"-0.3px" }}>{result.name}</div>
            {result.brand && <div style={{ fontSize:12, color:T.onPrimaryContainer, opacity:0.7, marginTop:1 }}>{result.brand}</div>}
            <div style={{ display:"flex", gap:14, marginTop:10 }}>
              {[["קק"ל",result.cal],["חלבון",result.p+"g"],["פחמ'",result.c+"g"],["שומן",result.f+"g"]].map(([l,v])=>(
                <div key={l}>
                  <div style={{ fontSize:9, color:T.onPrimaryContainer, opacity:0.6, fontWeight:700 }}>{l}</div>
                  <div style={{ fontSize:15, fontWeight:900, color:T.onPrimaryContainer }}>{v}</div>
                </div>
              ))}
            </div>
          </div>
          <label style={{ fontSize:13, fontWeight:600, color:T.onSurfaceVariant, display:"block", marginBottom:6 }}>כמות (גרם)</label>
          <input type="number" value={qty} onChange={e=>setQty(+e.target.value)} min={1}
            style={{ width:"100%", padding:"10px 12px", borderRadius:10, border:`1.5px solid ${T.outlineVariant}`,
              fontSize:15, marginBottom:12, boxSizing:"border-box" }}/>
          <MealTypeSelect value={mealType} onChange={setMealType}/>
          <div style={{ display:"flex", gap:8 }}>
            <button onClick={()=>setStep("scan")} style={{ flex:1, height:52, border:`1.5px solid ${T.outlineVariant}`,
              borderRadius:16, background:T.surfaceContainerLow, cursor:"pointer",
              fontWeight:700, color:T.onSurface }}>סרוק מחדש</button>
            <button onClick={confirm} style={{ flex:2, height:52, background:T.primary, color:"#fff",
              border:"none", borderRadius:16, fontWeight:900, fontSize:15,
              cursor:"pointer", fontFamily:T.font }}>אישור ✓</button>
          </div>
        </div>
      )}
    </div>
  );
}

function PhotoAdd({ onAdd, onBack }) {
  const [step, setStep] = useState("capture"); // capture | result
  const [result, setResult] = useState(null);
  const [qty, setQty] = useState(100);
  const [mealType, setMealType] = useState("ארוחת בוקר");
  const [processing, setProcessing] = useState(false);

  function simulatePhoto() {
    setProcessing(true);
    setTimeout(() => {
      const r = SCAN_RESULTS.photo[Math.floor(Math.random()*SCAN_RESULTS.photo.length)];
      setResult(r);
      setStep("result");
      setProcessing(false);
    }, 2200);
  }

  function confirm() {
    const scale = qty / 100;
    onAdd({
      name: result.name,
      cal: Math.round(result.cal * scale),
      p:   Math.round(result.p * scale * 10) / 10,
      c:   Math.round(result.c * scale * 10) / 10,
      f:   Math.round(result.f * scale * 10) / 10,
      meal: mealType,
      source: "photo",
    });
  }

  return (
    <div>
      <BackButton onClick={onBack} label="צילום מוצר/תווית" />
      {step === "capture" ? (
        <div style={{ textAlign:"center", padding:"20px 0" }}>
          <div style={{ width:200, height:200, borderRadius:16, background:T.surfaceContainerLow,
            border:`2px dashed ${T.primaryFixed}`, margin:"0 auto 16px",
            display:"flex", flexDirection:"column", alignItems:"center", justifyContent:"center", gap:8 }}>
            {processing ? (
              <div>
                <div style={{ fontSize:40 }}>🔍</div>
                <p style={{ fontSize:12, color:T.primary, margin:0 }}>מנתח תמונה...</p>
              </div>
            ) : (
              <>
                <CamIcon/>
                <p style={{ fontSize:12, color:T.outlineVariant, margin:0 }}>צלם תווית תזונה</p>
              </>
            )}
          </div>
          <button onClick={simulatePhoto} disabled={processing}
            style={{ background: processing ? T.surfaceContainerHigh : T.primary, color:"#fff", border:"none",
              borderRadius:16, padding:"14px 36px", fontWeight:800, fontSize:15,
              cursor: processing ? "not-allowed":"pointer", fontFamily:T.font }}>
            {processing ? "מעבד..." : "צלם מוצר 📸"}
          </button>
        </div>
      ) : (
        <div>
          <div style={{ background:T.secondaryContainer+"33", borderRadius:12, padding:12, marginBottom:12,
            border:`1px solid ${T.secondaryContainer}`, display:"flex", gap:8, alignItems:"center" }}>
            <span style={{ fontSize:16 }}>⚠️</span>
            <p style={{ margin:0, fontSize:12, color:T.secondaryDim }}>
              זיהוי בטחון: {result.confidence}% – זוהי הערכה. אנא אמת את הנתונים.
            </p>
          </div>
          <div style={{ background:T.primaryContainer, borderRadius:16, padding:16, marginBottom:14 }}>
            <div style={{ fontSize:10, fontWeight:700, letterSpacing:"0.1em",
              textTransform:"uppercase", color:T.onPrimaryContainer, opacity:0.75, marginBottom:6 }}>✓ מוצר שזוהה</div>
            <div style={{ fontWeight:900, fontSize:17, color:T.onPrimaryContainer,
              fontFamily:T.font, letterSpacing:"-0.3px" }}>{result.name}</div>
            {result.brand && <div style={{ fontSize:12, color:T.onPrimaryContainer, opacity:0.7, marginTop:1 }}>{result.brand}</div>}
            <div style={{ display:"flex", gap:14, marginTop:10 }}>
              {[["קק"ל",result.cal],["חלבון",result.p+"g"],["פחמ'",result.c+"g"],["שומן",result.f+"g"]].map(([l,v])=>(
                <div key={l}>
                  <div style={{ fontSize:9, color:T.onPrimaryContainer, opacity:0.6, fontWeight:700 }}>{l}</div>
                  <div style={{ fontSize:15, fontWeight:900, color:T.onPrimaryContainer }}>{v}</div>
                </div>
              ))}
            </div>
          </div>
          <label style={{ fontSize:13, fontWeight:600, color:T.onSurfaceVariant, display:"block", marginBottom:6 }}>כמות (גרם)</label>
          <input type="number" value={qty} onChange={e=>setQty(+e.target.value)} min={1}
            style={{ width:"100%", padding:"10px 12px", borderRadius:10, border:`1.5px solid ${T.outlineVariant}`,
              fontSize:15, marginBottom:12, boxSizing:"border-box" }}/>
          <MealTypeSelect value={mealType} onChange={setMealType}/>
          <div style={{ display:"flex", gap:8 }}>
            <button onClick={()=>setStep("capture")} style={{ flex:1, height:52, border:`1.5px solid ${T.outlineVariant}`,
              borderRadius:16, background:T.surfaceContainerLow, cursor:"pointer",
              fontWeight:700, color:T.onSurface }}>צלם מחדש</button>
            <button onClick={confirm} style={{ flex:2, height:52, background:T.primary, color:"#fff",
              border:"none", borderRadius:16, fontWeight:900, fontSize:15, cursor:"pointer", fontFamily:T.font }}>אשר ✓</button>
          </div>
        </div>
      )}
    </div>
  );
}

function MealAdd({ onAdd, onBack }) {
  const [step, setStep] = useState("capture"); // capture | review
  const [result, setResult] = useState(null);
  const [items, setItems] = useState([]);
  const [mealType, setMealType] = useState("ארוחת צהריים");
  const [processing, setProcessing] = useState(false);

  function simulateMeal() {
    setProcessing(true);
    setTimeout(() => {
      const r = SCAN_RESULTS.meal[Math.floor(Math.random()*SCAN_RESULTS.meal.length)];
      setResult(r);
      setItems(r.items.map((it,i) => ({ ...it, id:i, included:true })));
      setStep("review");
      setProcessing(false);
    }, 2500);
  }

  function toggleItem(id) {
    setItems(prev => prev.map(it => it.id === id ? { ...it, included:!it.included } : it));
  }
  function updateQty(id, qty) {
    setItems(prev => prev.map(it => it.id === id ? { ...it, qty } : it));
  }

  const totalCal = items.filter(i=>i.included).reduce((a,it)=>a + Math.round(it.cal * it.qty/100),0);
  const totalP   = items.filter(i=>i.included).reduce((a,it)=>a + it.p * it.qty/100,0);
  const totalC   = items.filter(i=>i.included).reduce((a,it)=>a + it.c * it.qty/100,0);
  const totalF   = items.filter(i=>i.included).reduce((a,it)=>a + it.f * it.qty/100,0);

  function confirm() {
    items.filter(i=>i.included).forEach(it => {
      const scale = it.qty / 100;
      onAdd({
        name: it.name + ` (${it.qty}g)`,
        cal: Math.round(it.cal * scale),
        p:   Math.round(it.p * scale * 10) / 10,
        c:   Math.round(it.c * scale * 10) / 10,
        f:   Math.round(it.f * scale * 10) / 10,
        meal: mealType,
        source: "meal",
      });
    });
  }

  return (
    <div>
      <BackButton onClick={onBack} label="צילום מנה" />
      {step === "capture" ? (
        <div style={{ textAlign:"center", padding:"20px 0" }}>
          <div style={{ width:220, height:180, borderRadius:20, background:T.surfaceContainerLow,
            border:`2px dashed ${T.primaryFixed}`, margin:"0 auto 16px",
            display:"flex", flexDirection:"column", alignItems:"center", justifyContent:"center", gap:8 }}>
            {processing ? (
              <div>
                <div style={{ fontSize:40 }}>🤖</div>
                <p style={{ fontSize:12, color:T.primary, margin:0 }}>מזהה מרכיבים...</p>
              </div>
            ) : (
              <>
                <span style={{ fontSize:36 }}>🍽️</span>
                <p style={{ fontSize:12, color:T.outlineVariant, margin:0 }}>צלם את הצלחת שלך</p>
              </>
            )}
          </div>
          <p style={{ color:T.onSurfaceVariant, fontSize:13, marginBottom:16 }}>
            AI מזהה את המרכיבים ומעריך קלוריות
          </p>
          <button onClick={simulateMeal} disabled={processing}
            style={{ background: processing ? T.surfaceContainerHigh : T.primary, color:"#fff", border:"none",
              borderRadius:16, padding:"14px 36px", fontWeight:800, fontSize:15,
              cursor: processing ? "not-allowed":"pointer", fontFamily:T.font }}>
            {processing ? "מנתח..." : "צלם מנה 🍽️"}
          </button>
        </div>
      ) : (
        <div>
          <div style={{ background:T.secondaryContainer+"33", borderRadius:12, padding:12, marginBottom:12,
            border:`1px solid ${T.secondaryContainer}`, display:"flex", gap:8 }}>
            <span style={{ fontSize:16 }}>🤖</span>
            <p style={{ margin:0, fontSize:12, color:T.secondaryDim }}>
              זיהוי AI ({result.confidence}% בטחון) – זו הערכה בלבד! אמת את המרכיבים והכמויות.
            </p>
          </div>

          {items.map(it => (
            <div key={it.id} style={{ background: it.included ? "#fff" : "#f5f3ee",
              borderRadius:12, padding:"10px 14px", marginBottom:8, border:`1px solid ${T.outlineVariant}33`,
              display:"flex", alignItems:"center", gap:10 }}>
              <button onClick={()=>toggleItem(it.id)}
                style={{ width:24, height:24, borderRadius:6,
                  background: it.included ? T.primary : "#e0dec8",
                  border:"none", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center",
                  flexShrink:0 }}>
                {it.included && <span style={{ color:"#fff", fontSize:14 }}>✓</span>}
              </button>
              <div style={{ flex:1 }}>
                <div style={{ fontWeight:700, fontSize:14, color: it.included ? T.onSurface : "#aaa" }}>{it.name}</div>
                <div style={{ fontSize:12, color:T.outlineVariant }}>{it.cal} קק"ל/100g</div>
              </div>
              <div style={{ display:"flex", alignItems:"center", gap:4 }}>
                <input type="number" value={it.qty} min={1}
                  onChange={e=>updateQty(it.id,+e.target.value)}
                  style={{ width:60, padding:"4px 6px", borderRadius:8, border:"1px solid #e0dec8",
                    fontSize:13, textAlign:"center" }}/>
                <span style={{ fontSize:11, color:T.outlineVariant }}>g</span>
              </div>
            </div>
          ))}

          <MealTypeSelect value={mealType} onChange={setMealType}/>

          <div style={{ background:T.primaryContainer+"66", borderRadius:10, padding:"10px 14px", marginBottom:12 }}>
            <div style={{ fontWeight:800, fontSize:15, color:T.primaryDim }}>
              סה"כ: {totalCal} קק"ל
            </div>
            <div style={{ fontSize:12, color:T.onSurfaceVariant }}>
              ח:{Math.round(totalP*10)/10}g פ:{Math.round(totalC*10)/10}g ש:{Math.round(totalF*10)/10}g
            </div>
          </div>

          <button onClick={confirm} style={{ width:"100%", height:52, background:T.primary, color:"#fff",
            border:"none", borderRadius:16, fontWeight:900, fontSize:15,
            cursor:"pointer", fontFamily:T.font }}>
            הוסף לארוחה ✓
          </button>
        </div>
      )}
    </div>
  );
}

// ─── Shared components ────────────────────────────────────────────────────────
function MealTypeSelect({ value, onChange }) {
  const meals = ["ארוחת בוקר","ארוחת צהריים","ארוחת ערב","ביניים/נשנוש"];
  return (
    <div style={{ marginBottom:16 }}>
      <div style={{ fontSize:11, fontWeight:700, letterSpacing:"0.1em",
        textTransform:"uppercase", color:T.onSurfaceVariant, marginBottom:8 }}>ארוחה</div>
      <div style={{ display:"flex", gap:6, flexWrap:"wrap" }}>
        {meals.map(m => {
          const active = value === m;
          return (
            <button key={m} onClick={()=>onChange(m)}
              style={{ padding:"7px 14px", borderRadius:99,
                border:`1.5px solid ${active ? T.primary : T.outlineVariant}`,
                background: active ? T.primaryContainer : "transparent",
                color: active ? T.onPrimaryContainer : T.onSurfaceVariant,
                fontWeight: active ? 700 : 500,
                fontSize:13, cursor:"pointer", fontFamily:T.font,
                transition:"all .15s" }}>
              {m}
            </button>
          );
        })}
      </div>
    </div>
  );
}

function BackButton({ onClick, label }) {
  return (
    <div style={{ display:"flex", alignItems:"center", gap:12, marginBottom:20 }}>
      <button onClick={onClick} style={{ background:T.surfaceContainerLow, border:"none",
        cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center",
        color:T.onSurface, padding:0, width:36, height:36, borderRadius:12 }}>
        <BackIcon/>
      </button>
      <h3 style={{ margin:0, fontSize:20, fontWeight:900, color:T.onSurface,
        letterSpacing:"-0.3px", fontFamily:T.font }}>{label}</h3>
    </div>
  );
}

function EmptyState({ icon, title, subtitle }) {
  return (
    <div style={{ textAlign:"center", padding:"40px 20px" }}>
      <div style={{ fontSize:48, marginBottom:10 }}>{icon}</div>
      <div style={{ fontWeight:900, fontSize:17, color:T.onSurface, marginBottom:6, fontFamily:T.font }}>{title}</div>
      <div style={{ fontSize:14, color:T.onSurfaceVariant, fontWeight:500 }}>{subtitle}</div>
    </div>
  );
}

function groupByMeal(entries) {
  const groups = { "ארוחת בוקר":[], "ארוחת צהריים":[], "ארוחת ערב":[], "ביניים/נשנוש":[] };
  entries.forEach(e => {
    const m = e.meal || "ביניים/נשנוש";
    if (groups[m]) groups[m].push(e);
    else groups["ביניים/נשנוש"].push(e);
  });
  return groups;
}
