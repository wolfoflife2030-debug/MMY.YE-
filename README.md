# MMY.YE — برنامج لوحة التحكم (ويندوز + أندرويد)

نفس الموقع (`www/index.html`) مُغلَّف كبرنامج:
- **ويندوز**: Electron → ملف تثبيت `.exe` + نسخة محمولة.
- **أندرويد**: Capacitor → ملف `.apk`.

## البناء التلقائي (الأسهل)
1. ارفع المجلد إلى مستودع GitHub.
2. من تبويب **Actions** اختر **Build Windows + Android** ثم **Run workflow**.
3. بعد انتهاء البناء نزّل الملفات من **Artifacts** (`MMY-Windows` و `MMY-Android`).
4. للنشر كإصدار: `git tag v1.0.0 && git push origin v1.0.0` فتظهر الملفات في **Releases**.

## البناء على جهازك (ويندوز)
```
npm install
npm start          # تشغيل تجريبي
npm run dist:win   # يخرج ملف التثبيت في dist/
```

## الأيقونات
`assets/windows-icon.png` و `assets/android-logo.png` هما الأصل؛ الأيقونات الجاهزة (خلفية بيضاء + حواف دائرية) في `build/`.
لإعادة توليدها: `python3 scripts/make_icons.py assets/windows-icon.png assets/android-logo.png build`

## ملاحظات
- البيانات تُحفظ محليًا داخل البرنامج (نفس سلوك الموقع)؛ صدّر نسخة احتياطية من الإعدادات بانتظام.
- اسم المستخدم الافتراضي `admin` وكلمة المرور `1234` وسيطلب البرنامج تغييرها.
- ملف APK الناتج من `assembleDebug` للتجربة؛ للنشر في Google Play يلزم توقيع Release.
