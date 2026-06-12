---
title: "Force use Intel Graphic Card instead dedicated one"
date: 2011-08-31
forum: Hardware
---

### Post by stranieroinpatria on 2011-08-31
Hi all,
I have a laptop with an (unsopported) AMD Radeon HD 6470M.
The OS is ubuntu 11.04 64bit.
The problem is that I can't boot the pc (black screen) with fglrx drivers installed even if I force "nomodeset apci=off" at the boot.
I have unistalled fglrx drivers and with these parameters in the grub i can boot the pc.

So if I install the drivers I can't boot,without I can.

But for switch the graphic card i need the switcheroo option,not available without drivers installed.

So, my question is : how to force the OS to use the Intel graphic card without install any driver??Is there a way??
Please help!!

---

### Post by .... on 2011-08-31
The intel GPU should be the default, but it probably needs kernel modesetting. vgaswitcheroo doesn't work with fglrx. It is meant for open-source drivers.

---

### Post by realzippy on 2011-08-31
Maybe there is a bios update for your machine allowing you to switch graphics.Read about this here in the forum days ago,cannot find the thread now.

---

