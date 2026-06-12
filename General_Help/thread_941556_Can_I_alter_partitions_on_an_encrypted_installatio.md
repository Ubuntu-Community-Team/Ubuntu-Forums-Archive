---
title: "Can I alter partitions on an encrypted installation?"
date: 2008-10-08
forum: General Help
---

### Post by phil81uk on 2008-10-08
Hi!

My laptop has a single hard drive with only Hardy installed upon it. The installation is encrypted. I just followed a tutorial and installed using the Alternative Install CD. I don't really know what I did, I just followed the steps.

Can I use GParted to add an extra partition onto my drive so that I can then install Vista into it? I am worried because the drive is encrypted, and also I read that you must install Windows first and then Linux.

Thanks !!

PS. Great operating system. First time Linux user for 3 months. Shame I cant use it on my work machine as I rely on Sage and Photoshop.

---

### Post by justleen on 2008-10-08
yes, you can, but you cant use gparted straight away, since gparted cant handle lvm's (shame the encrypted install option only allows full disk usage)
you first need to resize the encrypted LVM.. 

have a look in this thread : [http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

PS: try [gimpshop! ]("http://www.gimpshop.com/")

---

