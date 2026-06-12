---
title: "Ultrabay HDD not recognized T540P"
date: 2014-12-14
forum: Hardware
---

### Post by wtgambo9 on 2014-12-14
New laptop, put SSD in primary bay installed 14.04.1.  Everything works.  Installed 1TB drive in ultrabay adapter and it is not mounted.  The drive is good, took it out and connected USB, fine.  Does it require a manual mount?  Obviously installed where the CD drive was and it is enabled in BIOS.

---

### Post by houstonbofh on 2014-12-15
Sata drives do not automount like USB drives.  Look in "Computer" to see mountable drives.

---

### Post by Mark Phelps on 2014-12-16
>  Installed 1TB drive in ultrabay adapter and it is not mounted. 

If this bay needs special SATA drivers, and the manufacturer does not supply those (which is typically the case), you're likely not going to get the bay to work in Linux.

---

### Post by wtgambo9 on 2014-12-18
Thanks, I got the problem solved.  The HDD caddy was from Newmodeus.  Called their tech support, they shipped a replacement caddy 2 days.  It works perfectly.  I now have the 500gb SSD primary and the 1TB in the caddy.  Only thing I had to do is chown -R on the mount in /*me*/media to use the TB rotating drive.  BTW, this caddy matches the hardware on the t540p perfectly, very nice and well made.  Well, not my first cup of Ubuntu but I had to change login for some reason - lost my beans but kept part of my brain.......Ubuntu for 8 years now ...):P

---

