---
title: "No hard drives when installing"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by FourthCoffee on 2009-06-16
Hi,
Im currently trying to install ubuntu 8.04 desktop from a live CD and all has gone well untill i reach the prepare partions page of the setup.
And the problem is that it is not showing up any of my 2 ide hard drives, i have checked in bios and they are both there ready to taste the goodness of linux.
Its probley something simple i missed but if you could point me in the right direction that would be great.

thanks****

---

### Post by dstew on 2009-06-16
I assume the disk is good. Has it been used to install in other computers? The "Check Disk Integrity" test runs OK?

Most likely it is the fault of the Linux kernel in the Live CD, that it has trouble with your hardware, and cannot see the disks. One thought is to modify how the Live CD kernel is configured by using kernel parameters. You enter these at the end of the kernel line, accessed by pressing F6 at the opening menu. The parameter **all_generic_ide** has worked for some. You can also try altering your BIOS settings to tell the disks to behave differently.

You can also try using a different installation disk. The Alternate Install disk uses a text-based interface, but I do not know if it uses a different kernel. Possibly it will work with your hardware.

Any reason you need to install 8.04? Maybe the 9.04 Jaunty Live CD will work better.

---

