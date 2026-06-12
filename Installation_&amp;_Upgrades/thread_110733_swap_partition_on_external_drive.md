---
title: "swap partition on external drive ?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by HarryMangurian on 2005-12-31
Also, does Ubuntu automatically locate an available swap partition ?

---

### Post by earobinson on 2005-12-31
no it must be listed in your /etc/fstab

---

### Post by HarryMangurian on 2005-12-31
can fstab specify an external drive for swap ?

---

### Post by psusi on 2005-12-31
In theory... but why?

---

### Post by earobinson on 2005-12-31
i have been told by people on the forums that they installed ubuntu on an external hd so ya you could

---

### Post by HarryMangurian on 2005-12-31
[QUOTE=psusi]In theory... but why?[/QUOTE]

Ghost wants a free primary partition.  If I have XP, Ubuntu, swap, and an extended partition (with FAT32 for Linux/XP common files), I have used all the primaries allowed.  If I can put swap elsewhere, I can use Ghost.

---

### Post by psusi on 2006-01-01
All of the linux partitions can go inside an extended partition, including swap.

---

### Post by HarryMangurian on 2006-01-01
great news........

---

### Post by earobinson on 2006-01-01
it worked? may we ask why you wanted to do it in the first place?

---

### Post by HarryMangurian on 2006-01-01
I have a stock DELL Dimension running XP and Ubuntu.
I use Symantec Ghost for my Windows C: partition backup.
Ghost will not work if the drive already has 4 primary partitions. It gives an error saying there are too many primary partitions for it to create a virtual partition (or some words like that).   When I put Ubuntu boot and swap on the drive, the partitioning looks like this (more text below): this:[IMG]http://upload.pbase.com/image/54253608.jpg[/IMG]

The DELL diagnostic, XP boot, Linux, and extended partition (needed to add the SWAP) use up the 4 allowable primary partitions.  I am now running without a swap partition, so I can still use GHOST under Windows.  
Pretty screwed up, huh ?:confused:

---

