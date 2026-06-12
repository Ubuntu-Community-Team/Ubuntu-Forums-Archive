---
title: "Adaptec 1200A as just controller card - no RAID"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by blueorder on 2007-08-28
Can I use this RAID card as just an IDE controller card?

I'm currently using it with RAID1  on Windows but want to move to Ubuntu server. Can I just erase the RAID from the card BIOS and use software RAID?

BTW, I have 4 drives. A system drive, CDROM and the 2 drives that will be on RAID1. That's why I ask about using the 1200A as a controller card to keep the RAID drives on separate channels.

---

### Post by blueorder on 2007-08-29
I am guessing if the installer sees both drives connected to the 1200A that it is working as an IDE controller only. I, then, can use the System drive connected to IDE1 master, CD-ROM connected to IDE2 master, data drive 1 connected to 1200A IDE1 master and data drive 2 connected to 1200A IDE2 master. Keeping everything in its own channel. 

Then, I can install Ubuntu server to system drive and do software RAID1 on the 2 data drives.

Correct? Anyone?

---

