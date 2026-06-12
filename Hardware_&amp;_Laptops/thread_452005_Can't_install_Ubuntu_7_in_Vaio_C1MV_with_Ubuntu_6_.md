---
title: "Can't install Ubuntu 7 in Vaio C1MV with Ubuntu 6 ok"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by nas733 on 2007-05-22
Hello.

My attempts to install Ubuntu 7 in my VAIO C1MV (PictureBook) have been unsuccessful so far.  The error is that the kernel can not find the external IDE CD-ROM.  In Ubuntu 6 and with almost any version of kernel 2.6 (for instance with Knoppix) I am able to install by entering these parameters in the kernel command line:

[INDENT]ide1=0x180,0x386[/INDENT]

and some others like pci=conf2, etc., depending on the kernel hardware probes.  In Ubuntu 7.04 however these seem not to work.  The logs after each attempt shows no reference of the ports 0x180 or 0x386 being detected (cat /proc/ioports after failing the boot).  I disabled acpi (acpi=off), tried disabling PNP BIOS in the laptop to force the I/O ports (with several mixed options link pnpbios=off, pci=bios, pci=noacpi, pci=biosirq, etc.) with no success.

My questions are simple:

1.- How may I diagnostic this problem?.  It seems that the Ubuntu kernel is ignoring some of my options or there are new modules that probe the hardware and overrides my settings.

2.- Do anybody knows why the ide1=0x180,0x386 doesn't get probed at all?

3.- The logs tell me that the ide1= option will become obsolete, so I am assuming that there is a change in the kernel that sets this without user intervention.

Please note that the 2.6 kernel of the last Knoppix release boots ok with the parameters above.  So I am trying just to find the difference between the kernels that I should disable in the Ubuntu kernel to get the parameters work with this older laptop.

Any hint will be welcomed!!!


Thanks,


Nas733


p.d. I could try network boot or something else, but I really want to fix the CD-ROM problem to be able to use it from inside Ubuntu once it runs.

---

