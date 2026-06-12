---
title: "How2: have all bootable devices listed at boot time ?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-02-24
Hi, I am trying to figure out how Grub sees my USB key so I can change my menu.lst to boot to it by default.

I have tried several ways including going into GRUB command line at boot time. But when I list the available devices by doing a **root (hd<TAB>)** it only lists me my 2 HD. I tried doing a **root (sd<TAB>)** but it fails. I assume it only sees hd* devices.

The reasons I want to do this is :
- I installed Kubuntu 8.10 on my USB key and it works. Yesterday I booted directly to it from an office PC and was able to use it.
- at boot time with a USB key in, when Grub appears, my keyboard and mouse are frozen possibly due to a motherboard bug I have just discovered. After booting time, I can see the content of my USB key if I plug it after. It just won't boot from it.

So if I could see what my Grub sees at boot time, it would help me to figure out what to enter as the default booting O/S to setup the right USB Grub menu.

By the way, I downloaded the latest supergrub Cd version under several forms (*.iso, *.iso.zip, *.iso.gz, *.iso.bz2) but they are all defective.

---

