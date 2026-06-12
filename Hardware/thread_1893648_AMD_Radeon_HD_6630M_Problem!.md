---
title: "AMD Radeon HD 6630M Problem!"
date: 2011-12-10
forum: Hardware
---

### Post by m.r.karimi.j on 2011-12-10
Hi there.
I've just bought my new machine, Lenovo thinkpad edge E520 with configuration mentioned at the end. I tried to install Ubuntu 11.10 64bit on it. It seemed to be no problem, but the graphics card driver.

I tried to use "Additional Hardware" which had 
1. ATI/AMD propietary FGLRX graphics (post-release updates)
which resulted INSTALLATION FAILURE! 
2. ATI/AMD propietary FGLRX graphics which did not work and disabled desktop effects.

I Also installed "AMD Catalyst™ 11.11 Proprietary Linux x86 Display Driver". But after installation, unity did not boot :confused:, and I had to remove installed packages from tty1 and then reboot. moreover, after removing, desktop effects did not work :confused:!!!!

Is there a way to fix the problem or configure xorg to work with the switchable graphic cards?

configuration:
Intel core i5, AMD Radeon HD 6630M, Intel HD (integrated)

by the way, there is no vga_switcheroo. & there is the same issue on gnome-shell!

Thanks for your advices guys.:)

---

### Post by framebuffer on 2012-02-19
I am facing the same Problem.

According to the Unofficial AMD wiki wiki.cchtml.com, 6630M Drivers are not yet released for Linux. (Its not opening at the time of this posting)

The wiki also suggests trying your luck to use some other drivers and fool linux into thinking its for 6630M but that didnt work for me either.

I have seen AMD release a new driver for AMD Cards this month or so. haven't tried it. It will be great of someone can confirm that.

Because of this, I am unable to use Ubuntu :frown:

I hope AMD will release the drivers soon.

---

### Post by Alexislavie on 2012-02-23
Check this post : [ http://ubuntuforums.org/showthread.php?p=11712748]("http://ubuntuforums.org/showthread.php?p=11712748")

---

