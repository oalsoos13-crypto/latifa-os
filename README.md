# Latifa OS ☕

نظام تشغيل متكامل لـ **لطيفة كافيه** (فرعا الفحيحيل والسالمية) — تحليلات، تقارير تنفيذية، تقرير تحكّم بالأهداف، متابعة مسؤوليات آلية، ومركز رفع بيانات من فودكس. ملف واحد مستقل (`index.html`).

## التشغيل السريع
افتح `index.html` في المتصفح — يعمل فوراً بـ **وضع محلي** (بيانات على جهازك فقط).

## رابط حقيقي عبر GitHub Pages
Settings → Pages → Source: **Deploy from a branch** → `main` / `root` → Save. بعد دقيقة يعطيك رابطاً عاماً.

## قاعدة بيانات مشتركة + تسجيل دخول (Firebase — مجاني)
1. أنشئ مشروعاً على console.firebase.google.com
2. Authentication → فعّل **Email/Password**
3. Firestore Database → Create (Production mode)
4. Firestore → Rules:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{db}/documents {
       match /{document=**} { allow read, write: if request.auth != null; }
     }
   }
   ```
5. Project settings → Web app → انسخ `firebaseConfig`
6. في أول `index.html` املأ `FIREBASE_CONFIG` و `OWNER_EMAILS`

## الأدوار
مالك (كل شيء) · مدير · محلّل · كاشير · مشاهد — تُحدَّد من تبويب «المستخدمون».

## مصادر البيانات (فودكس)
الطلبات · الصندوق (Tills) · مبيعات الأحجام · المدفوعات · سطور المنتجات والمعدّلات · حركة المخزون · العملاء · قائمة أسعار وزارة التجارة (Excel) — تُسحب من تبويب «مركز الرفع» الذي يتعرّف على كل ملف تلقائياً.
