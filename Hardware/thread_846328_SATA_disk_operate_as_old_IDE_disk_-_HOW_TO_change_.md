---
title: "SATA disk operate as old IDE disk - HOW TO change it?"
date: 2008-07-01
forum: Hardware
---

### Post by jreinis on 2008-07-01
I have a HP DV6115 (DV6000 series) laptop. 
hdpatm -tT shows 
Timing cached reads: 1722 MB in 2.00 seconds = 860.85 MB/sec
Timing buffered disk reads: 102 MB in 3.03 seconds = 33.65 MB/sec
This disk is SATA-I!
My virtual disk on another computer operates as 67 MB/sec!

How to change the situation?

hdparm -i :
model ST9100824AS

---

