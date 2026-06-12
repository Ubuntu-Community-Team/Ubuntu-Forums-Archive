---
title: "Installing multiple distros from my hard drive"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by brncao on 2009-06-06
I don't have any DVD-RW's around nor can I get my DVD burner working. So my alternative route is to use my external hard drive (FAT32) to install Linux onto my laptop. I have multiple distros (ISO's) I want to install. There are guides telling you how to install one distro via hdd, but none for multiple distros afaik. I want to be able to choose from the boot menu which distro to boot from.

---

### Post by zvacet on 2009-06-08
You can try [Unetbootin.]("http://lubi.sourceforge.net/unetbootin.html")

---

### Post by Soul-Sing on 2009-06-08
Some general information. (I hope it will be helpful...)

A harddisk can only contain 4 primairy partitions. So make an extended partition, which can contain unlimited logical partitions.
linux can be installed on logical and primairy partitions....
Then you need a tool to partition: the gparted iso, burn it, and it runs like a live-cd!
1) make an extended primairy partition which you divide into the deisired number of logical partitions.
Logical partitions begins with the 5 number, because the first 4 are reserved for the primairy partitions.
You need 1 swap for all linux systems.
BSD systems and windows can only be installed on primairy partitions!!

---

### Post by brncao on 2009-06-12
Thanks for the help! I really appreciate it:KS

---

