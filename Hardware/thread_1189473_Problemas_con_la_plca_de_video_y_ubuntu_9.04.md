---
title: "Problemas con la plca de video y ubuntu 9.04"
date: 2009-06-16
forum: Hardware
---

### Post by hugokra on 2009-06-16
Hola a todos :


                  Soy novato con linux y tengo un problema que no puedo resolver, no puedo poner los efectos visuales normales.Por lo tanto les pido una mano para saber que hacer;

Algunos datos de mi placa de video:


[SIZE=3]lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)[/SIZE]

[SIZE=3] xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       85.0* 
   800x600        86.0  
   640x480        86.0  [/SIZE]

Gracias.

---

### Post by guillermolisi on 2009-06-17
> **hugokra said:**
> Hola a todos :


                  Soy novato con linux y tengo un problema que no puedo resolver, no puedo poner los efectos visuales normales.Por lo tanto les pido una mano para saber que hacer;

Algunos datos de mi placa de video:


[SIZE=3]lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)[/SIZE]

[SIZE=3] xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       85.0* 
   800x600        86.0  
   640x480        86.0  [/SIZE]

Gracias.
En una terminal/consola ingresa ```
sudo glxinfo | grep rendering
``` Como dijo Shaun > Si dice, "Yes", estas usando un driver que sabe hablar con el hardware directamente y todo debe funcionar bien.

---

