---
title: "Sin captura de sonido"
date: 2010-08-29
forum: Hardware
---

### Post by donmatas on 2010-08-29
Estimad@s:

instalé Ubuntu 10.04 en un Sony Vaio. Todo funciona bien, salvo que no funciona la captura de sonido. Después de bastante prueba y error, logré que capturara por el micrófono pero botando el sonido por los parlantes, pero no graba ni sirve para skype (con alsamixer).   La placa es la siguiente:

```


$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```


¿alguien puede darme una mano?

---

### Post by josecuervo86 on 2010-08-31
Probaste ejecutando en consola
```
gstreamer-properties
```
Y cambiando las opciones de entrada y salida?

---

