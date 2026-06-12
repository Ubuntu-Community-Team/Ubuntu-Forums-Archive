---
title: "I changed video cards, can I autodetect it?"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by qwert231 on 2005-08-25
Basically that's it. The video card I was using flaked out. Now X won't start, but I get the terminal. xorgconfig is hard to use, is there an easier way? xorgsetup isn't on the system.

---

### Post by tseliot on 2005-08-25
Try: 
sudo dpkg-reconfigure xserver-xorg

and then

sudo nano /etc/X11/xorg.conf

and set "vesa" instead of your previous driver:

You have find the section Device and make sure the word I put in red in the example is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

---

### Post by az on 2005-08-25
Actually, just boot into recovery mode and do 

dpkg-reconfigure xserver-xorg

You do not have to use sudo, because you are already root in recoverymode.



Your xserver is not running, so autodetection should set up your card fine.  You should not need to edit anything.

Type

init 2

when you are done to go into graphical mode.

That's it.

---

### Post by qwert231 on 2005-08-26
[QUOTE=azz]Actually, just boot into recovery mode and do 

dpkg-reconfigure xserver-xorg

You do not have to use sudo, because you are already root in recoverymode.



Your xserver is not running, so autodetection should set up your card fine.  You should not need to edit anything.

Type

init 2

when you are done to go into graphical mode.

That's it.[/QUOTE]
 Just went through dpkg-reconfigure xserver-xorg and then hit startx and all was well in the world. Thanks guys.

---

