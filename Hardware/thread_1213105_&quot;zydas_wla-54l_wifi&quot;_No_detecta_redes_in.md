---
title: "&quot;zydas wla-54l wifi&quot; No detecta redes inalambricas"
date: 2009-07-14
forum: Hardware
---

### Post by rivastomas on 2009-07-14
Hola 

Tengo un netbook con wifi y Ubuntu detecta este dispositivo como "BCM4312 802.11b/g", el cual funciona sin ningún problema, pero su alcance a la red inalámbrica de mi casa AVECES no es suficiente, así es que compre una tarjeta wifi con puerto usb. La marca es TP-LINK modelo TL-WN422G y Ubuntu la detecta como “ZyDAS WLA-54L WiFi” y el problema que me surge es que no muestra NINGUNA red inalámbrica. Una captura de lo que pasa:

[http://fotosupload.com/mostrar.php?imagen=FuD98467_pantallazo.png](http://fotosupload.com/mostrar.php?imagen=FuD98467_pantallazo.png)

Me pregunto si tengo que lanzar algún comando en consola para que comience a buscar redes, quizá tendré que desactivar el dispositivo wifi interno, no sé, ¿alguna ayuda?

Tengo Ubuntu 9.04 - Jaunty Jackalope, actualizado hasta el día de hoy

---

### Post by Carlos C on 2009-07-15
Con la tarjeta conectada, por favor escribe en el terminal:
```
lsusb
```
y copia acá lo que te salga.
Saludos.

---

### Post by rivastomas on 2009-07-15
rivastomas@u1:~$ lsusb
Bus 001 Device 006: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 003: ID 05c8:0202 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Carlos C on 2009-07-15
puedes encontrar información importante acá:

[http://ubuntuforums.org/showthread.php?t=1110139](http://ubuntuforums.org/showthread.php?t=1110139)

Saludos.

---

