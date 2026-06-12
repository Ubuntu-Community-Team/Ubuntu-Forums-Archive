---
title: "No puedo instalar Ubuntu 10.04 en Notebook Dell 710M"
date: 2010-05-05
forum: Instalación y Actualización
---

### Post by Patech on 2010-05-05
Estimados, todo iba bien con la versión 9.10 de Ubuntu. Hasta que intenté instalar en forma limpia la versión 10.04, la cual me fue imposible instalar, ya que después de un rato se me quedaba congelada la pantalla, no dejándome hacer absolutamente nada.
Intenté de todo... descargué la imagen ISO desde este Lunes 3 de Mayo de diferentes servidores (Brasil, Argentina, España, etc), quemándola con diferentes grabadores y sistemas operativos, ayer bajé incluso la imagen ISO de DVD y nada.
Curiosamente se me instaló en otro Notebook con Procesador AMD y mi tarro (PC) con el mismo procesador.
¿Será algún conflicto del Kernel con los procesadores INTEL?

Porfavor necesito que me puedan ayudar y no me digan "Por que note quedas con el 9.04, o quema el Notebook....jajajjaja)

De antemano muchas gracias

_Datos de mi equipo_


-Computer-
Processor        : Intel(R) Pentium(R) M processor 1.70GHz
Memory        : 750MB (301MB used)
Operating System        : Ubuntu 9.10
User Name        : 
Date/Time        : 
-Display-
Resolution        : 1280x800 pixels
OpenGL Renderer        : Mesa DRI Intel(R) 852GM/855GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel 82801DB-ICH4


-PCI Devices-
Host bridge        : Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller 
System peripheral        : Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller 
System peripheral        : Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller 
VGA compatible controller        : Intel Corporation 82852/855GM Integrated Graphics Device 
Display controller        : Intel Corporation 82852/855GM Integrated Graphics Device 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBM 
PCI bridge        : Intel Corporation 82801 Mobile PCI Bridge 
ISA bridge        : Intel Corporation 82801DBM 
IDE interface        : Intel Corporation 82801DBM 
SMBus        : Intel Corporation 82801DB/DBL/DBM 
Multimedia audio controller        : Intel Corporation 82801DB/DBL/DBM 
Modem        : Intel Corporation 82801DB/DBL/DBM 
Network controller        : Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection 
CardBus bridge        : Texas Instruments PCI7420 CardBus Controller
CardBus bridge        : Texas Instruments PCI7420 CardBus Controller
FireWire (IEEE 1394)        : Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller 
Mass storage controller        : Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
Ethernet controller        : Broadcom Corporation BCM4401-B0 100Base-TX

---

### Post by Carlos C on 2010-05-06
Intenta con un método que funcionó para algunos usuarios de Karmic: cuando estés en el menú de inicio, luego de escoger el idioma, presiona F4. De esa manera podrás optar por el "modo gráfico seguro" de arranque. Ve si con eso puedes instalar correctamente.

Saludos.

---

### Post by Patech on 2010-05-06
Grax por la ayuda, pero no me funcionó.
Quizás tenga que esperar hasta que se solucione esto.

---

### Post by Patech on 2010-06-01
Saludos, después del gran Flisol (en mi caso V región : Lugar Duoc). Se logró solucionar el problema que tenía al no poder instalar ubuntu Lucid 10.04.
Lo explicaré a continuación:
 
1) Bajen la imagen ISO el Aternate CD e instalen Ubuntu 10.04 [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
 
Debería instalarse sin ningún problema
 
2) Luego al reiniciar el sistema en la grub (Pantalla donde se selecciona el sistema operativo a ocupar ; si tienes más de un sistema operativo), selecciona el modo a prueba de fallos y ñuego de la carga seleccionar a prueba de fallos para Video
 
3) De ahí en el entorno gráfico (Escritorio) de baja resolución (ya que el problema radica en la resolución por la tarjeta Intel) siguen las siguientes posibles soluciones.... a mi me funcionó la de instalar el nuevo Kernel 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
 
Ojalá que me entiendan
 
Saludos

---

