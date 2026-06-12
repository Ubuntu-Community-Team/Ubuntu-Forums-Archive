---
title: "2 graphic cards + 2 screens"
date: 2009-04-22
forum: Hardware
---

### Post by new_tolinux on 2009-04-22
Hello,

According to Ubuntu 8.10 (Intrepid) I have 2 graphic cards:
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:09.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

The ATI is an AGP card and the nVidia is a PCI card.
Both cards have only 1 connector, which is in both cases a 15-pin VGA-connector.

Both work:
If I set the PCI card as primary card in the BIOS it works perfect, using the NV driver automatic.
If I set the AGP card as primary card in the BIOS it works perfect too, using the r128 driver automatic.

I tried a lot of stuff to get them working by editing the /etc/X11/xorg.conf in many ways, but basic the problem is this:
The primary set card (BIOS) is working perfect, but the other card never loads. The screen attached to it remains in standby-mode.

Also tried "Envy", but this only let the working screen remain black after showing the Ubuntu startup-screen, but never load the logon-screen. Did a reinstall after that, so that problem is solved ;)
Also spent the last 3 days around google to find a solution, but nothing worked either.

How to solve this, so I can use the second monitor as a desktop-extension, like in Windows.

---

### Post by new_tolinux on 2009-04-27
:confused: Can someone please help?

---

### Post by new_tolinux on 2009-04-29
Someone advised me to use the alternate installer, so I did a reinstall with the 9.04 alternate cd.
Result:
* Still 2 graphic cards with lspci
* Nvidia works perfect, when selected as primary card in the BIOS
* Ati works perfect, when selected as primary card in the BIOS
* Both cards do absolutely nothing when not selected as primary card in the BIOS.
* System - Preferences - Screen does only show the one active screen.

How can I get the second screen to work at the same time?

---

### Post by new_tolinux on 2010-06-03
Graphic card is replaced by a dual head card.
That means I'm able to use 2 screens and therefore I'll mark this thread solved.

---

