---
title: "Ibex and Windows 7 Dual-boot: Windows invisible to GRUB"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by gus.ke on 2009-01-11
I have Ubuntu 8.10 and Windows 7 BETA installed on separate partitions on my hard disk.  My dilemma is that I reinstalled GRUB (which was deleted by the windows installation, preventing me from booting into Ubuntu) and now it does not detect my windows partition.  All I know is that I have to somehow change the settings in GRUB (thats what one would do with Vista, right?), but the commands have changed since the last release of Ubuntu.  Any help would be greatly appreciated!

---

### Post by Tim Sharitt on 2009-01-11
Can you post the contents of /boot/grub/menu.lst

---

### Post by kranny on 2009-01-11
Why dont you edit your menu.lst manually to include windows 7 if there isnt one.


title Windows seven
root (hd0,x)
makeactive
chainloader +1

---

