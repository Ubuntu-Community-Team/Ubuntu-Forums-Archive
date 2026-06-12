---
title: "Casper grub problems on libretto u100"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by jadzy on 2007-05-01
Hi,

Just installed Ubuntu for the first time on a tiny little Toshiba Libretto U100.

The install was fairly difficult.  The live CD boots fine (i have the official docking station so didn't have the problems others seem to have wth pcmcia or usb cd/dvd drives), but no mouse pointer is displayed.  But i managed to complete the install mouse pointerless.

Note to the Ubuntu install GUI maintainers:  On the partition manager, you can't tab to the 'format' tick box and select it.  You have to use the mouse to select it.  Hard if you have next to no idea where on the screen the pointer is!  Or plain old don't have a mouse.  Also there was what looked like screen corruption along the top of the screen.  Not sure what was supposed to be there.  Don't think anything was missing as the main tool bar was there.  Just with some purple mess above it.

Anyway, the install completed, i rebooted the machine and then hit grub problems.  I get a nice grub error of "GRUB Hard Disk Error".  Seems many others have had this problem but not many seem to have fully understood it and solved it.  The GRUB error is easy enough.  GRUB and the BIOS don't agree on the HD geometry. 

So my first question is, can i tell GRUB what settings to use and work around the problem that way?

If not, several people seem to have solved the issue by giving up on grub and going back to good old lilo.  So, assuming lilo is still in casper somewhere, how do i get it installed?  can i ask for it somewhere at installation time?  if not can i install it having booted from the live/install cd?

any advice on this one gratefully received.
thanks

---

### Post by Syke on 2007-05-01
How big is your hard drive? I didn't have any grub problems on my U100.

When you do get it booting, switch to the VESA driver. It's not perfect, but you can get 1024x768 which is really close to the native LCD resolution, and even better, the mouse works!

---

### Post by jadzy on 2007-05-02
Changed the title now to Feisty, not sure where i got casper from?

Found out a bit more about my screen corruption.  Seems the taskbar from the bottom of the screen isn't being drawn at all.  The screen draw is offset from the top of the screen by about the width of the taskbar.

Seems to work fine in safe graphics mode.

The disk is 60GB.  The laptop is running BIOS 1.20.

---

### Post by jadzy on 2007-05-02
I've now tried Dapper, release 6.06 which also fails with the same GRUB error.

Details are: 

Dapper comes with GRUB 0.97-1
Feisty comes with GRUB 0.97-20

Time to try grub2 or lilo if i can figure out how to get it installed....

---

### Post by jadzy on 2007-05-03
problem solved by installing lilo.


Route i took (from memory) was:

Boot from install CD
mount the root (containing /boot) partition under /mnt
mount proc
configure the wifi interface so Internet access is available
mount --bind /dev /mnt/dev
chroot /mnt
apt-get install lilo
write a lilo config
exit chroot
/mnt/sbin/lilo -r /mnt

think that was all.  reboot, watch lilo boot the kernel and everything is good :)

---

