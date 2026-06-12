---
title: "dual display doesn't work anymore after upgrade from ubuntu 10.4 to 10.10"
date: 2010-09-27
forum: Hardware
---

### Post by jringoot on 2010-09-27
Hi,
On my latitude D620, 
(GPU is: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27A2]vendor: Intel Corporation [8086])
I did the upgrade from ubuntu 10.4 to 10.10 to resolve a problem with ECMWF XCDP (use of right mouse button made GUI hang untill xcdp was killed via console (CTRL+ALT+F1).
Great it works now.
But Now I can't use dual display (I can just see the cursor at the edge of the second screen), well it is to say: extended desktop over 2 monitors. double display(=twice the same screen) does work.
This is what I get with arander
> 
XRandR failed:
XRandR returned error code 1: X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  32
  Current serial number in output stream:  33



I tried several screens and tried also to swap the default screen to the external, problem remains.
I also tried the local vga-port of the laptop and the vga-port on the port replicator and the dvi-port on this port replicator.
Before the upgrade this went all smoothly for 2 screens in different setups... I tried different setups with ubuntu because I tried to get 3 screens to work, but I think that was too much for the video card.
BTW: resolution I tried most is 1440*900(this works for ubuntu 10.4) but lower resolutions give same result.

Any suggestions are welcome.

---

### Post by strombom on 2010-10-07
I have the same issue.

Some more info:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/619663](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/619663)

---

### Post by jringoot on 2010-10-09
Thanks, it is now resolved for me too: 

> **Nick Moeck]  wrote on 2010-09-20: 
This bug is fixed upstream, and the xorg-edgers PPA located at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)  has updated packages with the fix included. I don't know if that fix is going to make it into the official Maverick package, but I hope it does.
[/QUOTE]
[QUOTE=strombom said:**
> I have the same issue.

Some more info:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/619663](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/619663)


BTW: full screen video of flash and right mouse click in xcdp works too now!

---

