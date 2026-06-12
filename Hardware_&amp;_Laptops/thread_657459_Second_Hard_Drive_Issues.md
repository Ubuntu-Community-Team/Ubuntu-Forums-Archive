---
title: "Second Hard Drive Issues"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by deviance on 2008-01-03
I have managed to install a second hard drive, partition it, and format it. I can mount it to /media/sda1

I have then run "sudo cp -vax /home /media/sda1"
This created the file system /media/sda1/home/tim etc etc
I want to now mount it as /home.

Unmounted it and added it to /etc/fstab

When I "sudo mount -a" no programs could find any file system. I quickly removed it from fstab and unmounted it. 

There are two problems I think, one is 3 different places have told me different lines to add to fstab, and the other is I think the file system is wrong, I intended to mount it as /home but the copying copied it into the folder /home, so it would read /home/home/tim when mounted.

Please could someone tell me, should I delete all of sda1, and run "sudo cp -vax /home/tim /media/sda1"? And what is the correct line to add to my fstab, it is /dev/sda1, to mount as /home and ext3 is the file system.

Or is there another easier way?

Please help ^_^

---

### Post by deviance on 2008-01-05
Hate to bump, but can anyone help at all?

---

### Post by deviance on 2008-01-06
Hate to bump, is there anyone that can help?

---

