---
title: "Help!!! Hardware installation problems."
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by hinesdeal102 on 2008-01-29
I need to know how to blacklist my onboard video so my geforce 5200 fx will load up. Right now It just hangs when I try to boot with the geforce card. My intel onboard graphics are shot so my computer hangs often because of that, this is why I need to get my geforce card working. Ubuntu 7.10 just loads up both video devices during boot and that why it keeps crashing. Somebody please help. I have been trying to resolve this problem for some time now.

---

### Post by oldsoundguy on 2008-01-29
try a disable in the bios at boot up.  I had to do that on an Intel board for video/sound/network. That removes the conflict and you should be able to boot then.

IF IN DOUBT .. go to the Intel site and download the manual for your particular board.

---

### Post by Yellow Pasque on 2008-01-29
If you can boot into recovery mode or get to a terminal by pressing Ctrl+Alt+F1, then you need to straighten out your xorg.conf. First, get your BusID by typing:
```
lspci | grep VGA
```
That'll give you something like:
```
0**x**:0**y**.**z** VGA compatible controller: Nvidia....
```
Commit x,y,z to memory or write it down. Now you can edit your xorg.conf
> sudo nano /etc/X11/xorg.conf
Make sure you have a device section for your nvidia card. Delete the intel one. Also make sure the Device Identifier for your nvidia card matches the device line in the Screen section. For example:
```
Section "Device"
Identifier   "5200FX"
**BusID      "PCI:x:y:z"**
Driver      "nv"
EndSection

Section "Screen"
...
Device  "5200FX"
...
```

That should get you up and running. From there, I imagine you'll want to install the nvidia proprietary drivers.

---

