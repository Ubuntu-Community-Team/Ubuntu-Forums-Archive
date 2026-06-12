---
title: "Disk wakes up almost immediately after HDparm sleep cmd."
date: 2014-06-29
forum: Hardware
---

### Post by tubos2 on 2014-06-29
I have a 2TB USB2 external disk formatted ext4

when I use: 
      [B]sudo hdparm -Y /dev/sdb
[/B]the disk goes to sleep as expected.

But after like 5-10 secs spins up again out of itself.

I also tried setting short spindown interval with hdparm but nothing happens.

what can I do to troubleshoot this?


os: UBUNTU SERVER 14.04 
disk:Iomega 2TB companion drive

---

### Post by tubos2 on 2014-06-30
anyone?

---

