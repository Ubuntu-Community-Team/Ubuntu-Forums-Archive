---
title: "Problem Ubuntu 5.04 Amd64 freeze"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by Geronimo on 2005-05-10
My system:

Amd Athlon-64 3400+
1 Ghz Ram
Mainboard Gygabite GA-K8NNXP
SATA controller Silicon Image 3512
HD Maxtor DiamondMax 9 200Gb
Video Ati Radeon 9600 Pro

Problem:
I tryed to install two times Ubuntu 5.04 amd-64 but the problem persist, the system completly freeze after a while, without doing something in particular, sometimes in the gdm screen, sometimes after some minutes of work.
Reading some forum and thinking that the problem was the video card I tryed doing those things:

Adding "vmalloc=256m" in the grub, but without success,

adding "acpi=off" in the grub, but the system not start, it freeze at the biginning of the boot process.

adding  Option "KernelModuleParm" "agplock=0;agp_try_unsupported=1"
	Option "AGPMask" "0x00000010"
	Option "AGPv3Mask" "0x00000010"

	in the xorg.conf, but without success,

installing the "xorg-driver-fglrx" as mentioned here [http://www.ubuntulinux.org/wiki/ItalianBinaryDriverHowto](http://www.ubuntulinux.org/wiki/ItalianBinaryDriverHowto), but without success.

The problem still exist, the system random freeze after some second or some minutes of work.
Now I don't know what else can I do, maybe the problem is the SATA controller or something else.

I don't tryed to look the Xorg log but I think there is nothing because the system completly freeze (the mouse, the kayboard... all).

Any suggestion?

Thanks

---

### Post by rjstevens3 on 2005-05-11
does this system run other OSs without problems? sounds like a heat problem, but i had this happen to me from a bad cd. have you tried installing with a new disk?

-RJ

---

### Post by Geronimo on 2005-05-11
The system run Windows Xp without problem. This is the second CD that I downloaded (ISDN :-(), the first had problem. Now I really think that the problem is the video card because if I run Ubuntu in console (the second choice of grub) it run fine. But which problem!!!???
Please help me I really don't wan't to leave Ubuntu.
Thanks

---

