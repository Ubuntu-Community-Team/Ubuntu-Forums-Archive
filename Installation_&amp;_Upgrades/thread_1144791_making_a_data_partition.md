---
title: "making a data partition"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-05-01
I want to install jaunty  on a new HDD and make a serperate linux  partition to store data that can be mounted manually(just like we have a windows OS partition and a seperate data drive in windows)
I can install the 9.04 using the live CD but the later part of creating a partition to store data and then finding it to mount is something i have never done   
kindly guide me,Thanks!

---

### Post by pbpersson on 2009-05-01
It could appear different ways, it could be done different ways

Let us say you have two Linux distributions on your machine

You could:

1.  Designate one paritition that would be used as home in both distros
2.  Designate one partition that would be a data partition to be manually loaded
3.  Designate one partition that would be a data partition to be automatically loaded
4.  Manually load the root partition from distro 1 when you are in distro 2
5.  Automatically load the root partition from distro 1 when you are in distro 2

The list goes on and on

Specifically concerning your question, I have seven distros loaded on this machine.  I go to my file manager, I see all the partitions on the left side of the window, I double-click to mount, provide a password, and I am in.  That is manually mounting another ext3 partition.

---

### Post by richlyn9 on 2009-05-01
So do i just create a new partition and format it (from live CD)to ext3 file system, name it and it should show up in file manager?

---

