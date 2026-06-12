---
title: "Acer Travelmate 5520 problem"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by yemu on 2007-08-08
hi,
i tried installing ubuntu feisty (both 32 and 64 bit) and installer fails just after the first screen, after choosing Start or Install Ubuntu. It shows info like "Kernel panic" and reports some info about acpi problem (I can't remember the exact message because I don't have the notebook right now with me)
does anyone has any idea is it possible to install Ubuntu on this laptop?
thanks for any help
yemu

---

### Post by koshari on 2007-08-08
could you try booting with the no acpi option?

---

### Post by yemu on 2007-08-08
i don't know haven't tried it
how can I do it?

---

### Post by yemu on 2007-08-09
i managed to boot with acpi off, and install using alternate cd, but unfortunately it seems that travelmate 5520 is really not supported in linux :-( 

wired networking doesn't work - it uses marvell chipset which is not yet supported by sky2 module (it's 88e8071 i think)

display doesn't work either - i i don't know if it's supported by vesa, i think it should work with proprietary ati driver, but as my network connetcion doesn't work i can't install this driver :-(

wireless may work with bcm43xx driver but there's no firmware available, so it doesn't and again since i don't have working internet connection, i can't install

ahh, and of course acpi doesn't work, but that's obvious

but, i was able to get some sound of this laptop, don't know anything about microphone,camera and other things like card reader or modem

i can say that i've also tried opensuse 10.2, but the install cd hangs at the beginning, even with acpi off...it seems that ubuntu is better ;-) 

so unfortunately this notebook for now will be using vista :-(

y

ps. do you think it's worth trying if gutsy will work better?

---

### Post by flodins on 2007-08-17
I've also TravellMate 5520  Feisty 7.04 and this what i do:

-Wireless 

Installed with ndiswrapper from windows drivers. (GUI for ndiswrapper is ndisgtk) 

-LAN

Drivers from Marvell.com 

-Display x1250 
Vesa not support, Use vga if you want but everything will by in 320x280 (BIG)
When you've LAN or WLAN this is no problem. 

I dont know how to even check the Crystal Eye camera. Maybe someone help?

SD/xD etc. controller is working
Sound is working but in alsa I've only "General"(i gues, becouse I have polish language) and "PCM"

ACPI not work with Feisty 2.6.20-16 (cpu freq scaling, battery monitor, etc.)

In Gutsy  2.6.22 Ubuntu started without  option "acpi=off" but Gutsy is for now REALY unstable.

I saw somewhere "howto" install 2.6.22 in Feisty but I losted link.

P.S. Sorry for my english (:

---

### Post by Sophisto on 2007-09-01
Yemu! How did you manage to boot with the acpi off? (im struggling)

Many thanks

---

### Post by aropupu on 2007-09-07
Sorry to bump this up, I'm having trouble with installing drivers downloaded from Marvell.com

I followed the readme until I was supposed to
   ./install.sh
which didn't work at all. All I got was
   .install.sh: 72: Syntax error: "(" unexpected

Yes, I'm new with Ubuntu. I hope that I will soon get rid of MS

---
5520G
X2 TL-58
Marvell 88e8071
Ubuntu Feisty

---

### Post by Sophisto on 2007-09-09
Hello Arupupu!

I would recomend installing the wlan drivers first in order to get internet access. Then everything else gets much easier. Ive been working with my travelmate 5520 over the weekend and everything works perfectly now (apart from acpi). Even Compiz works brilliantly which is really cool. I used this guide for the wlan [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and I used this link for the windows drivers [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en) and its the bcmwl5.sys and bcmwl5.inf you want.

Let me know if you have any more problems!

---

### Post by flodins on 2007-09-11
> **aropupu said:**
> Sorry to bump this up, I'm having trouble with installing drivers downloaded from Marvell.com

I followed the readme until I was supposed to
   ./install.sh
which didn't work at all. All I got was
   .install.sh: 72: Syntax error: "(" unexpected

Yes, I'm new with Ubuntu. I hope that I will soon get rid of MS

---
5520G
X2 TL-58
Marvell 88e8071
Ubuntu Feisty

open in gedit/kedit file install.sh and change #!/bin/sh to #!/bin/bash

---

### Post by Sophisto on 2007-09-11
Flodins, did you have to recompile the kernel to get the drivers to work or did you just install it and load the module?

---

### Post by flodins on 2007-09-11
> **Sophisto said:**
> Flodins, did you have to recompile the kernel to get the drivers to work or did you just install it and load the module?

before kernel module compiled but now I can't compile it, im now downloading kernel 2.6.23-rc6 this kernel have support for Marvell 88e8071in module sky2 before it was buggy I will complie this testing kernel check it

---

### Post by stingwray on 2007-09-15
Hi, i've alway got the Acer Travelmate 5520 and having similar sorts of problems.

Turning ACPI off and installing using the alternative cd using the text install works fine.

Problem is I can't find the settings for xorg.conf to enable me to start the x server, so can anyone point me in the right direction.

Many Thanks,

Stingwray

---

### Post by Sophisto on 2007-09-18
If you get your internet working you can download the ATI-drivers and then you screen should work without any alternations to your xorg.conf.

---

### Post by stingwray on 2007-09-19
Thanks, so i'm guessing that has to be done through the command line, i think I'll wait until the weekend to try again when i have a bit more time.

---

### Post by Sophisto on 2007-09-23
yes through the command line. Its very easy though. just follow the ubuntu wiki guide for ATI. I think I posted the link in one of my previous posts.

---

### Post by steqve on 2007-10-12
Two questions:

1.

i tried to install the ndiswrapper today (using gutsy RC1, x64) and installation seems to finish ok. But no driver is recognized. 

ndiswrapper -l 

will give me: bcmwl5: driver installed

Nothing more. Any ideas?

2. The marvell driver installation failes due to lack of "modpost" script. How do i get this script from my clean installation? 

Also, the program "arch" seems to be missing, but the script will run on and sets the platform to i386.

I cannot find arch on the CD. Can I get it at packages.ubuntu.com? In that case - where?

---

### Post by flodins on 2007-10-27
1.you must compile ndiswrapper from source by your self and then install windows driver

2. in kernel 2.6.23 is full supported module sky2 and this is best driver for marvell, don't use sk98lin from marvell site, it seem to sky2 is in 2.6.22-14 (current gutsy kernel)

anyone know when module bcm43xx will be supported?

---

### Post by flodins on 2007-11-01
(: !

NDISWRAPPER IS NO NEEDED ANYMORE

use bcm43xx driver!

I'll write u in couple of days some HowTo for all devices in Travell Mate 5520 (:

---

### Post by Ian Soutar on 2007-12-04
I had good luck with the following way of getting the commercial driver to work.

1/ I booted the live CD and installed the wifi restricted driver on the live Ubuntu 7.10 CD.  
2/ Then I installed to the hard drive.
3/ The wifi worked right away.

As a note ... there is a real bug on the live CD install.   If you fail to install the restricted driver right on the live CD state the installation fails and gets stuck in a loop at the first boot time.   It says it is looking for the WIFI BCMxxx driver.

Another bug appeared when I later installed the restricted ATI driver for my ATI based Acer Travelmate 5520 (5520-5762).   Before installing the commercial ATI driver both sleep and suspend worked.   Afterwards they failed.   

Finally the sound driver does not support the built in microphone.   

But at least the computer is useable.

Ian

---

### Post by Statuesque on 2007-12-10
Hi! I also have a TravelMate 5520 and I installed the windows WLAN driver with ndiswrapper but the wifi don't work. I can view the wireless networks in my range but I can't connect.

The driver of the graphic card is the restrictive driver of ATI, with this it rules!

The Crystal Eye webcam I can't getting it to work.

If someone can help me.. thanks!

---

### Post by flodins on 2007-12-10
Hi,

[COLOR="Red"]**Before you do anything read whole this post carefully.**[/COLOR]

[CENTER][SIZE="6"]**ACPI** (Battery, Temperature,CPU freq scalling etc.)[/SIZE][/CENTER]

Acer programmers are #$%^
I fixed the DSDT table for TravelMate 5520. Lets go:

First you need latest kernel.

Do 1,2,3,4,5 steps form [http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

Download and apply patch for kernel.
```
sudo su
cd /usr/src/linux/
wget http://gaugusch.at/acpi-dsdt-initrd-patches/acpi-dsdt-initrd-v0.8.4-2.6.21.patch
patch -p1 <acpi-dsdt-initrd-v0.8.4-2.6.21.patch
```

Now you can use mine config for kernel or configure it by yourself.

```
sudo su
cd /usr/src/linux
rm .config
wget http://flodins.info/kernel/.config

```

Then do 10 and 11 steps form [http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

Download fixed DSDT
```
sudo su
cd /
wget http://flodins.info/kernel/DSDT.aml
```

Reboot your laptop

And now you have full ACPI 



[CENTER][SIZE="6"]**WIFI**[/SIZE][/CENTER]

Gues what (: bcm43xx is now DEPRECATED

Use b43 driver. You need for this 2.6.23 kernel. My config contains setings for wifi.


then download and compile latest [compat-wireless-2.6.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")

```
sudo su
cd /usr/src/
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xvjf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
make
make install
```

Extract firmware
```
sudo su
apt-get install b43-fwcutter
cd /lib/firmware
wget http://flodins.info/kernel/wl_apsta.o
b43-fwcutter -w /lib/firmware wl_apsta.o
```

Blacklist bcm43xx (Just in case)

```
sudo nano  /etc/modprobe.d/blacklist
```

Add on the end of file
```
blacklist bcm43xx
```

Reboot your laptop.

Now b43 driver is included in 2.6.24 and I'm working on config for this kernel. When 2.6.24 will be stable release I'll write shorter howto. 

If not work post your dmesg and lsmod.


[CENTER]**[SIZE="6"]CrystalEye Webcam[/SIZE]**[/CENTER]

Web cam is working but many software dont set yuv format.

For test camera download luvcview 

```

wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar -xvf luvcview-20070512.tar.gz
cd luvcview-20070512
make 
./luvcview -f yuv

```

If not work load uvcvideo module
```
sudo su
modprobe uvcvideo
```


Mic is working but very quiet(external mic work almost good), in 2.6.24(alsa 1.15) is an option for boost mic

I'm not ussing modem and ieee1394 so I not test these devices.

---

### Post by Statuesque on 2007-12-11
Thank you flodins! In what repositorie is the b43-fwcutter packet? Thank you!

---

### Post by flodins on 2007-12-11
Sory, I tried write everything in Ubuntu way but I'm using Gentoo so can't remember everything.
You can compile b43-fwcutter from sources:
```

sudo su
cd /usr/src/
wget http://download.berlios.de/bcm43xx/b43-fwcutter-008.tar.bz2
tar -xvjf b43-fwcutter-008.tar.bz2
cd b43-fwcutter-008
make 
make install

```

And now you have b43-fwcutter in system.


Any body have tested my DSDT? There are some things to fix so I need some tests.

---

### Post by Statuesque on 2007-12-11
I'm upgraded the kernel to the actual version 2.6.23. And I followed step by step (installing with your other how-to the b43-fwcutter packet) your wifi how-to but the wifi don't work. It doesn't recognize the wifi card.

With the Crystal Eye manual I have a little problem in the make instruction (fourth line). I paste you the errors:
```

statuesque@statuesque-portatil:~/luvcview-20070512$ make
make: sdl-config: No se encontró el programa
make: sdl-config: No se encontró el programa
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.2.1\" -I  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.2.1\" -I   -c -o luvcview.o luvcview.c
luvcview.c:32:21: error: SDL/SDL.h: No existe el fichero ó directorio
luvcview.c:33:28: error: SDL/SDL_thread.h: No existe el fichero ó directorio
luvcview.c:34:27: error: SDL/SDL_audio.h: No existe el fichero ó directorio
luvcview.c:35:27: error: SDL/SDL_timer.h: No existe el fichero ó directorio
luvcview.c:44:22: error: X11/Xlib.h: No existe el fichero ó directorio
luvcview.c:45:27: error: SDL/SDL_syswm.h: No existe el fichero ó directorio
luvcview.c:109: error: expected specifier-qualifier-list before &#8216;SDLKey&#8217;
luvcview.c:114: error: &#8216;SDLK_n&#8217; no se declaró aquí (no en una función)
luvcview.c:114: aviso: exceso de elementos en el inicializador de struct
luvcview.c:114: aviso: (cerca de la inicialización de &#8216;keyaction[0]&#8217;)
luvcview.c:114: aviso: exceso de elementos en el inicializador de struct
luvcview.c:114: aviso: (cerca de la inicialización de &#8216;keyaction[0]&#8217;)
luvcview.c:115: error: &#8216;SDLK_b&#8217; no se declaró aquí (no en una función)
luvcview.c:115: aviso: exceso de elementos en el inicializador de struct
luvcview.c:115: aviso: (cerca de la inicialización de &#8216;keyaction[1]&#8217;)
luvcview.c:115: aviso: exceso de elementos en el inicializador de struct
luvcview.c:115: aviso: (cerca de la inicialización de &#8216;keyaction[1]&#8217;)
luvcview.c:116: error: &#8216;SDLK_x&#8217; no se declaró aquí (no en una función)
luvcview.c:116: aviso: exceso de elementos en el inicializador de struct
luvcview.c:116: aviso: (cerca de la inicialización de &#8216;keyaction[2]&#8217;)
luvcview.c:116: aviso: exceso de elementos en el inicializador de struct
luvcview.c:116: aviso: (cerca de la inicialización de &#8216;keyaction[2]&#8217;)
luvcview.c:117: error: &#8216;SDLK_w&#8217; no se declaró aquí (no en una función)
luvcview.c:117: aviso: exceso de elementos en el inicializador de struct
luvcview.c:117: aviso: (cerca de la inicialización de &#8216;keyaction[3]&#8217;)
luvcview.c:117: aviso: exceso de elementos en el inicializador de struct
luvcview.c:117: aviso: (cerca de la inicialización de &#8216;keyaction[3]&#8217;)
luvcview.c:118: error: &#8216;SDLK_c&#8217; no se declaró aquí (no en una función)
luvcview.c:118: aviso: exceso de elementos en el inicializador de struct
luvcview.c:118: aviso: (cerca de la inicialización de &#8216;keyaction[4]&#8217;)
luvcview.c:118: aviso: exceso de elementos en el inicializador de struct
luvcview.c:118: aviso: (cerca de la inicialización de &#8216;keyaction[4]&#8217;)
luvcview.c:119: error: &#8216;SDLK_v&#8217; no se declaró aquí (no en una función)
luvcview.c:119: aviso: exceso de elementos en el inicializador de struct
luvcview.c:119: aviso: (cerca de la inicialización de &#8216;keyaction[5]&#8217;)
luvcview.c:119: aviso: exceso de elementos en el inicializador de struct
luvcview.c:119: aviso: (cerca de la inicialización de &#8216;keyaction[5]&#8217;)
luvcview.c:120: error: &#8216;SDLK_z&#8217; no se declaró aquí (no en una función)
luvcview.c:120: aviso: exceso de elementos en el inicializador de struct
luvcview.c:120: aviso: (cerca de la inicialización de &#8216;keyaction[6]&#8217;)
luvcview.c:120: aviso: exceso de elementos en el inicializador de struct
luvcview.c:120: aviso: (cerca de la inicialización de &#8216;keyaction[6]&#8217;)
luvcview.c:121: error: &#8216;SDLK_a&#8217; no se declaró aquí (no en una función)
luvcview.c:121: aviso: exceso de elementos en el inicializador de struct
luvcview.c:121: aviso: (cerca de la inicialización de &#8216;keyaction[7]&#8217;)
luvcview.c:121: aviso: exceso de elementos en el inicializador de struct
luvcview.c:121: aviso: (cerca de la inicialización de &#8216;keyaction[7]&#8217;)
luvcview.c:122: error: &#8216;SDLK_r&#8217; no se declaró aquí (no en una función)
luvcview.c:122: aviso: exceso de elementos en el inicializador de struct
luvcview.c:122: aviso: (cerca de la inicialización de &#8216;keyaction[8]&#8217;)
luvcview.c:122: aviso: exceso de elementos en el inicializador de struct
luvcview.c:122: aviso: (cerca de la inicialización de &#8216;keyaction[8]&#8217;)
luvcview.c:123: error: &#8216;SDLK_e&#8217; no se declaró aquí (no en una función)
luvcview.c:123: aviso: exceso de elementos en el inicializador de struct
luvcview.c:123: aviso: (cerca de la inicialización de &#8216;keyaction[9]&#8217;)
luvcview.c:123: aviso: exceso de elementos en el inicializador de struct
luvcview.c:123: aviso: (cerca de la inicialización de &#8216;keyaction[9]&#8217;)
luvcview.c:124: error: &#8216;SDLK_y&#8217; no se declaró aquí (no en una función)
luvcview.c:124: aviso: exceso de elementos en el inicializador de struct
luvcview.c:124: aviso: (cerca de la inicialización de &#8216;keyaction[10]&#8217;)
luvcview.c:124: aviso: exceso de elementos en el inicializador de struct
luvcview.c:124: aviso: (cerca de la inicialización de &#8216;keyaction[10]&#8217;)
luvcview.c:125: error: &#8216;SDLK_t&#8217; no se declaró aquí (no en una función)
luvcview.c:125: aviso: exceso de elementos en el inicializador de struct
luvcview.c:125: aviso: (cerca de la inicialización de &#8216;keyaction[11]&#8217;)
luvcview.c:125: aviso: exceso de elementos en el inicializador de struct
luvcview.c:125: aviso: (cerca de la inicialización de &#8216;keyaction[11]&#8217;)
luvcview.c:126: error: &#8216;SDLK_s&#8217; no se declaró aquí (no en una función)
luvcview.c:126: aviso: exceso de elementos en el inicializador de struct
luvcview.c:126: aviso: (cerca de la inicialización de &#8216;keyaction[12]&#8217;)
luvcview.c:126: aviso: exceso de elementos en el inicializador de struct
luvcview.c:126: aviso: (cerca de la inicialización de &#8216;keyaction[12]&#8217;)
luvcview.c:127: error: &#8216;SDLK_p&#8217; no se declaró aquí (no en una función)
luvcview.c:127: aviso: exceso de elementos en el inicializador de struct
luvcview.c:127: aviso: (cerca de la inicialización de &#8216;keyaction[13]&#8217;)
luvcview.c:127: aviso: exceso de elementos en el inicializador de struct
luvcview.c:127: aviso: (cerca de la inicialización de &#8216;keyaction[13]&#8217;)
luvcview.c:128: error: &#8216;SDLK_f&#8217; no se declaró aquí (no en una función)
luvcview.c:128: aviso: exceso de elementos en el inicializador de struct
luvcview.c:128: aviso: (cerca de la inicialización de &#8216;keyaction[14]&#8217;)
luvcview.c:128: aviso: exceso de elementos en el inicializador de struct
luvcview.c:128: aviso: (cerca de la inicialización de &#8216;keyaction[14]&#8217;)
luvcview.c:129: error: &#8216;SDLK_l&#8217; no se declaró aquí (no en una función)
luvcview.c:129: aviso: exceso de elementos en el inicializador de struct
luvcview.c:129: aviso: (cerca de la inicialización de &#8216;keyaction[15]&#8217;)
luvcview.c:129: aviso: exceso de elementos en el inicializador de struct
luvcview.c:129: aviso: (cerca de la inicialización de &#8216;keyaction[15]&#8217;)
luvcview.c:130: error: &#8216;SDLK_q&#8217; no se declaró aquí (no en una función)
luvcview.c:130: aviso: exceso de elementos en el inicializador de struct
luvcview.c:130: aviso: (cerca de la inicialización de &#8216;keyaction[16]&#8217;)
luvcview.c:130: aviso: exceso de elementos en el inicializador de struct
luvcview.c:130: aviso: (cerca de la inicialización de &#8216;keyaction[16]&#8217;)
luvcview.c:131: error: &#8216;SDLK_m&#8217; no se declaró aquí (no en una función)
luvcview.c:131: aviso: exceso de elementos en el inicializador de struct
luvcview.c:131: aviso: (cerca de la inicialización de &#8216;keyaction[17]&#8217;)
luvcview.c:131: aviso: exceso de elementos en el inicializador de struct
luvcview.c:131: aviso: (cerca de la inicialización de &#8216;keyaction[17]&#8217;)
luvcview.c:132: aviso: exceso de elementos en el inicializador de struct
luvcview.c:132: aviso: (cerca de la inicialización de &#8216;keyaction[18]&#8217;)
luvcview.c:132: aviso: exceso de elementos en el inicializador de struct
luvcview.c:132: aviso: (cerca de la inicialización de &#8216;keyaction[18]&#8217;)
luvcview.c:133: error: &#8216;SDLK_i&#8217; no se declaró aquí (no en una función)
luvcview.c:133: aviso: exceso de elementos en el inicializador de struct
luvcview.c:133: aviso: (cerca de la inicialización de &#8216;keyaction[19]&#8217;)
luvcview.c:133: aviso: exceso de elementos en el inicializador de struct
luvcview.c:133: aviso: (cerca de la inicialización de &#8216;keyaction[19]&#8217;)
luvcview.c:134: error: &#8216;SDLK_j&#8217; no se declaró aquí (no en una función)
luvcview.c:134: aviso: exceso de elementos en el inicializador de struct
luvcview.c:134: aviso: (cerca de la inicialización de &#8216;keyaction[20]&#8217;)
luvcview.c:134: aviso: exceso de elementos en el inicializador de struct
luvcview.c:134: aviso: (cerca de la inicialización de &#8216;keyaction[20]&#8217;)
luvcview.c:135: error: &#8216;SDLK_F1&#8217; no se declaró aquí (no en una función)
luvcview.c:135: aviso: exceso de elementos en el inicializador de struct
luvcview.c:135: aviso: (cerca de la inicialización de &#8216;keyaction[21]&#8217;)
luvcview.c:135: aviso: exceso de elementos en el inicializador de struct
luvcview.c:135: aviso: (cerca de la inicialización de &#8216;keyaction[21]&#8217;)
luvcview.c:136: error: &#8216;SDLK_F2&#8217; no se declaró aquí (no en una función)
luvcview.c:136: aviso: exceso de elementos en el inicializador de struct
luvcview.c:136: aviso: (cerca de la inicialización de &#8216;keyaction[22]&#8217;)
luvcview.c:136: aviso: exceso de elementos en el inicializador de struct
luvcview.c:136: aviso: (cerca de la inicialización de &#8216;keyaction[22]&#8217;)
luvcview.c:186: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
luvcview.c:188: error: expected &#8216;)&#8217; before &#8216;key&#8217;
luvcview.c:191: error: expected specifier-qualifier-list before &#8216;SDL_Surface&#8217;
luvcview.c:200: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;SDL_VIDEO_Flags&#8217;
luvcview.c: En la función &#8216;main&#8217;:
luvcview.c:206: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
luvcview.c:206: error: &#8216;info&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:206: error: (Cada identificador no declarado solamente se reporta una vez
luvcview.c:206: error: ara cada funcion en la que aparece.)
luvcview.c:208: error: &#8216;SDL_Surface&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:208: error: &#8216;pscreen&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:209: error: &#8216;SDL_Overlay&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:209: error: &#8216;overlay&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:210: error: &#8216;SDL_Rect&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:210: error: expected &#8216;;&#8217; before &#8216;drect&#8217;
luvcview.c:211: error: &#8216;SDL_Event&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:211: error: expected &#8216;;&#8217; before &#8216;sdlevent&#8217;
luvcview.c:212: error: &#8216;SDL_Thread&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:212: error: &#8216;mythread&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:213: error: &#8216;SDL_mutex&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:213: error: &#8216;affmutex&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:216: error: &#8216;Uint32&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:216: error: expected &#8216;;&#8217; before &#8216;currtime&#8217;
luvcview.c:217: error: expected &#8216;;&#8217; before &#8216;lasttime&#8217;
luvcview.c:362: error: &#8216;SDL_INIT_VIDEO&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:384: error: &#8216;SDL_VIDEO_Flags&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:384: error: &#8216;SDL_HWSURFACE&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:388: error: &#8216;SDL_ASYNCBLIT&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:414: error: &#8216;SDL_SWSURFACE&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:450: error: &#8216;SDL_YUY2_OVERLAY&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:452: error: &#8216;drect&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:468: error: &#8216;lasttime&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:475: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptscreen&#8217;
luvcview.c:476: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptvideoIn&#8217;
luvcview.c:477: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptsdlevent&#8217;
luvcview.c:477: error: &#8216;sdlevent&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:478: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;drect&#8217;
luvcview.c:480: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;affmutex&#8217;
luvcview.c:484: error: &#8216;currtime&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:520: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;frmrate&#8217;
luvcview.c: En el nivel principal:
luvcview.c:548: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
luvcview.c: En la función &#8216;GUI_whichbutton&#8217;:
luvcview.c:551: error: &#8216;Sint32&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:551: error: expected &#8216;;&#8217; before &#8216;scaleh&#8217;
luvcview.c:552: error: &#8216;scaleh&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:557: error: &#8216;pscreen&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c: En el nivel principal:
luvcview.c:564: error: expected &#8216;)&#8217; before &#8216;key&#8217;
luvcview.c: En la función &#8216;eventThread&#8217;:
luvcview.c:580: error: &#8216;SDL_Surface&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:580: error: &#8216;pscreen&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:580: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptscreen&#8217;
luvcview.c:581: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptvideoIn&#8217;
luvcview.c:582: error: &#8216;SDL_Event&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:582: error: &#8216;sdlevent&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:582: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;ptsdlevent&#8217;
luvcview.c:583: error: &#8216;SDL_Rect&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:583: error: &#8216;drect&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:583: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;drect&#8217;
luvcview.c:584: error: &#8216;SDL_mutex&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:584: error: &#8216;affmutex&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:584: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;affmutex&#8217;
luvcview.c:595: error: &#8216;struct pt_data&#8217; no tiene un miembro llamado &#8216;frmrate&#8217;
luvcview.c:598: error: &#8216;SDL_KEYUP&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:599: error: &#8216;SDL_MOUSEBUTTONUP&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:604: error: &#8216;SDL_MOUSEBUTTONDOWN&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:606: error: &#8216;SDL_MOUSEMOTION&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:608: error: demasiados argumentos para la función &#8216;GUI_whichbutton&#8217;
luvcview.c:610: error: &#8216;SDL_VIDEORESIZE&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:614: error: &#8216;SDL_VIDEO_Flags&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:618: error: &#8216;SDL_KEYDOWN&#8217; no se declaró aquí (primer uso en esta función)
luvcview.c:623: error: &#8216;SDL_QUIT&#8217; no se declaró aquí (primer uso en esta función)
make: *** [luvcview.o] Error 1

```

And I don't test the ACPI how-to.

I will tell you all my experiences. THANK YOU very much for all.

---

### Post by flodins on 2007-12-12
for wifi please post your lsmod and dmesg

for luvcview you need libsdl it should be in repo


why Ubuntu users don't read the README files?

---

### Post by Statuesque on 2007-12-12
Hi flodins!
The Crystal Eye Cam works. In the ACPI how-to I had to download the DSDT.aml file before to compile the kernel, But now it works! Thanks

I've returned to do the Wifi how-to but it doesn't work. I post you my lsmod and dmesg.

dmesg:
```

Linux version 2.6.23.9.131207 (root@statuesque-portaitl) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT Thu Dec 13 03:29:59 CET 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
 BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000006fe80000 (usable)
 BIOS-e820: 000000006fe80000 - 000000006fe93000 (ACPI data)
 BIOS-e820: 000000006fe93000 - 000000006fe95000 (ACPI NVS)
 BIOS-e820: 000000006fe95000 - 0000000080000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
894MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000f8410
Entering add_active_range(0, 0, 458368) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->   229376
  HighMem    229376 ->   458368
Movable zone start PFN for each node
early_node_map[1] active PFN ranges
    0:        0 ->   458368
On node 0 totalpages: 458368
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 1760 pages used for memmap
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 1789 pages used for memmap
  HighMem zone: 227203 pages, LIFO batch:31
  Movable zone: 0 pages used for memmap
DMI present.
ACPI: RSDP 000F83E0, 0024 (r2 PTLTD )
ACPI: XSDT 6FE88CD0, 005C (r1 ACRSYS ACRPRDCT  6040000 INNA        0)
ACPI: FACP 6FE929F1, 00F4 (r3 ATI    Herring   6040000 ATI     F4240)
ACPI: DSDT 6FE88D2C, 9CC5 (r1    ATI    SB600  6040000 MSFT  100000E)
ACPI: FACS 6FE94FC0, 0040
ACPI: SLIC 6FE92B59, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
ACPI: SSDT 6FE92CCF, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
ACPI: ASF! 6FE92ED5, 0063 (r32    DMA AMDTBL    6040000 PTL         1)
ACPI: APIC 6FE92F38, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
ACPI: MCFG 6FE92F8C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
ACPI: HPET 6FE92FC8, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
ATI board detected. Disabling timer routing over 8254.
ACPI: PM-Timer IO Port: 0x8008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:8 APIC version 16
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Processor #1 15:8 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x43538301 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
Built 1 zonelists in Zone order.  Total pages: 454787
Kernel command line: root=/dev/sda1 ro quiet splash
mapped APIC to ffffb000 (fee00000)
mapped IOAPIC to ffffa000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Detected 1895.349 MHz processor.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1806424k/1833472k available (3011k kernel code, 25820k reserved, 1575k data, 244k init, 915968k highmem)
virtual kernel memory layout:
    fixmap  : 0xffe15000 - 0xfffff000   (1960 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc0682000 - 0xc06bf000   ( 244 kB)
      .data : 0xc04f0eb5 - 0xc067abec   (1575 kB)
      .text : 0xc0200000 - 0xc04f0eb5   (3011 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
hpet0: 4 32-bit timers, 14318180 Hz
Calibrating delay using timer specific routine.. 3854.33 BogoMIPS (lpj=1927167)
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 0(2) -> Core 0
CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Early unpacking initramfs... done
ACPI: Core revision 20070126
ACPI: Table DSDT replaced by host OS
ACPI: DSDT 00000000, 8C6E (r1    ATI    SB600  6040000 INTL 20060912)
ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"Parsing all Control Methods:
Table [DSDT](id 0001) - 1085 Objects with 70 Devices 291 Methods 40 Regions
Parsing all Control Methods:
Table [SSDT](id 0002) - 8 Objects with 0 Devices 0 Methods 0 Regions
 tbxface-0598 [00] tb_load_namespace     : ACPI Tables successfully acquired
spurious 8259A interrupt: IRQ7.
evxfevnt-0091 [00] enable                : Transition to ACPI mode successful
CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay using timer specific routine.. 3790.50 BogoMIPS (lpj=1895250)
CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 1(2) -> Core 1
CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
Total of 2 processors activated (7644.83 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A ...  failed.
...trying to set up timer as Virtual Wire IRQ... works.
Brought up 2 CPUs
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using MMCONFIG
PCI: No mmconfig possible on device 00:18
Setting up standard PCI resources
evgpeblk-0956 [00] ev_create_gpe_block   : GPE 00 to 1F [_GPE] 4 regs on int 0x9
evgpeblk-1052 [00] ev_initialize_gpe_bloc: Found 5 Wake, Enabled 2 Runtime GPEs in this block
ACPI: EC: Look up EC in DSDT
ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Completing Region/Field/Buffer/Package initialization:.....................................................................................................
Initialized 35/40 Regions 10/10 Fields 36/37 Buffers 20/35 Packages (1102 nodes)
Initializing Device/Processor/Thermal objects by executing _INI methods:ACPI Error (exregion-0164): Could not map memory at C1F61F2437E94DE4, size 1 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.OSTP] (Node c1f4c5a4), AE_NO_MEMORY
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._INI] (Node c1f516bc), AE_NO_MEMORY
ACPI Exception (nsinit-0564): AE_NO_MEMORY, during \_SB_.PCI0._INI._INI execution [20070126]
.
Executed 1 _INI methods requiring 0 _STA executions (examined 76 objects)
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E5, size 3FF [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.NS38._STA] (Node c1f5839c), AE_NO_MEMORY
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E4, size 400 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.WPC8._STA] (Node c1f58a04), AE_NO_MEMORY
ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Transparent bridge - 0000:00:14.4
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E94F74, size 48 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Exception (dswexec-0462): AE_NO_MEMORY, While resolving operands for [And] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._CRS] (Node c1f51ab8), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0._CRS] (Node c1f51ab8), AE_NO_MEMORY
pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0a08
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E5, size 3FF [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.NS38._STA] (Node c1f5839c), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.NS38._STA] (Node c1f5839c), AE_NO_MEMORY
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E4, size 400 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.WPC8._STA] (Node c1f58a04), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.WPC8._STA] (Node c1f58a04), AE_NO_MEMORY
pnp: PnP ACPI: found 10 devices
ACPI: ACPI bus type pnp unregistered
SCSI subsystem initialized
libata version 2.21 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
Time: hpet clocksource has been installed.
pnp: 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
pnp: 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
pnp: 00:05: ioport range 0x1080-0x1080 has been reserved
pnp: 00:05: ioport range 0x220-0x22f has been reserved
pnp: 00:05: ioport range 0x40b-0x40b has been reserved
pnp: 00:05: iomem range 0xff800000-0xffefffff has been reserved
pnp: 00:06: iomem range 0xe0000-0xfffff could not be reserved
pnp: 00:06: iomem range 0xfff00000-0xffffffff could not be reserved
pnp: 00:06: iomem range 0x0-0x0 could not be reserved
PCI: Bridge: 0000:00:01.0
  IO window: 9000-9fff
  MEM window: f0000000-f01fffff
  PREFETCH window: d0000000-dfffffff
PCI: Bridge: 0000:00:04.0
  IO window: a000-afff
  MEM window: f0200000-f02fffff
  PREFETCH window: 8c000000-8c0fffff
PCI: Bridge: 0000:00:05.0
  IO window: disabled.
  MEM window: f0300000-f03fffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:06.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bus 12, cardbus bridge: 0000:0b:06.0
  IO window: 00002000-000020ff
  IO window: 00002400-000024ff
  PREFETCH window: 88000000-8bffffff
  MEM window: 90000000-93ffffff
PCI: Bridge: 0000:00:14.4
  IO window: 2000-2fff
  MEM window: f0400000-f04fffff
  PREFETCH window: 88000000-8bffffff
PCI: Setting latency timer of device 0000:00:04.0 to 64
PCI: Setting latency timer of device 0000:00:05.0 to 64
PCI: Setting latency timer of device 0000:00:06.0 to 64
ACPI: PCI Interrupt 0000:0b:06.0[A] -> GSI 20 (level, low) -> IRQ 16
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
checking if image is initramfs... it is
Freeing initrd memory: 4880k freed
highmem bounce pool size: 64 pages
Total HugeTLB memory allocated, 0
Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
PCI: MSI quirk detected. MSI deactivated.
Boot video device is 0000:01:05.0
PCI: Setting latency timer of device 0000:00:04.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:04.0:pcie00]
Allocate Port Service[0000:00:04.0:pcie03]
PCI: Setting latency timer of device 0000:00:05.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:05.0:pcie00]
Allocate Port Service[0000:00:05.0:pcie03]
PCI: Setting latency timer of device 0000:00:06.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:06.0:pcie00]
Allocate Port Service[0000:00:06.0:pcie02]
Allocate Port Service[0000:00:06.0:pcie03]
ACPI: AC Adapter [ADP1] (off-line)
ACPI: Battery Slot [BAT0] (battery present)
input: Power Button (FF) as /class/input/input0
ACPI: Power Button (FF) [PWRF]
input: Power Button (CM) as /class/input/input1
ACPI: Power Button (CM) [PWRB]
input: Lid Switch as /class/input/input2
ACPI: Lid Switch [LID0]
input: Sleep Button (CM) as /class/input/input3
ACPI: Sleep Button (CM) [SLPB]
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E5, size 3FF [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.NS38._STA] (Node c1f5839c), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.NS38._STA] (Node c1f5839c), AE_NO_MEMORY
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E5, size 3FF [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.NS38.NFIR._STA] (Node c1f58acc), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.NS38.NFIR._STA] (Node c1f58acc), AE_NO_MEMORY
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E4, size 400 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.WPC8._STA] (Node c1f58a04), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.WPC8._STA] (Node c1f58a04), AE_NO_MEMORY
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E949E4, size 400 [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.WPC8.WFIR._STA] (Node c1f587d4), AE_NO_MEMORY
ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.WPC8.WFIR._STA] (Node c1f587d4), AE_NO_MEMORY
ACPI: Thermal Zone [TZS0] (50 C)
ACPI: Thermal Zone [TZS1] (53 C)
Real Time Clock Driver v1.12ac
hpet_resources: 0xfed00000 is busy
Linux agpgart interface v0.102
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
RAMDISK driver initialized: 16 RAM disks of 4096K size 1024 blocksize
loop: module loaded
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
netconsole: not configured, aborting
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SB600_PATA: IDE controller at PCI slot 0000:00:14.1
ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
SB600_PATA: chipset revision 0
SB600_PATA: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
Probing IDE interface ide0...
hda: Optiarc DVD RW AD-7560A, ATAPI CD/DVD-ROM drive
hda: selected mode 0x42
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
ahci 0000:00:12.0: version 2.3
ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
ata1: SATA max UDMA/133 cmd 0xf8814100 ctl 0x00000000 bmdma 0x00000000 irq 18
ata2: SATA max UDMA/133 cmd 0xf8814180 ctl 0x00000000 bmdma 0x00000000 irq 18
ata3: SATA max UDMA/133 cmd 0xf8814200 ctl 0x00000000 bmdma 0x00000000 irq 18
ata4: SATA max UDMA/133 cmd 0xf8814280 ctl 0x00000000 bmdma 0x00000000 irq 18
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (not used)
ata1.00: configured for UDMA/100
ata2: SATA link down (SStatus 0 SControl 300)
ata3: SATA link down (SStatus 0 SControl 300)
ata4: SATA link down (SStatus 0 SControl 300)
scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
Fusion MPT base driver 3.04.05
Copyright (c) 1999-2007 LSI Logic Corporation
Fusion MPT SPI Host driver 3.04.05
ACPI: PCI Interrupt 0000:0b:06.4[A] -> GSI 20 (level, low) -> IRQ 16
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0402000-f04027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
ieee1394: raw1394: /dev/raw1394 device initialized
ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
ehci_hcd 0000:00:13.5: EHCI Host Controller
ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:13.5: debug port 1
ehci_hcd 0000:00:13.5: irq 19, io mem 0xf0709400
ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 10 ports detected
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:13.0: irq 17, io mem 0xf0704000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 20
ohci_hcd 0000:00:13.1: OHCI Host Controller
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:13.1: irq 20, io mem 0xf0705000
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 21
ohci_hcd 0000:00:13.2: OHCI Host Controller
ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:13.2: irq 21, io mem 0xf0706000
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 1-7: new high speed USB device using ehci_hcd and address 3
ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 20
ohci_hcd 0000:00:13.3: OHCI Host Controller
ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:13.3: irq 20, io mem 0xf0707000
usb 1-7: configuration #1 chosen from 1 choice
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 21
ohci_hcd 0000:00:13.4: OHCI Host Controller
ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
ohci_hcd 0000:00:13.4: irq 21, io mem 0xf0708000
usb usb6: configuration #1 chosen from 1 choice
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
usb 4-2: new low speed USB device using ohci_hcd and address 2
USB Universal Host Controller Interface driver v3.0
usb 4-2: configuration #1 chosen from 1 choice
usbcore: registered new interface driver usblp
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
input: AT Translated Set 2 keyboard as /class/input/input4
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001d72ffff062427]
Advanced Linux Sound Architecture Driver Version 1.0.14 (Fri Jul 20 09:12:58 2007 UTC).
ACPI Error (exregion-0164): Could not map memory at C1F61F2437E94DEA, size 11B [20070126]
ACPI Exception (evregion-0420): AE_NO_MEMORY, Returned by Handler for [SystemMemory] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\PHSR] (Node c1f4c554), AE_NO_MEMORY
ACPI Error (psparse-0537): Method parse/execution failed [\HKEY] (Node c1f4c540), AE_NO_MEMORY
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.AZLA._PS0] (Node c1f58ec8), AE_NO_MEMORY
ACPI: Transitioning device [AZLA] to D0
ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
ALSA device list:
  #0: HDA ATI SB at 0xf0700000 irq 17
oprofile: using NMI interrupt.
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 10
IPv6 over IPv4 tunneling driver
NET: Registered protocol family 17
powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.00.00)
powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
Starting balanced_irq
Using IPI No-Shortcut mode
Freeing unused kernel memory: 244k freed
Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04713/0x204000
input: SynPS/2 Synaptics TouchPad as /class/input/input5
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:02:00.0 to 64
sky2 0000:02:00.0: v1.18 addr 0xf0200000 irq 17 Yukon-Extreme (0xb5) rev 2
sky2 eth0: addr 00:1d:72:06:24:27
input: USB Mouse as /class/input/input6
input: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:13.2-2
usbcore: registered new interface driver usbhid
drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:05:00.0 to 64
ssb: SPROM revision 2 detected.
ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
piix4_smbus 0000:00:14.0: Using Interrupt SMI# for SMBus.
piix4_smbus 0000:00:14.0: SMBREV = 0x0
piix4_smbus 0000:00:14.0: SMBA = 0x8410
i2c-adapter i2c-0: adapter [SMBus PIIX4 adapter at 8410] registered
Yenta: CardBus bridge found at 0000:0b:06.0 [1025:0124]
Yenta O2: res at 0x94/0xD4: 00/ea
Yenta O2: enabling read prefetch/write burst
Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Socket status: 30000006
pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
pcmcia: parent PCI bridge Memory window: 0xf0400000 - 0xf04fffff
pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Adding 5309440k swap on /dev/sda5.  Priority:-1 extents:1 across:5309440k
EXT3 FS on sda1, internal journal
sky2 eth0: enabling interface
ADDRCONF(NETDEV_UP): eth0: link is not ready
sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Bluetooth: Core ver 2.11
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.8
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM ver 1.8
Clocksource tsc unstable (delta = -78900303 ns)
hda-intel: Invalid position buffer, using LPIB read method instead.
eth0: no IPv6 routers present

```

lsmod:
```

Module                  Size  Used by
rfcomm                 33176  2 
l2cap                  21376  11 rfcomm
bluetooth              45348  4 rfcomm,l2cap
yenta_socket           23116  1 
i2c_piix4               9932  0 
ssb                    27972  0 
usbhid                 18212  0 
i2c_core               22336  1 i2c_piix4
k8temp                  5952  0 
hwmon                   4356  1 k8temp
rsrc_nonstatic         10560  1 yenta_socket
pata_atiixp             7232  0 
pcmcia                 24332  1 ssb
pcmcia_core            31064  3 yenta_socket,rsrc_nonstatic,pcmcia
sky2                   40392  0 
```

See you!

---

### Post by flodins on 2007-12-12
post "sudo modprobe b43" , "ls /lib/firmware/"  and dmesg  after modprobe


Have you backlight control from Fn+rarrow/larrow keys ? and  for volume set ?
How about suspend and hibernate?


It seem we have little different laptops mine is 5520-5A1G12 so your DSDT will be little different. tomorrow I'll describe how to extract DSDT from ACPI and then you send me this file

---

### Post by Statuesque on 2007-12-16
My laptop is an Acer TravelMate 5520 402g16mi. I have installed a Linux Mint and I follow the [Mint Wiki instructions]("http://www.linuxmint.com/wiki/index.php/MintWifi") and the wifi works!

But the ACPI don't work :(

---

### Post by flodins on 2007-12-17
Send me result file from command "sudo cat /proc/acpi/dsdt >dsdt"

Mint wifi howto is about ndiswrapper it have not many functions but if you not need anything more it will be ok

---

### Post by tomofhelsinki on 2007-12-26
Trying to install Ubuntu 7.10 from alternative 64-bit version CD to my Acer Travelmate 5520G-402G16Mi. Here are some results:

1. The first installation option from the CD jams when showing "Select and Install software" 85%. I might have corrupted installation CD, since the md5sum check showed that 100dpi fonts are corrupted.

2. So I tried with another option: Install text-based version. That worked. Now I'm continuing with text-based installations and adding ubuntu desktop: sudo apt-get install ubuntu-desktop.

Should I next just follow the instruction in Ubuntu community:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
in order to get (atleast) the graphics work?

---

### Post by tomofhelsinki on 2007-12-26
Now ubuntu-desktop is installed and I start to believe that I might need to recompile the kernel. 

The last steps the installation created /boot/initrd.img-2.6.22-14-generic file and "* Reloading system log daemon..." After that I started to see error messages "bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed." on my command line.

Let's see what happens when I restart computer.

---

### Post by tomofhelsinki on 2007-12-26
After restart the computer the Ubuntu GUI run fine (even with vesa graphics driver!).

The desktop notified that I have restricted drivers available. I opened the dialog and confirmed I want to use "Firmware for Broadcom 43xx chipset family". Then I checked Download from internet "xeve.de/down/wl_apsta.o" and the wireless seemed to work. I have wired connection but I could see neighbours wireless-stations signals.

Now I have tried to use ATI-drivers (fglrx) without success. Ubuntu GUI doesn't start. In command line for startx-command it says: 
"(EE) No devices detected
Fatal server error:
no screens found".
And the same text is found from /var/log/Xorg.o.log file.

How did you get the ATI-driver working? Do you see the resolution of 1200x800? With vesa-driver I can  get 1024x768 at best.

---

### Post by flodins on 2007-12-28
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by tomofhelsinki on 2007-12-30
Hello again,

I followed the instructions (method 2) and survived to install fglrx. For those who have problems, I would recommend to use envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)).

I have still a couple of problems left. First is the most annoying. When I try to use any application using 3D graphics, like previewing 3D screensavers, my graphics crashes and restarts X-server. Could this be somekind of memory problem? The graphics driver si ATI Mobility Radeon HD 2400 XT with 256 MB of RAM (it should automatically use the system RAM for more if needed).

Here are the results of fglrxinfo:
 
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2400 XT
OpenGL version string: 2.1.7170 Release

---

### Post by tseliot on 2007-12-31
what's the output of this command?
```
glxinfo
```

---

### Post by tomofhelsinki on 2007-12-31
```
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by tomofhelsinki on 2007-12-31
I add also my xorg.conf file here. As you can notice I have tried several options starting from the simplest one using only fglrx,"VideoOverlay" = "on" and "OpenGLOverlay"="off".

In addition trying the glxgears crashes the X server.

xorg.conf: ```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
   Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
   Option       "no_accel" "no"
   Option       "no_dri" "no"
   Option       "DynamicClocks" "on"
   Option       "mtrr" "on"
   Option       "DesktopSetup" "Single"
   Option       "ScreenOverlap" "0"
   Option       "Capabilities" "0x00000000"
   Option       "CapabilitiesEx" "0x00000000"
   Option       "CenterMode" "off"
   Option       "PseudoColorVisuals" "off"
   Option       "Stereo" "off"
   Option       "StereoSyncEnable" "1"
   Option       "FSAAEnable" "no"
   Option       "FSAAScale" "1"
   Option       "FSAADisableGamma" "no"
   Option       "FSAACustomizeMSPos" "no"
   Option       "FSAAMSPosX0" "0.000000"
   Option       "FSAAMSPosY0" "0.000000"
   Option       "FSAAMSPosX1" "0.000000"
   Option       "FSAAMSPosY1" "0.000000"
   Option       "FSAAMSPosX2" "0.000000"
   Option       "FSAAMSPosY2" "0.000000"
   Option       "FSAAMSPosX3" "0.000000"
   Option       "FSAAMSPosY3" "0.000000"
   Option       "FSAAMSPosX4" "0.000000"
   Option       "FSAAMSPosY4" "0.000000"
   Option       "FSAAMSPosX5" "0.000000"
   Option       "FSAAMSPosY5" "0.000000"
   Option       "UseFastTLS" "0"
   Option       "BlockSignalsOnLock" "on"
   Option       "UseInternalAGPGART" "no"
   Option       "ForceGenericCPU" "no"
   Option       "KernelModuleParm" "agplock=0"
   Option       "PowerState" "1"
   BusID       "PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Device"
	Identifier	"ATI RADEON X600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"		"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by tomofhelsinki on 2008-01-01
One more note: even when using vesa-driver, the x-window restarts after screensaving (?!). However glxgears and other 3D applications works fine with vesa.

---

### Post by flodins on 2008-01-03
3d in vesa?! miracle (:

---

