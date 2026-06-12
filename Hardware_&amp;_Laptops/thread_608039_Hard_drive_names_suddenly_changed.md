---
title: "Hard drive names suddenly changed"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by phalkone on 2007-11-09
I had 2 HD:
/dev/sdb and /dev/sdc which are two drives used by my RAID-1 array /dev/md0

I recently installed two new hard drives to store some extra data. These drives were given the names /dev/sda and /dev/sdd. I had a few normal reboots until I had my first fscheck fail, which I ignored (it was very late in the evening and after a reboot everything appeared to be in order). 
This evening I had a second fscheck fail and now I investigated it further. It turns out that /dev/sdb and /dev/sdd switched names. Now /dev/sdc and /dev/sdd are used for my RAID array and when my static mount (fstab) tried to load /dev/sdd it of course failed. I also ran lshw which confirmed that the names switched. 

I then disabled my /dev/sdb and /dev/sdc in fstab and rebooted the machine. It now appears that the names have changed back. This is a really difficult problem because I can't keep changing my fstab file. This machine is used as a server machine without a monitor so every time I have a fscheck fail I have to hook up a monitor and keyboard to exit the restore shell. 

I really don't know why this is happening and really hope that somebody can shed some light on this problem.

---

