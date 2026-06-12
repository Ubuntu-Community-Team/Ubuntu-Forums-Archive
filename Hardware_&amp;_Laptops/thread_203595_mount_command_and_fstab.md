---
title: "mount command and fstab"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Blazeix on 2006-06-25
Hi, I recently purchased an external harddrive, and I got it working fine by putting an entry into fstab and then running "mount -a":
/dev/sdb1       /mnt/sdb1       ntfs    nls=utf8,umask=0222     0       0

I'm not sure of one thing though. I will only be using this hard drive occasionally, so it won't always be plugged in. Is there any harm in leaving the fstab entry in there, or do I have to take it out if the hard drive is not going to be plugged in? Thanks.

---

### Post by mlind on 2006-06-25
[QUOTE=Blazeix]Hi, I recently purchased an external harddrive, and I got it working fine by putting an entry into fstab and then running "mount -a":
/dev/sdb1       /mnt/sdb1       ntfs    nls=utf8,umask=0222     0       0

I'm not sure of one thing though. I will only be using this hard drive occasionally, so it won't always be plugged in. Is there any harm in leaving the fstab entry in there, or do I have to take it out if the hard drive is not going to be plugged in? Thanks.[/QUOTE]

There *could* be one problem I can think of. /dev/sd? entries are assigned to
other external devices too. When your drive is not plugged and you plugin another
usb device, it could get /dev/sb1 device node assiged to it. I'm not sure how
your fstab entry would affect this.

You can define udev rule for your external hdd, that will always assign unique node
for your drive, for example /dev/my_hdd which you can use on fstab.

This is just my guess, could be that you will never encounter any problems.

---

