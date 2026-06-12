---
title: "LVM Partitioning"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by adamitj on 2009-05-06
What are the pros and cons of using LVM partitioning in a Desktop & Server machines?

---

### Post by tomcheng76 on 2009-05-06
what impress me in LVM is that i can even enlarge my lvm partition to use empty space of the harddrive while i am using the OS to do daily task!

---

### Post by kryptikos on 2009-05-06
In a server environment I prefer to use LVM as it gives you greater flexibility in day to day operations and gives you ease of disk management. Meaning I don't have to dedicate the entire disk at one time. I can divide it up based on application need, size requirements etc. If I just do a standard partition I'm stuck...especially if I have an app that has specific requirements. I'd have to redo the entire partition and restore from backup. 

Some leisure reading on the benefits to using LVM:

[http://linuxbsdos.com/2008/09/24/the-benefits-of-using-linux-logical-volume-manager/]("http://linuxbsdos.com/2008/09/24/the-benefits-of-using-linux-logical-volume-manager/")

[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html]("http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html")

[http://www.linux.org/docs/ldp/howto/LVM-HOWTO/benefitsoflvmlarge.html]("http://www.linux.org/docs/ldp/howto/LVM-HOWTO/benefitsoflvmlarge.html")

---

### Post by matpol on 2009-05-06
If this is for a home computer I wouldn't bother. I used to have centos setup using lvm - when it went wrong it was a pain to fix. I never expanded the partitions or anything. For me it seems easier just to mount and format another disk.

---

### Post by OlympicSoftworks on 2009-08-08
Unless you have a media center that you have movie/music files on.  You may want to be able to add to it's storage and LVM offers a excellent method to do so.

---

