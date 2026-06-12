---
title: "Problems with software RAID 1 in Ubuntu server"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-04-20
Hi all, I have taken the following steps to set up software RAID 1 on two 500 GB IDE drives for my fresh Ubuntu server installation.
(I followed the [tutorial found here]("http://mywheel.net/blog/index.php/software-raid-in-ubuntu/"))

-Placed drives on separate IDE controllers

Using fdisk -l I found my 500GB drives on /dev/sdb and /dev/sdc.

I then ran:
sudo fdisk /dev/sdb

I created a new primary partition, began at cylinder 1, ended at cylinder 60800, and set it to type 83, then wrote the changes.

I repeated this for /dev/sdc

Since I didn't have it, I ran sudo apt-get install mdadm

It had me run through a "Citadel server" setup, which I had no desire for, but figured I needed it for RAID?

Then I ran this:
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

But now I'm stuck.  When I ran watch cat /proc/mdstat after reboot I just got the error message "at: /proc/mdstat:  No such file or directory."  I'm not sure how to check where I went wrong, or if I in fact set up RAID correctly and just don't know where to go from here.

Thanks!

---

### Post by Nixie Pixel on 2009-04-21
Does anyone know of a good tutorial site where I might be able to learn more about this?

---

### Post by Nixie Pixel on 2009-04-21
If I'm asking in the wrong forum, perhaps someone can let me know where I should ask?  I am really unsure of where to go from here.

Thanks!

---

### Post by ronparent on 2009-04-22
You might try the server forum for raid expertese. Also have you seen the following:

[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)

---

