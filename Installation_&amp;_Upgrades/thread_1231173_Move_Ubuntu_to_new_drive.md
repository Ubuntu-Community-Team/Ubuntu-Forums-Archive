---
title: "Move Ubuntu to new drive"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by dr_pressure on 2009-08-04
Hey guys, I'm in the process of setting up a new webserver for a volunteering organization here.

I'm trying to move their standard ubuntu installation over to a new HDD.

If I boot the system up in a live cd and use

dd if=/dev/old of=/dev/new 

Is there anything else I have to do? Because I will be copying all the partitions and the MBR, I should not have to update grub or do anything else... correct?

Do I have to worry about aligning the partitions or anything like that?

I'd really appreciate any advice!

---

### Post by Sef on 2009-08-04
Check out [Clonezilla]("http://clonezilla.org/").

---

### Post by dr_pressure on 2009-08-04
Okay thanks, I'll check it out. BTW, are you from the good Korea or the bad Korea?

---

