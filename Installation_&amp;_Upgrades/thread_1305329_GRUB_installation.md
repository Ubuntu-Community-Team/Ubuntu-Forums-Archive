---
title: "GRUB installation"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Sigma47 on 2009-10-29
OK there may be an answer for this somewhere out there but Im pressed for time and have spent 3 days in the depths of reformats and such so gimme a freebee please.

I just installed 9.10 on my system after a long battle with "Win7 RC". I have 3 hard drives: 80 GB sys, 300 GB data, 300 GB backup attached in sequential order on my mobo. So I go and install Ubuntu and am gonna use the last 50 GB of my sys drive for root and home with 8 GB of the backup 300 GB for swap. Gparted saw the data drive as hdd0 or sda, and the sys drive as hdd1 or sdb. So at the last part of the install, I notice that Ubuntu is installing GRUB to HDD0 the data drive. I would like  the sys drive as primary boot drive. Win7 recognized these as disks 0-2 in the order I have them connected sys, data, backup, why for not Ubuntu do the same? and what can I do to get grub to HDD1.  thanks for your time and efforts, and I should say that the install w/ dual boot went perfect on my laptop and its blazin saddles!

---

### Post by JBAlaska on 2009-10-29
All is working as it should, Grub (The bootloader) must install on sda the active boot drive or it can't do it's job.

---

### Post by Sigma47 on 2009-10-29
Thanks for the fast reply JB, but I am under the impression that I am booting using sdb at least w/ Win7 anyway, so I am gonna change my HDD boot priority to boot from the data drive and point it to Grub but... how do I change how Ubuntu sees my HDD's so that it see's my smaller system drive as the active drive, sda? I would like to do this for mere organization and consistency...Thx

---

### Post by Sigma47 on 2009-10-29
OK Update, Switching my HDD boot priority to HDD0 loaded GRUB and every thing boots fine including Win, so my question remains though how do I switch these around so that GRUB and Ubuntu see my disks as HDD0/sda=80 GB sys, HDD1/sdb=300 GB data, HDD2/sdc=300 GB backup...can I do this. I would reinstall 9.10 if needed as I obviously have nothing config'd yet. Thanks again

---

