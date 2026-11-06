# Directorio Dolorense

Directorio de negocios de Dolores Hidalgo: API REST local en Node + app Flutter (cliente HTTP, 5 estados de pantalla, pruebas con MockClient).

Desarrollo Móvil Integral · UTNG

## Requisitos
- Node.js 18+
- Flutter 3.x

## API
```bash
cd api
node server.js        # http://localhost:3000/negocios
```

## App
```bash
cd app
flutter create . --project-name directorio_dolores --platforms=android,ios
flutter pub get
flutter test
flutter run                                   # emulador Android (usa 10.0.2.2)
flutter run --dart-define=API_URL=http://TU-IP:3000   # celular real
```

### Android (solo desarrollo)
En `app/android/app/src/main/AndroidManifest.xml` agrega, antes de `<application`:
```xml
<uses-permission android:name="android.permission.INTERNET"/>
```
y dentro de `<application`: `android:usesCleartextTraffic="true"`.

### iOS (solo desarrollo)
En `ios/Runner/Info.plist` agrega `NSAppTransportSecurity` con `NSAllowsLocalNetworking = true`.

## Estructura
- `api/server.js`: API en memoria (GET, POST, PUT, DELETE)
- `app/lib/dominio`: Negocio y excepciones
- `app/lib/datos`: NegociosApi y configuración de URL
- `app/lib/presentacion`: ViewModel y pantalla
- `app/test`: pruebas
