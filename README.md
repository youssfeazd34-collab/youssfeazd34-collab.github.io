# قرد الأدغال - مشروع أندرويد (Capacitor)

## ما تحتاجه على جهازك
- Node.js (نسخة LTS)
- Android Studio (يجيب معه Java و Android SDK)

## قبل ما تبدأ (مهم)
1. افتح `capacitor.config.json` وغيّر `appId` لمعرف خاص فيك، مثل `com.ahmed.junglemonkey`.
   هذا المعرف ما ينغير بعد ما تنشر التطبيق.
2. افتح `privacy.html` وغيّر `YOUR_EMAIL@example.com` لإيميلك، وارفعه على أي استضافة مجانية
   (مثل GitHub Pages) عشان تاخذ رابط تحطه في Play Console.

## بناء المشروع
```bash
npm install
npx cap add android
npx @capacitor/assets generate --android     # يولّد الأيقونة وشاشة البداية من مجلد assets
npx cap sync
npx cap open android                          # يفتح Android Studio
```

## عمل ملف النشر (AAB)
في Android Studio:
1. جرّب اللعبة أولاً على جوالك أو المحاكي (زر Run).
2. من القائمة: Build > Generate Signed App Bundle / APK > Android App Bundle.
3. أنشئ مفتاح توقيع (Keystore) جديد واحفظه وكلمة سره في مكان آمن. لو ضاع ما تقدر تحدّث التطبيق.
4. اختر release وسيطلع لك ملف `app-release.aab`.

لتحديث التطبيق لاحقاً: زد `versionCode` و `versionName` في `android/app/build.gradle`.

## الرفع على Play Console
1. أنشئ التطبيق (Create app) واختر Game ومجاني.
2. املأ: سياسة الخصوصية (رابط privacy.html)، التصنيف العمري، نموذج أمان البيانات
   (اللعبة ما تجمع بيانات)، الإعلانات (لا يوجد).
3. من مجلد `store`: الأيقونة `icon-512.png` والصورة `feature-graphic-1024x500.png`.
   النصوص جاهزة في `listing.txt`. لقطات الشاشة خذها من اللعبة على جوالك (2 على الأقل).
4. ارفع ملف AAB في مسار Closed testing.
5. إذا حسابك شخصي وأنشأته بعد 13 نوفمبر 2023: لازم 12 مختبر على الأقل يشاركون لمدة 14 يوم متواصل،
   ثم تقدّم على Production access.

## ملاحظات
- أزلت رابط خطوط Google من اللعبة عشان تشتغل بدون إنترنت، وتستخدم خط النظام.
  لو تبي خط "Lalezar" حمّله من Google Fonts وحطه في `www/` وأضف `@font-face` في `www/index.html`.
- لقفل اللعبة عمودياً، أضف `android:screenOrientation="portrait"` للـ activity في
  `android/app/src/main/AndroidManifest.xml`.
- اللعبة ما تطلب أي أذونات.
