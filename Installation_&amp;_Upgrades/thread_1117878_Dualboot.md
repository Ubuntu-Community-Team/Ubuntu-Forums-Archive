---
title: "Dualboot"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by pontuslp on 2009-04-06
Hey. I've been searching this forum and others for a solution to this, but none of the solutions made my day :S

I once had an IDE drive with windows xp, and one SATA drive with ubuntu, swap and a shared media, which all worked perfectly. One day ubuntu stopped working because of some drive corruption (or something). I didn't bother for a while, and just kept using windows instead, until last week. I did a reinstall of ubuntu 8.10. It worked, so I switched over to ubuntu. Today I tried starting xp for the first time since, and it didn't work. Grub gave error 13.

fdisk shows (swedish, but should be comprehensible to those who knows this stuff):

Disk /dev/sda: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xdf6a9ecf

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612        2676      522112+  82  Linux växling / Solaris
/dev/sda3            2677       30401   222701062+   5  Utökad
/dev/sda5            2677       30401   222701031   83  Linux

Disk /dev/sdb: 20,5 GB, 20525137920 byte
255 huvuden, 63 sektorer/spår, 2495 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x155a1dd3

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *           1        2494    20033023+   7  HPFS/NTFS



And my menu.lst

title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

I've tried some different combinations on this, as told in different topics, but none fixed it. Any ideas?

---

### Post by meierfra. on 2009-04-12
Did you try

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1

---

