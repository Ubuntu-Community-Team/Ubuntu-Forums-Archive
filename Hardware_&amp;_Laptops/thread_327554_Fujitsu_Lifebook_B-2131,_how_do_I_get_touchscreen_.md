---
title: "Fujitsu Lifebook B-2131, how do I get touchscreen to work?"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by thor918 on 2006-12-29
Hi. I'm trying to get touchscreen to work on Fujitsu Lifebook B-2131, 
and after searching, I found a driver :
[http://www.conan.de/](http://www.conan.de/)

problem is that the lifebook driver patch is for older kernels:
Psmouse-Patch for Kernel 2.6.12-2	psmouse-lifebook-2.6.12-2.diff.gz
Psmouse-Patch for Kernel 2.6.11.7-2	psmouse-lifebook-2.6.11.7-2.diff.gz

and I tryied to install the "Input-Event X driver", but 
in xorg log, I get an error loading modul:
(EE) Failed to load module "evtouch" (loader failed, 7)


I came over some info that the lifebook support should be built in to the kernel now:
[http://www.linuxquestions.org/questions/showthread.php?t=481845&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=481845&referrerid=195877)
currently I'm running kernel 2.6.15-27-686 linux distro drapper, but I can't seem to get the touchscreen working. it does work under win98!
any one got a fix?

---

### Post by thor918 on 2006-12-30
found something else in the error log now:
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
dlopen: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required b$
(EE) Failed to load /usr/lib/xorg/modules/input/evtouch_drv.so

added a ubuntu edge source, since dapper dosen't seem to have 2.4 version.
and apt-get install the glibc

now another new error appear:
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
        compiled for 4.3.99.902, module version = 0.8.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(EE) module ABI minor version (6) is newer than the server's version (5)
(II) UnloadModule: "evtouch"
(II) Unloading /usr/lib/xorg/modules/input/evtouch_drv.so
(EE) Failed to load module "evtouch" (module requirement mismatch, 0)

---

### Post by thor918 on 2006-12-30
just tryed the edgy distro, and the touchscreen was responding without any modifications.
I guess that's how it should be if it is enabled correctly in the kernel.
The problem was the edgy distro was to edgy.
so back on some more stable distros again.

---

### Post by vilee on 2008-01-03
Hi,

I have the same problem. I have also Fujitsu Lifebook B-2131 and I can't get touchscreen to work in Ubuntu Linux. I have tried to search over the internet for help, but I still have the same problem. I have tried with Ubuntu Dapper, Edgy, Feisty and now with the newest Gutsy. I think I have the necessary stuff (new kernel with psmouse module, evtouch driver for x, x configure examples from [www.conan.de](www.conan.de) and other sites etc...) but still cant get it to work.

I'm pretty much in dead end  so can anybody give me some tip / help how I can get touchscreen to work with this laptop? Example touchscreen settings from xorg.conf or something else that can take me forward? Where in /dev/ I can find touchscreen and what is the name of it etc..?

Maybe these can help somebody to help me:

ls /dev/input:

by-path
event0
event1
event2
event3
mice
mouse0
mouse1

cat /proc/bus/input/devices:

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

cat /proc/bus/input/handlers:

N: Number=0 Name=kbd
N: Number=1 Name=mousedev Minor=32
N: Number=2 Name=evdev Minor=64

I'll be very grateful if anybody can help me with this.

---

### Post by thor918 on 2008-01-03
;) I did tourment myself to find a solution and I did infact write down what I did.
My touchscreen have been in service in over a year now ;)

in Norwegian:
> 
installering:
---------------------------------------------------------------
 [http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch.html](http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch.html)
 wget [http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.1.tar.gz](http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.1.tar.gz)
 tar xzvf evtouch-0.8.1.tar.gz
---------------------------------------------------------------
 cp evtouch_drv.so /usr/lib/xorg/modules/drivers/
---------------------------------------------------------------
 pico /etc/X11/xorg.conf
 
 lim inn:
  Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
   EndSection

 og lim inn i section "ServerLayout":
   InputDevice "touchscreen" "CorePointer"
---------------------------------------------------------------
 pico /etc/apt/sources.list
 legg til edgy kilde [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
 (libc6 versjonen 2.4 trenges, og den ligger i edgy kilder)
---------------------------------------------------------------
 apt-get build-dep libc6 
---------------------------------------------------------------
 apt-get install xserver-xorg-video-nv
---------------------------------------------------------------
 ctrl + alt + backspace = restart x

kalibrering:
---------------------------------------------------------------
 [http://www.mp3car.com/vbulletin/showthread.php?p=984566](http://www.mp3car.com/vbulletin/showthread.php?p=984566)
 apt-get install xorg-dev
 wget [http://nextabyte.com/support/touchscreen/calibrator.c](http://nextabyte.com/support/touchscreen/calibrator.c)
---------------------------------------------------------------
 pico calibrator.c

  endre:
	int x_inv = 0, y_inv = 0;
  til:
        int x_inv = 0, y_inv = 1;
---------------------------------------------------------------

 gcc -L/usr/X11R6/lib/ -lX11 -o calibrator calibrator.c
 /root/calibrator /dev/input/event2
 pico /etc/X11/xorg.conf og kopier inn resultatet fra calibrator

problemer:
 undersøk logg  -> pico /var/log/Xorg.0.log


in English:
> 
install:
---------------------------------------------------------------
 [http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch.html](http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch.html)
 wget [http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.1.tar.gz](http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.1.tar.gz)
 tar xzvf evtouch-0.8.1.tar.gz
---------------------------------------------------------------
 cp evtouch_drv.so /usr/lib/xorg/modules/drivers/
---------------------------------------------------------------
 pico /etc/X11/xorg.conf
 
 paste:
  Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
   EndSection

 and in the section "ServerLayout" paste in:
   InputDevice "touchscreen" "CorePointer"
---------------------------------------------------------------
 pico /etc/apt/sources.list
add this apt source (edgy): 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
 (libc6 version 2.4 is needed and it's not in the normal apt source)
---------------------------------------------------------------
 apt-get build-dep libc6 
---------------------------------------------------------------
 apt-get install xserver-xorg-video-nv
---------------------------------------------------------------
 ctrl + alt + backspace = restart x

calibrating the touch screen:
---------------------------------------------------------------
 [http://www.mp3car.com/vbulletin/showthread.php?p=984566](http://www.mp3car.com/vbulletin/showthread.php?p=984566)
 apt-get install xorg-dev
 wget [http://nextabyte.com/support/touchscreen/calibrator.c](http://nextabyte.com/support/touchscreen/calibrator.c)
---------------------------------------------------------------
 pico calibrator.c

  change:
	int x_inv = 0, y_inv = 0;
  to:
        int x_inv = 0, y_inv = 1;
---------------------------------------------------------------

 gcc -L/usr/X11R6/lib/ -lX11 -o calibrator calibrator.c
 /root/calibrator /dev/input/event2
 pico /etc/X11/xorg.conf and copy the result from calibrator

problems:
 check logg  -> pico /var/log/Xorg.0.log


the evtouch driver also seems to be updated. don't know if there any point to update.

I see that calibrator.c url is changed. seems like the code is updated. 
however if you like to follow in my footsteps, here are the code I used:
[http://home.no.net/thor918/calibrator.c](http://home.no.net/thor918/calibrator.c)

And remember to thank me! It was a pain to figure out this stuff.

---

### Post by mircione on 2008-01-04
Hi there.

I have a TabletPC Toshiba portege 3500 and I installed Ubuntu 7.10 today.
You have an idea how can I make to work the touch screen?
Best regards.

---

### Post by vilee on 2008-01-05
Thank you very much for helping me thor918. I really appreciate it. Though I didn't get the touchscreen to work yet but I believe that your instructions will take me forward.

X loads evtouch driver fine and dont complain about it but I have little problem with the calibrator, I stopped to the calibrating step of your instructions because after I run command /root/calibrator /dev/input/event2 it prints: (null): cannot connect to X server

I can modify and compile the calibrator.c just fine but after I run it it complains that cannot connect to X server. I tried to run the command X on and X off killing gdm first but anyway it keeps complaining that cannot connect to X server. Did you have the same problem or do can you give me some help / tip how can I run the calibrator properly?

Which Ubuntu distribution you use? Edgy? (I tried with Edgy just now because I thought that you had it working with Edgy.) And do you have Ubuntu default kernel or custom built kernel? And if custom, can you show/tell me about touchscreen part of your kernel configuration?

When you look at the /proc/bus/input/devices file do you have also this as event2 ?? Or if not, then which device you have pointing to event2?

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

As I said I really appreciate your help with this and I'll be very thankful if you just can help me little more.

---

