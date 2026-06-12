---
title: "Hola tengo una duda."
date: 2010-06-28
forum: Hardware
---

### Post by LaMakina on 2010-06-28
Buenas veran soy muy novato en esto de ubuntu e estado investigando pero tengo una inquietud lo que sucede es que al verficar mis controladores de hardware me dice que, no estoy utilizando hardware privativos en mi sistema y la verdad no se si realmente mi tarjeta de video y sonido estan funcionando, al parecer no y tampoco se si este sistema soporta mi hardware dejare los datos para ver si alguien me puede ayudar muchas gracias :).

Tarjeta de video: Ati Radeon xpress 1100
Tarjeta de sonido: Realtek hda 5350
Wifi: Atheros wlan 710116
Lan: Realtek lan 61001106

mi  laptop es una packard bell mx 440 y uso ubuntu 10 - Gnome.

---

### Post by BenjaminChile on 2010-06-28
Hola,

mira cuando me ayudaron a usar el terminal (o la Consola) de Linux, la puedes encontrar en la seccion de Accesorios, haz clic en Terminal. Aparecera una ventana para ingresar texto. Alli escribe lo sgte.: (no temas no le pasara nada a tu equipo)

ben@ben-laptop:~$lspci (y oprime  enter)

en tu equipo aparecera tu nombre de usuario y de equipo que inscribiste al instalar ubuntu.
Bueno aparecera una lista larga a revisar de todas las tarjetas pci conectadas al sistema operativo y sus respectivos controladores asignado en linux. Algo asi como en la mia, mira:
ben@ben-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:02.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0a:02.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0a:02.2 FLASH memory: ENE Technology Inc Memory Stick Card Reader Controller
0a:02.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0a:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
ben@ben-laptop:~$ 


Espero esto te sirva para partir aprendiendo a usar el terminal de linux.
]

---

### Post by asterix77 on 2010-06-29
Como lo detalla Benjamin un lspci en la terminal te arroja bastante información, ahora si quieres depurar la info de tu tarjeta de video debes escribir en la terminal lo siguiente:

#lspci | grep VGA

Lo anterior te detalla el controlador de tu tarjeta de video, si quieres ver si está funcionando escribes

#glxinfo | grep render

Si aparece lo siguiente: "direct rendering: Yes", es que tu tarjeta está con aceleración gráfica (ok).

Puedes chequear el funcionamiento de la misma con lo siguiente:

#glxgears

Aparecerán unos engranajes, primero en una ventana reducida, y luego puedes maximizar la pantalla para ver como te funciona. Tienes que observar dos cosas, primero si hay o no parpadeo de los engranajes; y segundo ver los valores de frames por segundo que te arrojan los engranajes, tanto en pantalla pequeña, como en pantalla completa.

Con respecto al sonido, bueno sería explicar porqué crees que tienes problemas (no se oye música, se oye entrecortado, etc.)

PD: Sería bueno eso sí, si es que tienes diferentes problemas, que abras un nuevo post para cada uno de ellos (por las normas del foro).


Saludos

---

### Post by LaMakina on 2010-06-30
Muchas gracias por la ayuda ... no habia tenido tiempo para responder se agradece, probare sus aclaraciones y cualquier inconveniente avisare gracias de nuevo :).

---

