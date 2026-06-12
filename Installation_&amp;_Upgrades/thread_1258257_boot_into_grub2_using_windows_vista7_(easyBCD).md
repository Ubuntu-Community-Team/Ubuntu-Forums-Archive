---
title: "boot into grub2 using windows vista/7 (easyBCD)"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by waspinator on 2009-09-04
Hi,

I just installed Karmic Alpha 5 with the boot loader on the '/' partition.

Using EasyBCD in Windows Vista / 7 I was always able to create an entry in the Windows bootloader for Ubuntu when it used GRUB1. Now with GRUB2 it doesn't work. 

I found something in the arch forums but I can't find the file they're talking about (C:/NST/menu.lst)
[http://wiki.archlinux.org/index.php/GRUB2#With_Windows_Vista.2C_via_EasyBCD_and_NeoGRUB](http://wiki.archlinux.org/index.php/GRUB2#With_Windows_Vista.2C_via_EasyBCD_and_NeoGRUB)


Is there a way to manually add a grub2 entry into the Windows bootloader?



Thanks,

Waspinator

---

### Post by dhavalbbhatt on 2009-09-21
> **waspinator said:**
> Hi,

I just installed Karmic Alpha 5 with the boot loader on the '/' partition.

Using EasyBCD in Windows Vista / 7 I was always able to create an entry in the Windows bootloader for Ubuntu when it used GRUB1. Now with GRUB2 it doesn't work. 

I found something in the arch forums but I can't find the file they're talking about (C:/NST/menu.lst)
[http://wiki.archlinux.org/index.php/GRUB2#With_Windows_Vista.2C_via_EasyBCD_and_NeoGRUB](http://wiki.archlinux.org/index.php/GRUB2#With_Windows_Vista.2C_via_EasyBCD_and_NeoGRUB)


Is there a way to manually add a grub2 entry into the Windows bootloader?



Thanks,

Waspinator
You might have to install os prober and then update grub2. Try searching for grub2 in this forum - you should find what you are looking for.

Actually, here is what you are looking for -
[http://ubuntuforums.org/showthread.php?t=1268809&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1268809&highlight=grub2)

DB

---

### Post by oldfred on 2009-09-22
I chainboot into grub2 from grub but had to add grub2 to the partition (not MBR) that had Karmic in it. I did that as part of my install as that was what I knew I wanted to do. There was a WARNING do not do that for some reason but it has worked fine for me. Not sure on instructions to just reinstall Grub2? I would try the Karmic CD.

---

