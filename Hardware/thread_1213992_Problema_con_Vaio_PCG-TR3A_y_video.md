---
title: "Problema con Vaio PCG-TR3A y video"
date: 2009-07-15
forum: Hardware
---

### Post by crash_master25 on 2009-07-15
[english]
Hi!

I will write in both, english and spanish, then you can answere me in what you want (english or spanish LOL ;) ) I have a problem, my laptop works fine with ubuntu 9.04, but when I want to paly wolfenstein 3D or simply I want to change the video resolution or sometimes when I start the laptop with gnome, the screen turns white with some black spots that fade to white and I can´t see anything. If I connect an external plasma monitor all  see correct, and perfectly fine, this is the result of the lspci: 
[/english]

[spanish]
Hola 

Tengo un problema, mi laptop trabaja muy bien, pero cuando quiero jugar un juego como el wolfstein, o deseo cambiar de resolucion de video o simplemente algunas veces arranca el gnome, como que el video se atonta y se pone blanca la pantalla de plasma, y no se ve nada, si le conecto un monitor externo se ve todo perfectamente  bien... les dejo aqui el resultado del lspci:
[/spanish]


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


I hoppe you can helpme....


Espero me puedan ayudar
Saludos
Bruno Chavez

---

### Post by carml on 2009-07-15
[SIZE="5"]Please write in English[/SIZE]. 
This is the official forum and not a local forum.If you're not fluenty or able to speak in english you can always ask your question on the Spanish (I suppose you're from Spain or similar) ;)

---

### Post by carml on 2009-07-15
For the future I suggest you to write in english in this forum, apart from that I had almost understand what you write even if in spanish and I don't speak spanish (I'm from Italy and spanish derives from latin ;) ).
Your problem seems to be the video driver,can you check what I wrote here [HTML]http://ubuntuforums.org/showthread.php?t=1213800[/HTML] and let us know the result?

---

### Post by crash_master25 on 2009-07-15
> **carml said:**
> For the future I suggest you to write in english in this forum, apart from that I had almost understand what you write even if in spanish and I don't speak spanish (I'm from Italy and spanish derives from latin ;) ).
Your problem seems to be the video driver,can you check what I wrote here [HTML]http://ubuntuforums.org/showthread.php?t=1213800[/HTML] and let us know the result?

Tks, I'm checking the thread... I will only write in english...


Regards
Bruno Chávez

---

### Post by Hei Ku on 2009-07-15
Will you please stop? 
This is the forum for the Argentina LoCo Team. We speak Spanish.

Por favor, hablá en español, porque este es el foro de Argentina.

---

### Post by crash_master25 on 2009-07-15
> **carml said:**
> For the future I suggest you to write in english in this forum, apart from that I had almost understand what you write even if in spanish and I don't speak spanish (I'm from Italy and spanish derives from latin ;) ).
Your problem seems to be the video driver,can you check what I wrote here [HTML]http://ubuntuforums.org/showthread.php?t=1213800[/HTML] and let us know the result?

Hi again

I open the System->Administration->Hardware Drivers and there's nothing... tell "There are no any privative controlers in the system"

I don't know what to do

Regards
Bruno Chávez

---

### Post by crash_master25 on 2009-07-15
> **Hei Ku said:**
> Will you please stop? 
This is the forum for the Argentina LoCo Team. We speak Spanish.

Por favor, hablá en español, porque este es el foro de Argentina.


Hola

Pues ya no se, yo pense que era en español, luegome dijeron que en ingles, total, aunque sea en chino, pero no puedo correr WORFSTEIN 3D en mi lap

---

### Post by Hei Ku on 2009-07-15
No necesitas controladores privativos, porque tenes una Intel.

Posteá el resultado de correr esto en una terminal:

glxinfo | grep rendering

---

### Post by crash_master25 on 2009-07-15
> **Hei Ku said:**
> No necesitas controladores privativos, porque tenes una Intel.

Posteá el resultado de correr esto en una terminal:

glxinfo | grep rendering

get fences failed: -1
param: 6, val: 0
direct rendering: Yes


Saludos
Bruno Chavez

---

### Post by Hei Ku on 2009-07-15
Probaste en otras resoluciones? Me suena a que el juego te esta cambiando la resolucion y no le engancha bien el refresco del monitor.

---

### Post by crash_master25 on 2009-07-16
> **Hei Ku said:**
> Probaste en otras resoluciones? Me suena a que el juego te esta cambiando la resolucion y no le engancha bien el refresco del monitor.

Hola

De hecho me da el mismo problema cuando cambio la resolucion del monitor, en el momento que la modifico la pantalla se pone igual en blanco....

Saludos
Bruno Chave

---

### Post by crash_master25 on 2009-07-16
Hola

He aqui algo que encontre:

al poner: xrandr me dice:

Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1280x768         59.8*+
1024x768         85.0     75.0     70.1     60.0
832x624           74.6
800x600           85.1     72.2      75.0     60.3      56.2
640x480           85.0     72.8      75.0     59.9
720x400           85.0
640x400           85.1
640x350           85.1

Intente cambiar a todas estas resoluciones y sucede lo mismo, la pantalla se vuelve blanca...

Saludos

Bruno

---

