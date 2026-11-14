# 🎬 TubeGenie

تطبيق ويب يصنع فيديوهات يوتيوب بالذكاء الاصطناعي ويرفعها مباشرة إلى قناتك. كل شيء يعمل داخل المتصفح ومجاناً.

## كيف يعمل
1. تكتب فكرة، فيكتب **Gemini** العنوان والوصف والوسوم والمشاهد
2. يصنع التطبيق الفيديو داخل المتصفح: خلفيات متحركة ونصوص وإيموجي وموسيقى مولّدة
3. يرفعه إلى يوتيوب عبر **YouTube Data API**، أو تشاركه إلى تطبيق يوتيوب

---

## الإعداد (مرة واحدة)

### 1) رفع التطبيق إلى GitHub Pages
1. أنشئ مستودعاً جديداً باسم `tubegenie`
2. ارفع الملفات: `index.html` و`manifest.json` و`sw.js` و`icon.svg`
3. من **Settings ← Pages** اختر الفرع `main` ثم **Save**
4. سيكون الرابط: `https://اسمك.github.io/tubegenie/`

### 2) مفتاح Gemini (مجاني)
1. افتح https://aistudio.google.com/apikey
2. اضغط **Create API key** ثم انسخه
3. ضعه في ⚙️ الإعدادات داخل التطبيق

### 3) Client ID للرفع إلى يوتيوب
1. افتح https://console.cloud.google.com وأنشئ مشروعاً جديداً
2. من **APIs & Services ← Library** ابحث عن **YouTube Data API v3** ثم **Enable**
3. من **OAuth consent screen** (أو Google Auth Platform):
   - النوع: **External**
   - أضف بريدك في **Test users**
4. من **Credentials ← Create Credentials ← OAuth client ID**:
   - النوع: **Web application**
   - في **Authorized JavaScript origins** أضف: `https://اسمك.github.io` (بدون `/tubegenie`)
5. انسخ **Client ID** وضعه في إعدادات التطبيق

---

## ⚠️ ملاحظات مهمة
- **الفيديوهات المرفوعة عبر API تكون خاصة (Private)** حتى يجتاز مشروعك تدقيق YouTube API Compliance Audit. للنشر العام الآن استخدم زر **📲 مشاركة** واختر تطبيق يوتيوب، أو حمّل الفيديو وارفعه يدوياً.
- الحصة اليومية الافتراضية تسمح بعدد محدود من الرفعات في اليوم (حوالي 6).
- أبقِ الشاشة مفتوحة أثناء صنع الفيديو، لأنه يُسجَّل بزمنه الحقيقي (30 إلى 60 ثانية).
- يعمل بأفضل شكل على **Chrome**. الفيديو يخرج بصيغة WebM أو MP4 حسب المتصفح، ويوتيوب يقبل الصيغتين.
- مفاتيحك محفوظة على جهازك فقط (localStorage).
