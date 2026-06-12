---
title: "Windows dual boot question"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by inverseroom on 2009-05-12
I've been using Hardy for about a year on an old laptop, and have a new one on the way (HP dv3) on which I'll be installing Jaunty.  I'm tempted to dual boot this time, though, so that I can still play a few Windows games I like, and use Netflix Watch Instantly.

I can't seem to find this out with goggle, but is it possible to configure the boot so that the computer will boot Ubuntu by default, and will only boot Windows if a particular key is held down during booting?  If I have to respond to a menu every time I turn the computer on, I probably won't bother.

Thank you!

---

### Post by brentrubeck on 2009-05-12
Here's a tutorial for dual booting (since you said new computer I figured you'd want a vista to linux + vista tutorial):  

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Linux will install the grub boot loader (a menu) and it should have an option for booting into windows, but it will boot into one system or the other based on the order they are listed in a file called the menu.lst (under /boot/grub I believe).  In that file you can also change the amount of time in seconds it waits on the grub screen before kicking into the first OS on the menu.  The grub menu will look something like this:

[http://dl.maximumpc.com/galleries/linuxguide2/dual_boot_fedora_sm.png](http://dl.maximumpc.com/galleries/linuxguide2/dual_boot_fedora_sm.png)

---

### Post by inverseroom on 2009-05-12
Excellent--thank you!

---

### Post by acmariner99 on 2009-05-12
That is the exact setup I have on my laptop. I used Ubuntu's partitioner to set up the hard drive the way I wanted, installed Ubuntu, then installed Windows to the unused partition. It is a little trickier to load Ubuntu first because when windows installs, it becomes the default OS, so you need to reconfigure GRUB and add windows as a boot option. (not sure where to get that information.) Then Ubuntu becomes the default and windows will only boot if you access GRUB's manual boot menu and select it there.

---

