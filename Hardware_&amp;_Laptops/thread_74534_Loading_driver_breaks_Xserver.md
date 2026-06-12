---
title: "Loading driver breaks Xserver"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by Gene_Pool on 2005-10-12
I have a nPort 1240 which is a USB device that has four serial ports on it. The laptop I'm using it with does not have any plain old serial ports on it and I need to communicate with a mini SSC-II card which only has an RS-232 connection port (Those of you who are already thinking this sounds cludgy, don't worry it gets better.). The driver provided by Moxa the manufacturer of the nPort 1240 list their driver as being compatable with 2.4.x versions of the kernel. To that end I compiled a 2.4.27 kernel and attempted to get the hardware running under it. After a whole mess of twiddling with the driver I hadn't managed to get it to compile so I took a break from the project for a while. This evening while booted into the 2.6.10-5-386 kernel I decided to fiddle with it just a bit more. And lo and behold it compiled(after some tweaking). I ran the install script and then rebooted the system. During the reboot into 2.4.6 X choked. I'm getting the good ol failed to initialize core devices error. after looking at /var/log/Xorg.0.log the X server seems to not be seeing the mouse at boot time while booting into the 2.4.6 kernel. But there are no problems while booting into the 2.4.27 kernel. I have searched through several forums and read most of the information on [http://wiki.X.org](http://wiki.X.org) and am stumped. Thank you in advance for taking the time to read this post and share your insights into this pickle I have wrapped myself up into.
~Gene

---

### Post by Gene_Pool on 2005-10-18
As an update I found a workaround. Namely recompiling a new 2.6 kernel. I figured out that part of the problem with the driver I was loading was that it was written for the 2.4 kernel (I'm not entirely sure how it compiled and loaded into my 2.6 kernel while still having a "#define MODULE" statement in it). I was following the instructions in _Linux Device Drivers_ 2nd Edition from O'Reilly press which is targeted at the 2.4 kernel. I'm still something of a newbie and did not realize that such major changes would have to be incorporated into a driver to make it compatible with the new version of the kernel. I did find a good article here [http://linuxdevices.com/articles/AT4389927951.html](http://linuxdevices.com/articles/AT4389927951.html) Which describes some of the differences between how to write/modify a driver so as to make it work under the 2.6 kernel.

---

