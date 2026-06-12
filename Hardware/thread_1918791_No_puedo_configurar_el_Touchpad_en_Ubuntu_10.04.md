---
title: "No puedo configurar el Touchpad en Ubuntu 10.04"
date: 2012-02-01
forum: Hardware
---

### Post by donmatas on 2012-02-01
Estimad@s:
tengo Ubuntu 10.04 instalado en un Dell Inspiron 1545 hace bastante tiempo.
Hasta ayer o antes de ayer, tenía desactivada la posibilidad de hacer "click" tocando el touchpad (lo que es una joda para quienes escribimos en el compu). No sé qué pasó y se activó (¿fue una actualización?) Lo peor es que desapareció la alternativa de desactivarlo que creo estaba en Sistema/preferencias/ratón (acompaño imagen del menú). 
Busqué en el CSU y encotré GSynaptics. El problema es que al ejecutarlo me apareció el siguiente mensaje:
```
GSynaptics no ha podido arrancar.
Necesita configurar la variable 'SHMConfig' al valor 'true' en el archivoxorg.conf o XF86Config que use GSynaptics
```

Después inenté con ThouchFreeze, pero no sirve.


¿alguien sabe qué puedo hacer?


gracias
DM

---

### Post by donmatas on 2012-02-02
como se fue volvió. Hoy prendí mi computador y sentí que todo andaba bien. Revisé Sistema/preferencias/ratón y verifiqué que todo había vuelto a la normalidad (como pueden ver en el adjunto)

---

### Post by El Potro on 2012-05-12
Hola Don Matas,

me pasó exactamente lo mismo que a vos, no me quedó otra que reiniciar el sistema (porque con reiniciar las X no me alcanzó).

Estos bugs malparidos, como el del panel de gnome la verdad que... a esta altura deberían estar solucionados, pero bue... Porque es ilógico tener que crear un xorg.conf sólo para esta opción, cuando por defecto Ubuntu 10.04 no usa el xorg.conf.

Buscando acerca de esto, encontré cómo configurar el touchpad con otro programa, desde la terminal. Se llama synclient. Para desactivar el "tapping" (que se presione el click izquierdo cuando tocas el touchpad), se hace así:

```
synclient TapButton1=0 TapButton2=0 TapButton3=0
```

En en blog de mi firma hay más info. Espero que sirva!

---

