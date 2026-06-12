---
title: "Partitioning"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by Stragne_One on 2005-12-22
I have my entire partition on ntfs, can I change it FAT32 or FAT16 without having to delete to old partition, so i can resize it?

---

### Post by darth_vector on 2005-12-22
no, you cant change from NTFS to FAT32 or FAT16. you can resize your NTFS partition using a windows program called Partition Magic, but you will have to pay for it.

---

### Post by Stragne_One on 2005-12-22
[QUOTE=darth_vector]no, you cant change from NTFS to FAT32 or FAT16. you can resize your NTFS partition using a windows program called Partition Magic, but you will have to pay for it.[/QUOTE]
i heard of a program called QtParted, how does that work?

---

### Post by foolosophy on 2005-12-22
you don't need to change it to fat. there's some soft that allows you to resize nfts. QTparted may work. Download the Knoppix cd, and you'll be able to do it. I  did it last week.

---

### Post by zappa86 on 2005-12-23
If you are installing linux I know the CD has a resizer on it. I resized my friends NTFS down 15gb to make room for linux. After that though, I have no idea how to do it.

---

### Post by roelofs on 2005-12-28
For general NTFS resizing info, see the [NTFS Resize Frequently Asked Questions]("http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html") page.  The current version recommends KNOPPIX, but a year ago it suggested [SystemRescueCD]("http://www.sysresccd.org/"), which is what I used successfully on the XP system I got at work.  Ubuntu itself includes ntfsresize (albeit an older version), so that might be the most reasonable route to try.

---

### Post by az on 2005-12-28
The installer will resize by default.  All you need to tell it is how big.

---

### Post by psusi on 2005-12-28
Or if you don't want to install ubuntu, or already have, you can resize by booting from the livecd and running gparted.

---

