---
title: "HP 6710s, GRUB installation fails"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Caldur on 2007-10-20
i am trying to install Ubuntu 7.10 on my HP6710s.. I already have WinXP there on partition F and Vista on C, which i cant boot, 'cos XP changed MBR :) then i have other partitons for data and one for linux..
so here is the problem.. i boot from ubuntu CD, start installation, choose location where to install linux ('/').. (i didnt create a swap disk, so maybe there can be the problem, but i have 2GB RAM, so i dont think i need it) then it starts copying data to the partition.. when all the data are copied, it tries to install grub.. but the grub installation fails and i can only click OK.. is there any way to view the install logs? how can i install grub or lilo so that i can boot my Ubuntu and XP (and perhaps Vista too :) ) thx

---

### Post by Sef on 2007-10-20
Download the [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It has easy to follow instructions.

---

### Post by Caldur on 2007-10-26
i tried and it does not work for me.. i dont have grub installed at all, so super grub disk cant restore grub files.. also i tried to boot linux from every disk it found and nothing happened :(

Then i tried to install Ubuntu again, but this time on my primary partition.. And this was a big mistake.. Not only it failed again with the same error, but also it changed mbr or something and i cant boot any OS now :( So people, i save u lot of time, DONT even try installing Ubuntu on HP Santa Rosa notebooks

---

### Post by logos34 on 2007-10-26
> **Caldur said:**
>  So people, i save u lot of time, DONT even try installing Ubuntu on HP Santa Rosa notebooks

There's a week-old sticky on that at top of Installation & Upgrades page:

['Problems with Gutsy on HP laptops.'  ]("http://ubuntuforums.org/showthread.php?t=582220")

---

