---
title: "Laptop doesn't like new Linux versions"
date: 2010-04-27
forum: Hardware
---

### Post by panthermod on 2010-04-27
I have the HP Dx2000MT computer.
I've installed 2 gigs of memory, and it has a 500 gig hard drive now. It comes with built in Intel graphics, but I use my own Nvidia graphics card.
Up until recently, I ran many versions of Linux on this machine.
Now newer versions of linux are cropping up that crash when I try to load them up.
Is there something wrong with the Intel 865 chipset that will not allow newer versions of linux to load? I think it has something to do with onboard graphics. When I use the built in graphics solution, the machine boots just fine. When I use the Nvidia card, it doesn't work at all. Before this, I had a X1300 ATI card, thinking a different graphics card might be the solution...but so far no luck.
I use a dual booting solution...I use Windows XP, and I alternate between Xandros 4.5 and Ubuntu 8.04. Ubuntu 8.10 and higher simply will not boot. Debian 5.0 and newer versions of Mandrake, Fedora and such also will not boot.

Help??

abner@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
01:02.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 22)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
abner@ubuntu:~$ 

abner@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-27-generic #1 SMP Fri Mar 12 01:10:31 UTC 2010 i686 GNU/Linux

is the only kernel that loads.

also have flashed bios to most current !

:confused:

and yes i have cleaned out the dust bunnies :lolflag:

ran memtest all sticks test fine :lolflag:

IN need of some help:confused::guitar::lolflag:

---

### Post by Iowan on 2010-04-27
Moved to new thread.
No need to hijack someone else's when you can have your very own for the same price. :)

---

