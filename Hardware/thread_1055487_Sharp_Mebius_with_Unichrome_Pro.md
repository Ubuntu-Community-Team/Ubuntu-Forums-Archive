---
title: "Sharp Mebius with Unichrome Pro"
date: 2009-01-30
forum: Hardware
---

### Post by 00b00nt00 on 2009-01-30
I have acquired a Sharp Mebius laptop with the following specs:

AMD Sempron 2600+
1GB DDR RAM
40GB Hard Disk
64MB shared video (adjustable in the BIOS)
VT3108 K8N800 VIA Unichrome Pro video adapter.

So, when I boot from the live CD, the Ubuntu menu and sliding bar appear as usual, however it is replaced by a blank screen. Shortly after, all disc activity stops and the computer appears to 'lock up'.

Any ideas?

---

### Post by Yellow Pasque on 2009-01-30
Have you tried pressing F4 and booting with 'Safe Graphics' Mode?

---

### Post by 00b00nt00 on 2009-01-30
Yes I have tried safe graphics mode. I can get to the desktop, but only at 800*600 not 1024*768.

---

### Post by Yellow Pasque on 2009-01-30
Then it would seem that the VIA video driver on the LiveCD isn't compatible with your GPU. It sounds like this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/182778](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/182778)

What version of Ubuntu are you attempting to use?

---

### Post by 00b00nt00 on 2009-01-30
I'm using Ubuntu Intrepid.

As a side note, could get the laptop to work in OpenSUSE 10.3, but something broke in OpenSUSE 11. I've also tried several other Linux ditros, with pretty much the same result.

Could it be that the latest Unichrome drivers are broken?

---

### Post by Yellow Pasque on 2009-01-30
> Could it be that the latest Unichrome drivers are broken?
It's very possible, given the relatively infant state of the openchrome driver.

From [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)
> For Unichrome Pro laptops the driver automatically activates VBE modes to make the panel work, and you will thus be restricted to the BIOS modes when you are using the panel with these computers. (This may not work in 64-bit mode.)

---

### Post by 00b00nt00 on 2009-01-30
Not good news considering the chipset has been out in the wild for several years now. I'll wait until Jaunty is officially released and report back if there have been any improvements.

Shame, really, because Ubuntu works perfectly on my other (older) laptop.

---

### Post by libv on 2009-10-18
Please contact unichrome-devel at lists dot sf dot net to get this resolved properly. I have esimilar device here and it works fine.

---

