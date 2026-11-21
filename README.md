# AOD Enable (custom ROMs)
Overlay RRO que activa Pantalla siempre activa y la opcion de mostrar el fondo en el AOD en ROM AOSP/custom.
Probado en Redmi 9 (lancelot, LCD) con PixelOS Android 17 y KernelSU Next + meta-overlayfs.

## Requisitos
- Root (Magisk, o KernelSU con metamodulo) y Android 14+ (la opcion de fondo).
- Que el panel y el kernel soporten doze. El modulo no lo arregla si no.

## Instalar
Instalar el ZIP desde el gestor, borrar /data/system/package_cache y reiniciar.
Comprobar: cmd overlay list android | grep aod

## Valores (overlay-src/res/values/config.xml)
- config_dozeAlwaysOnDisplayAvailable: muestra la opcion de AOD.
- config_dozeComponent: servicio de doze del SystemUI (valor de AOSP).
- config_displayBlanksAfterDoze=false y config_screenBrightnessDoze=20: ajustados a un LCD. Quitarlos en AMOLED.
- config_dozeSupportsAodWallpaper: opcion de mostrar el fondo.

## Problemas
- El AOD no se ve con el ahorro de batería: settings put global battery_saver_constants disable_aod=false
- Si algo falla al arrancar: desactivar el modulo y reiniciar.
