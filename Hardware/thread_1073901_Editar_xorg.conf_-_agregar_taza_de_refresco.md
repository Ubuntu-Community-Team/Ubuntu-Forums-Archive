---
title: "Editar xorg.conf - agregar taza de refresco"
date: 2009-02-18
forum: Hardware
---

### Post by sajnox on 2009-02-18
Hola,

He comprado una placa de video

```
miguel@miguel-desktop:~$ lspci | grep video
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
```

Con el driver libre la placa no tiene aceleracion 3D, o por lo menos falle en la configuracion, el tema es que si pude instalar el driver de ATI (9.1 que es la ultima version) Hasta aca todo bien, el tema es que hace un poco de fantasma en la pantalla y creo que es la taza de refresco, el monitor puede ir a 75hz pero solo detecta 60hz.

Entonces la pregunta es: ¿Que debo agregar en el xorg.conf para tener la opcion de la taza de refresco a 75hz?

Dejo mi xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection
```

---

### Post by guillermolisi on 2009-02-18
> **sajnox said:**
> Hola,

He comprado una placa de video

```
miguel@miguel-desktop:~$ lspci | grep video
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
```Con el driver libre la placa no tiene aceleracion 3D, o por lo menos falle en la configuracion, el tema es que si pude instalar el driver de ATI (9.1 que es la ultima version) Hasta aca todo bien, el tema es que hace un poco de fantasma en la pantalla y creo que es la taza de refresco, el monitor puede ir a 75hz pero solo detecta 60hz.

Entonces la pregunta es: ¿Que debo agregar en el xorg.conf para tener la opcion de la taza de refresco a 75hz?

Dejo mi xorg.conf

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection
```
Miguel

No sera tambien problema de frecuencias de horizontal y vertical mas que frecuencia de refresco ?

Te copio una parte de mi /etc/X11/xorg.conf en donde se establecen valores para el monitor que estoy usando en casa con una placa nVidia 6200.```

Section "Monitor"
    Identifier     "Samsung"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 794MB/794MBplus/798MB"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
```Los valores de frecuencias vertical y horizontal para tu monitor deberias obtenerlos del manual del fabricante.

Ojo que si no estan dentro del limite de trabajo podes quemar el aparato.

---

### Post by 1antares1 on 2010-09-11
Hola amigos, disculpen por que el tema es viejo, pero tengo el mismo inconveniente y veo que no se ha encontrado aún la solución.

Quisiera cambiar el refresco de la pantalla, ya que antes de instalar los drivers, estaban en 1440x900 75hz y luego de instalar los privativos, todo bien y perfecto. Pero el unico problema es que no corre a 75hz.

No me da la opción, pués solo aparece 60 hz. ¿Es un problema del Xorg o un bug de los drivers de ATI?

Es una ATI HD 4670 - Drivers 10.8.

Espero que alguien posea alguna informaciòn sobre ésto y me la haga saber. Gracias. ;)

---

### Post by 1antares1 on 2010-09-12
Imágenes de Muestras:

-Entro al Catalyst Control Center y encuentro que en la información de la tarjeta, la máxima frecuencia es 75 Hz:

[IMG]http://i55.tinypic.com/9v9ow7.png[/IMG]


Pero al tratar de cambiarlo, tanto en aquí como en "Monitores", sólo salen 60 Hz, no más de ahí.

Una muestra:

[IMG]http://i53.tinypic.com/2im9rhj.png[/IMG]



Aparte, que mi Xorg, lo veo muy simple, comparado como el de otros. (Es idéntico como el del creador del tema).
[B]
¿Como puedo generar un Xorg automático de ATI?[/B]

**¿Cómo agregar frecuencias al Xorg?**

Esto de verdad me tiene molestoso, espero que puedan ayudarme, estaría agradecido de antemano.

Gracias.

---

