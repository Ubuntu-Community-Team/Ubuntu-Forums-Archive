---
title: "dual boot on laptop with usb hd!"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by susbut on 2007-05-01
I want  to dualboot on a fujitsu simens laptop. It has 160 GB hd (C) and a 80 GB usb hd (E). 
What is the best way to partition, and has anyone any experience with Ubuntu (Dapper) on a usb hd?

---

### Post by teh.element on 2007-05-02
I installed Fiesty and WinXP on my laptop, but for some reason, ANY time my external hd is turned on and I try to boot, GRUB fails with an Error 17. I am not sure exactly why, but my external interferes with GRUB. I would like to have Ubuntu installed on my external, but I don't know of anyone doing it.

It is easier if you just partition your 160 and install grub to the MBR and use your external as storage. If you want you can even install NTFS-3G to read/write to your external if it is in NTFS format. FAT(32) is natively supported by both Windows and Ubuntu making it the simplest way for sharing files between both OSes. However w/FAT(32) you cannot have files >4GB. NTFS-3G is still in beta stage and may not be completely reliable. I have my laptop dual boot on the internal hd w/my external as NTFS. I also have a FAT32 partition on my laptop that i use for transfering btw OSs incase i dont have my external and still need to transfer.

---

### Post by monojbaruah on 2007-05-02
I have install ubuntu 7.0.4 on my external USB drive. Before installation, I removed the internal sata HDD from the laptop. The HDD was later reinstalled and my dual boot system (winXP and Ubuntu )works perfectly OK.

Monoj Baruah

---

