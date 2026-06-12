---
title: "HP Pavillion tx1000 touch screen drivers?"
date: 2011-02-27
forum: Hardware
---

### Post by x6herbius on 2011-02-27
I am currently trying to get the touch screen on my HP Pavillion tx1000 laptop to work in Ubuntu 10.10 64-bit. I downloaded drivers from EETI (which were recommended by [http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen](http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen)) and manually installed them by editing the xorg.conf file (because I don't trust that installer, it messed things up for me previously). When I log out to restart the X server the PC hangs (but still responds to a press of the power button), and if I reboot Ubuntu just boots into the terminal instead of the desktop. If I restore the xorg.conf from my backup everything works again.

I'm guessing this driver is not compatible with either Ubuntu or the touch screen? I did download the 64-bit version (of which there was only one option). Are there any other touch screen drivers people know of?

Thanks.

---

### Post by x6herbius on 2011-02-28
OK, to update: the situation is that my touch screen currently detects touches without having other drivers installed, but just clicks in the top left hand corner of the screen. Installing the eGalaxTouch X64 drivers (even though my touch screen is listed under *xinput --list* as *eGalax Inc. USB TouchController id=11 [slave pointer (2)]*) works when I can avoid a black screen on startup (something's up with the NVIDIA drivers and I don't know quite what), but the calibration utility reports no touch device found. My X server is Server 1.9.0, X protocol Version 11, Revision 0, xorg-server 2:1.9.0.0ubuntu7 and pixman: 0.18.4, and my kernel is 2.6.35-22-generic.

Any help getting this working would be very much appreciated.

---

