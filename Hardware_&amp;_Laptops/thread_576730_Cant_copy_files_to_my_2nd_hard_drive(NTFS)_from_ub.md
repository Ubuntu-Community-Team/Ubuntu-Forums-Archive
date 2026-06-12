---
title: "Cant copy files to my 2nd hard drive(NTFS) from ubuntu"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by geraldabey on 2007-10-15
Im using my 1st hard drive only 4 ubuntu n i partioned it to one drive but no im running out of space n want to copy most of my multimedia files to my 2nd hard drive which is also partioned into one drive n this one has XP in it when connect both the hards its mounted but comes as read only thats my 2nd hard

pls help me out

---

### Post by 505 on 2007-10-15
You need the NTFS-3g driver to enable write support for NTFS. It's in the repositories. After that change /etc/fstab so to use the driver for your NTFS drive. Just google for an actual how-to.

---

