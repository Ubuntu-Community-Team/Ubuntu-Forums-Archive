---
title: "harddrive installation problem"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by communico on 2005-09-07
Hi, I've installed Ubuntu on a machine with 6 harddrives. There is a primary, a secondary, then four in a raid configuration. They were all setup in the bios okay.

I followed the instructions in the how to install a harddrive in the wiki, and I managed to format them ... I assume, because it all said the right stuff. This might have been the complete wrong thing to do, but then I mounted the four raid devices into a folder /raid/disc1 raid/disc2 etc. I can access them through the filesystem browser, but I cannot create folders or write files to them.

I'm a little stuck at this point ... I'm coming from a dos background, so I'm still fuzzy on the concept of how harddrives are accessed through unix.

---

### Post by communico on 2005-09-07
I get these errors when I use this command:

root@ubuntu:/home/communico # dmraid -ay -v
ERROR: sil: zero sectors on /dev/sdc
ERROR: sil: setting up RAID device /dev/sdc
ERROR: sil: zero sectors on /dev/sdd
ERROR: sil: setting up RAID device /dev/sdd
ERROR: sil: zero sectors on /dev/sde
ERROR: sil: setting up RAID device /dev/sde
ERROR: sil: zero sectors on /dev/sdf
ERROR: sil: setting up RAID device /dev/sdf

any ideas about what it means by zero sectors? does that mean I didn't format them correctly?

---

