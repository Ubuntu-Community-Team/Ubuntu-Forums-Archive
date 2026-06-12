---
title: "sil 3124 help making this work"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by Cr0n_J0b on 2007-11-24
I have a RAID controller that is based on the SI 3124 chip.  It presents 4 sata drives, 3 of which i have configured for RAID (in the bios).  My question is...what should I expect from this?  I'm only seeing seperate devices for the RAID set, so I'm guessing that i need some type of driver to make the OS see the group I created in the BIOS.  I have heard of FakeRAID, but I'm wondering if there is a Silicon Image driver that I can use instead?

My next option is to just create software sets, but I wanted to make to see if there was a hardware option first. 

thanks

---

### Post by notetoself.net on 2008-04-14
did you get ubuntu to see the raid group for your sil3124 controller?  i have the same issue.  i have two drives on it in an existing raid1 array that the BIOS can see.  i can see the separate discs using fdisk -l, but i don't know how to mount them together.

---

