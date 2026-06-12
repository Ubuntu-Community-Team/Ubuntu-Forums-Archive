---
title: "DVD Issue"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by dizzie on 2005-03-22
Greetings.

Any idea why any and i mean ANY players wont play DVD, got errors like "cant find dvd://" or "DVD is in a encrypted format" or "No media and drive"

My DVD drive is a "Liteon DVD-Rom LTD163" 

Totem complains about a missing plugin btw....

Oh and yes /dev/dvd exists and points to my dvd drive

/dev entries

lrwxrwxrwx  1 root root 3 2005-03-20 11:04 /dev/dvd -> hdc
lrwxrwxrwx  1 root root 3 2005-03-20 11:04 /dev/cdrom -> hdc

fstab

/dev/hdc        /media/cdrom0           udf,iso9660 ro,user,noauto              0       0

Any ideas ?

---

### Post by IdoMcFly on 2005-03-22
search for DVD in ubuntu site, there is a faq entry for this

---

### Post by dizzie on 2005-03-23
libdvdcss2 = sorted  8)

---

