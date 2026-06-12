---
title: "Syntek webcam worked in Hoary but in Intrepid?"
date: 2008-10-29
forum: Hardware
---

### Post by What_the_deuce on 2008-10-29
Hi

I have an Asus S96S, and enjoyed full hardware support under Hoary, but have lost it under Intrepid . My webcam no longer works. The output of lsusb is:

```
Bus 007 Device 003: ID 174f:6a51 Syntek 2.0MPixel Web Cam - Asus Z96J, Z96S, S96S

```

It doesn't work with skype, aMSN, cheese or Ekiga.

My Internet searching has been in vain, as no one seems to have this model of webcam. 

I can't figure out what is wrong, any help would be greatly appreciated.
Thanks

---

### Post by sgleo87 on 2008-11-02
same problem here....worked fine under Hardy but not in Intrepid. (see my post here [http://ubuntuforums.org/showthread.php?t=966357&highlight=syntek+intrepid](http://ubuntuforums.org/showthread.php?t=966357&highlight=syntek+intrepid))

---

### Post by simpsonsfan74 on 2008-11-02
Same here- webcam worked in Hardy, but not at all in Intrepid.
lsusb | grep Syntek
Bus 003 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S

---

### Post by Mouth on 2008-11-05
[https://bugs.launchpad.net/ubuntu/+bug/278899](https://bugs.launchpad.net/ubuntu/+bug/278899)

... apparently the stk11xx kernel module that supports our camera's doesn't compile with the 2.6.27 kernel (which is in Intrepid).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123)

... a fix is available, as the stk11xx from current (upstream?) source control does compile. We just need someone to bring this into the Ubuntu kernel and we'll have our camera's working correctly !?

If you inflicted by this issue, please make comments/support in the above linked URL's so that the developers see here is support for it and give us a correction :)

---

### Post by sgleo87 on 2008-11-10
Well the driver compiles fine for me and seems to be running but Skype or any other program (Cheese, Camorama) does not recognized the webcam so something must still be wrong....the people in this thread seem to have the webcam working though [http://ubuntuforums.org/showthread.php?t=966357](http://ubuntuforums.org/showthread.php?t=966357)

---

### Post by jtrox23 on 2008-11-22
New S96Sp Dual boot XPsp3  and Ubuntu 8.10. Most worked out of the box. A few things. webcam doesn't work & the speakers are VERY quite. here's lsmod - lsusb

Bus 007 Device 003: ID 174f:6a51 Syntek 2.0MPixel Web Cam - Asus Z96J, Z96S, S96S
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I've been exploring Debian Sarge on a 10yr old CpxJ and finally upgraded to Ubuntu Intrepid on a S96Sp. Wow is all I can say. It was well worth the wait.

back to research

---

### Post by geraldine_ms on 2008-11-23
Hi! I'm starting into Ubuntu world, I'm tired of Windows :mad:

I have the same problem that you guys, I have a Syntek webcam integrated and I can't make it work on Intrepid. But my web cam ID is diferent than yours :confused:

$ lsusb
Bus 004 Device 003: ID 174f:5931 Syntek 

(Sorry if I don't speak very well, my english is not very good)
[B]
Samsung NP-Q310-FS01ES[/B]: Intel Core 2 Duo T5750 2.00 GHz - 4GB DDR2 1GHz - Nvidia GeForce 9200GS 256MB - 250GB 5.400rpm SATA - Intel Wifi Link 5100 - **Ubuntu 8.10 Intrepid Ibex**

---

### Post by davbren on 2009-03-22
I have the same problem. I'm using a Samsung Q310. I want my webcam! :(

---

### Post by Molimo on 2009-03-24
> **davbren said:**
> I have the same problem. I'm using a Samsung Q310. I want my webcam! :(

Hi!
Jast add folowing lines to /etc/modules:
```
#For Syntec camera
options uvcvideo quirks=16

```
then reboot and test camera, for exmaple with mplayer:
```
mplayer tv:// -tv driver=v4l2:width=320:height=240:fps=25:outfmt=rgb24:device=/dev/video0

```
If it doesn't work, download last version [uvc]("http://linux-uvc.berlios.de/#download") driver then make and make install it, and then load it with quirks=16 parameter.

---

### Post by davbren on 2009-03-24
wow that actually worked. The webcam is being detected which is great. It still doesn't work in cheese for some reason...

---

