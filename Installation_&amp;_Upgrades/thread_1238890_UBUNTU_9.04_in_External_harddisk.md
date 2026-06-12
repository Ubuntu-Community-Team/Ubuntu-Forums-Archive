---
title: "UBUNTU 9.04 in External harddisk"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by codingfreak on 2009-08-12
Hi

I do have some doubts regarding installation of UBUNTU on a external harddisk so that I can carry and plug into a machine and boot from the USB based external harddisk and use my OS.

**NOTE:** I am planning to use UBUNTU 9.04 version for this whole experiment. So please answer to my doubts accordingly considering UBUNTU 9.04.

[LIST]
[*]If I install UBUNTU in external harddisk on a machine with PENTIUM processor then will there be any problems if I plug it to a machine with AMD64 processor (or any other architecture) and try to use UBUNTU in external harddisk ?
[/LIST]

[LIST]
[*]Even regarding graphic cards .... if I keep on using on machines with different varieties of graphic cards will there be any constraints ??
[/LIST]

[LIST]
[*]How stable it is really to use UBUNTU on USB based external harddisk ??
[/LIST]

---

### Post by aysiu on 2009-08-13
It'll work as well as there are native Linux drivers for the hardware of the machine you boot it from.

All the drivers are built into the Linux kernel.

If, however, you have something that requires binary blobs (Broadcom, ATI, Nvidia), then you may have to install those manually to get maximum functionality on the machine you boot the external drive Ubuntu on.

---

### Post by codingfreak on 2009-08-13
Thats sounds intresting and encouraging for me to try out ..........

---

### Post by codingfreak on 2009-08-18
Hi

I have tried out UBUNTU 9.04 on a external harddisk. Installation did not create any problems as I installed on a machine with harddisk connected. The machine is not having any high end graphic cards just a basic INTEL pc.

But when I used the external harddisk on a laptop with graphic cards everything is fine until the next restart of the machine created a GRUB error .... ERROR 17 ..........

Seems using UBUNTU from a external harddisk doesnt sounds encouraging as there chances of corrupting GRUB or filesystems ......

---

