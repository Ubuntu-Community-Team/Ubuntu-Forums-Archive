---
title: "Partition Proplem in Breezy Version"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by abood on 2006-01-10
Hi all,
My proplem that i was using Ubuntu 5.04 Hoary + Windows Xp, lately i want to remove the Hoary copy (not upgraing) but to install a new fresh copy of Breezy's, i downloaded an iso image from ubuntu website and checked the md5sum for it, it was correct and i burned it in a slow speed to be insure that everything is fine, i entered the cd on boot and everything goes well till i faced the partition section that i cant find my NTFS (xp) partions or the linux one that was installed before, so any one got any solution for this, i tried the ubuntu copy on another machine and it worked well .
Regards,

Abood

---

### Post by Sef on 2006-01-10
With the Breezy Live CD, use the partitioner on that to check your partitions.  

Even though it downloaded correctly, your Breezy Install copy may not have burned right; the cd that you burned it on could be bad; or their is something that got on the disk, e.g. a fingerprint, dust, etc.

---

### Post by abood on 2006-01-10
Sef, i burned 2 cd's and i face the same proplem they are very good cd's "imation", and as write before it works on the another machine .

---

### Post by abood on 2006-01-11
Please guys any feedback for this proplem

---

### Post by aysiu on 2006-01-11
If Hoary installed correctly, maybe your best bet is to stick with Hoary and then ```
sudo apt-get dist-upgrade
``` to get Breezy instead of a fresh Breezy install.

---

### Post by kingsidy on 2006-01-11
the problem does not look like a bad cd problem. during the install when you get to the partition section, you when select edit partition manually, normally it should detect the windows partition. otherwise, just do a dist upgrade like aysiu suggested

---

