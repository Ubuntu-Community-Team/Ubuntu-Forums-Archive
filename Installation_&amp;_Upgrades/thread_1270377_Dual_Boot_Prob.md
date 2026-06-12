---
title: "Dual Boot Prob"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by robvan on 2009-09-19
have installed ubuntu 9.04 as standalone on a SATA and am running windows XP on another SATA drive. Prob is, i can't choose to boot from either drive without editing the boot sequence from the BIOS. Mobo is ASUS P5KPL. Options available is to boot from only one HDD and/or CD/DVD SATA. Don't have option on my BIOS to choose to boot from both hard drives.All HDD's are SATA, maybe thats the prob? Any help or advice is appreciated.

---

### Post by arrange on 2009-09-19
1 Can BIOS only see ONE SATA drive? You don't have an option to change priorities of booting?
 
2. Is there Grub installed on the drive you are able to set BIOS to boot from?

---

### Post by AmerNewbieInDE on 2009-09-19
sounds like you put grub on the linux drive and not the first drive.. boot to ubuntu, use alt+f2 type gksu kate. if you dont have kate install it. open /boot/grub/menu.lst toward the end of the page, you will see your linux install, add...

title        Windows XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

but change (hd0,1) to where ever your windows is located... to find it, you can use sudo fdisk -l from terminal.. my guess is (hd0,0)

then just boot from your linux drive and you should have a choice to boot to windows

---

