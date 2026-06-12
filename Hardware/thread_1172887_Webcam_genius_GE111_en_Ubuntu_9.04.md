---
title: "Webcam genius GE111 en Ubuntu 9.04"
date: 2009-05-29
forum: Hardware
---

### Post by DamianRa on 2009-05-29
Hola:
soy completamente nuevo en ubuntu. Instale la version 9.04, creo que es la ultima y no puedo hacer andar la webcam genius GE111 en Ubuntu 9.04. instale el paquete gsps-source o algo asi pero no me la toma a la cam.
cuando hago un lsusb me dice esto:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 093a:2471 Pixart Imaging, Inc. SoC PC-Camera
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
la cam supuestamente esta soportada por el driver, pero skype me muestra como una estatica pero verde y camorama directamente se cierra cuando termina de abri la ventana. me dice uknow error y se cierra.
como puedo usar la web cam? trabajo en video conferencia con ella y la necesito. con a E-messenger 112 de genius me hizo lo mmismo.. que sera?
gracias por estar...

damian
PD: si anda tego que volver a Güindors con la cola entre las patas...

---

### Post by Hei Ku on 2009-05-29
Las genius suelen traer un chipset variado, pero consistente en la mala calidad.

En fin, el paquete que instalaste supongo que sera el gspca-source, que no sirve de nada. Desinstalalo cuando puedas.

Instala y verifica que tengas actualizados los paquetes xserver-xorg-video-v4l y libv4l-0.

Despues de eso, volve a probar con Cheese.

---

### Post by SLA_leandrin on 2009-05-29
> **DamianRa said:**
> skype me muestra como una estatica pero verde y camorama directamente se cierra cuando termina de abri la ventana. me dice uknow error y se cierra.
como puedo usar la web cam? 

Hola Damián, lo del Skype tien fácil solución,
En la consola poné:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Con eso me anduvo en mis dos PCs con diferentes camaras, una de ellas una creative.

Si te funca después hay varias formas de que el skype arranque siempre así.
Espero te sirva, saludos.

---

### Post by LisaSimpson on 2009-06-22
y si contaras cómo hacer para que siempre arranque así...
es que me fue de gran ayuda, tengo una genius 111 y no me funcionaba con ubuntu 9.04, hasta el 8.10 había funcionado genial...
y ahora anda todo
pero no sé cómo arrancar sin modo consola
gracias!!!!

---

### Post by anarko on 2009-06-23
Podrias hacer un script en bash que dijese algo como :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Y despues modificar el lanzador del skype para que en vez de lanzar solo skype corra el script que hiciste vos

---

