---
title: "Fiesty: hdx changed to sdx, one drive not being recongized"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by B-Con on 2007-05-04
Why does Feisty only recognize my hard drives as sdX, rather than as hdX, like under Dapper? They're normal IDE-connected ATA hard drives.

Also, it no longer recognizes the third of my hard drives. I have the primary disk on one cable (with the OS) and two other drives on another cable, but only the first of those two is recognized. The second gets completely ignored and I don't see it show up under /dev.

Why'd hdx change to sdx? And, more importantly, any suggestions on how to fix that problem?

---

### Post by tact on 2007-05-04
Hi there,

I asked the same question in here a few days ago and more knowledgable people pointed me to a ubuntu site where it is explained that this is a deliberate "feature" of fiesty (7.04).

Apparently there is some benefit in faking out the system to think your IDE HDD's are SCSI and also it will mean that all users of ubuntu in the future will have the same HDD naming conventions whether using IDE or SCSI. (for all of us our first HDD will be sda regardless whats under the bonnet).

---

### Post by B-Con on 2007-05-05
Interesting. I'll see if I can chase down more documentation along those lines at some point. Thanks for the info. :-)

---

