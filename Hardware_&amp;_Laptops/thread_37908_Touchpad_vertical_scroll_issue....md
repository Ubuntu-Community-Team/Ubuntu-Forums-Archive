---
title: "Touchpad vertical scroll issue..."
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by kumpooterjooser on 2005-05-29
I installed ubuntu on my Toshiba M35-S359 laptop...
things are going pretty well...

Trying to figure out how to get vertical scroll on my synaptics touchpad to 
work...Have googled lot of forums and tried all types of settings, but that 
scroll wont happen (other things like X not starting do happen :-( ... )
Other functionalities of touchpad are working fine...

I have the latest xorg-driver-synaptics on my machine...

Here is a suggestion (and its variants) that I tried...
1. [http://ubuntuforums.org/archive/index.php/t-3993.html](http://ubuntuforums.org/archive/index.php/t-3993.html)

I even configured my xorg.conf as per the file 
/usr/share/doc/xorg-driver-synaptics/README.debian

Nothing seemed to wake the vertical scrollbar...

Finally I checked with 'cat /proc/bus/input/devices' and found that touchpad 
isn't listed as an input device...Could that be an issue... ?

Is it a known issue or am I missing something...
Would highly appreciate help/suggestions...

Thanks

...kumpooterjooser

*************************
here is the console output...
```

# cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 ts0 event1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c00c Version=2110
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
H: Handlers=mouse1 ts1 event3
B: EV=f
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=100 0
```

---

### Post by andlinux21 on 2005-05-29
[FONT=Comic Sans MS][SIZE=3][COLOR=Navy]Is everything else working fine for you?[/COLOR][/SIZE][/FONT]

---

### Post by kumpooterjooser on 2005-05-29
[QUOTE=andlinux21][FONT=Comic Sans MS][SIZE=3][COLOR=Navy]Is everything else working fine for you?[/COLOR][/SIZE][/FONT][/QUOTE]
 Everything else seems to be working fine in my laptop...
The touchpad vertical scroll issue is there since day one, I'm 2 weeks old in my rebirth as 
Linux user :-) ...

Today I tweaked my graphics card setting and landed in another problem...can be seen at 
this thread

[http://ubuntuforums.org/showthread.php?t=37907](http://ubuntuforums.org/showthread.php?t=37907)

These two issues shouldn't be related I guess.

Thanks

...kumpooterjooser

---

### Post by ::DoGG:: on 2005-05-29
Well, touchpad scroll areas are tricky. I got linux on ny laptop from 2 yeasr and didn`t figured i tout, sometimes it`s just won`t work.. But i don`t use that "scroll area" future anyway, so.. :D

---

