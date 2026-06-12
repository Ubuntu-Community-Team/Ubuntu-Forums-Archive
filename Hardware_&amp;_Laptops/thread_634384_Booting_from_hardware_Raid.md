---
title: "Booting from hardware Raid"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by helioz on 2007-12-07
Hi All,
I am new to Ubuntu and this form so please go easy on me.

I have a true hardware raid system (Adaptec 2820SA controller) and I have Server V7.10 installed on a RAID1 volume.
Installation went OK but the system wan't boot from RAID1 volume.
I can boot using the CD and then select "boot from 1st HDD" in the menu and it boots OK.

I have searched and googled and the problems seems to be GRUB not wantign to boot from a RAID system - but I haven't found a real solution.

Please don't start the software vs. hardware raid discussion in this thread.

If you have a true HARDWARE raid system booting from a raid volume I would like know how it's done. (lilo?)

Many Thanks

Helioz

---

### Post by Yoooder on 2007-12-07
If you believe grub is the candidate then you may want to try a different bootloader such as LILO, which would at least allow you to determine for sure if grub is at fault.

---

### Post by helioz on 2007-12-08
I'm trying to find someone who's got a raid setup working (and booting).
It looks like the Ubuntu community is more desktop/enduser oriented.
Maybe I should be looking somewhere else .....

Helioz

---

