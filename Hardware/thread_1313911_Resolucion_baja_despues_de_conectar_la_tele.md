---
title: "Resolucion baja despues de conectar la tele"
date: 2009-11-04
forum: Hardware
---

### Post by Tosh78 on 2009-11-04
Bueno, les cuento que tengo una notebook con Karmic 64, placa de video ATI Radeon 4570 y monitor HD. Venia funcionando todo bien pero la conecte a la tele y se me bajo la resolucion. Con los drivers de ATI Catalyst bajados de la pagina.
El tema es asi, yo venia usando una resolucion de 1600x900, como la tele a la que conecto la compu tiene una resolucion mas baja, siempre tengo que poner la misma que la de la tele (1280x720) en la notebook y clonarlas. Pero esta vez me aparecio un mensaje diciendo que un archivo no estaba creado (fui lo suficientemente tonto como para no fijarme bien el nombre) y dije que si. A partir de ese momento, la resolucion maxima que tengo es 1280x720 en lugar de 1600x900. 
Alguien podria ayudarme para recuperar mi vieja resolucion maxima?

Edito aca y pego mi xorg.conf


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2048 802
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by Tosh78 on 2009-11-05
Bueno, finalmente resolvi esto. La solucion es volver a correr el comando 
aticonfig -f --initial

Gracias Hei Ku por darme la solucion!

---

