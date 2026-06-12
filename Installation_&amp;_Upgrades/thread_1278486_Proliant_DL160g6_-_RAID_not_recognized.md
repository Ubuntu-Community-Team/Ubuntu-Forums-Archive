---
title: "Proliant DL160g6 - RAID not recognized"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by misterfriendly on 2009-09-29
Hello,

Brand new ProLiant DL160g6 with 4 SATA 160 GB drives - I set them up with a single RAID 0+1 logical drive using the HP RAID configuration cd.
Ubuntu installer doesn't recognize the logical drive - it sees all 4 physical drives and gives me the option to format/install on one of them. But that's not what I want to do!
I've tried 8.10 and 9.04 installers, same problem - any tips on how to fix this?
Thanks!

---

### Post by lemming465 on 2009-10-03
Probably the *HP Smart Array B110i SATA RAID Controller* doesn't have an Ubuntu Linux driver yet.  In your situation I'd give up on the hardware RAID and using the alternate install CD to make an LVM stripe across MD raid-1 mirrors and do the disk setup entirely in software at the OS level.

---

### Post by misterfriendly on 2009-10-04
yep, I think that's what's happening - LVM is a little confusing but I think I got it working.
Next adventure: configuring eBox ...

---

### Post by 3L33T on 2010-05-04
yada yada

---

### Post by misterfriendly on 2010-05-04
It's been a while, so I don't exactly remember what I did - but the server has been running ever since, so I must have fixed it!
Probably I just made a software raid set. Good enough ...

---

