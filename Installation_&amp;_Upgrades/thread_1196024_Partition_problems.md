---
title: "Partition problems"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by NoOne121 on 2009-06-24
I am new to linux/ubuntu and using 9.04. Dual booting with winxp.
Been ok for a couple of weeks now but ran into problems installing a newer kernel to test out.(2.6.30) The installer (kernel check) said I had ran out of disk space.

Odd I thought as I had definately allowed about 25 gigs for my ubuntu install using the wubi installer and i checked this after install and all was ok.

Using Disk Usage Analyser in ubuntu it says i have a... 166.1 Gb capacity, used 103.4 Gb , available 62.7Gb ....which I most definately do not have as my hd is only 80 gig.

In winxp it looks like my windows partition is about 76Gb...basically all the hard disk?

How can I sort this and is it best to work from winxp or ubuntu to do so. Dont really want to loose my xp install and would prefer if anything to loose ubuntu and start over again if i absolutely must do.

thanks guys....

---

### Post by NoOne121 on 2009-06-24
this is my.. df ..output


Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      16876388  15413304    605792  97% /
tmpfs                   767880         0    767880   0% /lib/init/rw
varrun                  767880       112    767768   1% /var/run
varlock                 767880         0    767880   0% /var/lock
udev                    767880       152    767728   1% /dev
tmpfs                   767880        84    767796   1% /dev/shm
/dev/sda1             78148160  46231540  31916620  60% /host
lrm                     767880      2392    765488   1% /lib/modules/2.6.28-11-generic/volatile


just realised that looks hard to read...sorry

---

### Post by NoOne121 on 2009-06-24
this is odd to me....looks like im going to loose something here does anyone understand this gparted screenshot or an idea how to go forward.

thanks

---

### Post by NoOne121 on 2009-07-03
can nobody help out here....where is my linux install?

the above screenshot is from within jaunty? i have also run gparted from a live cd and it looks the same!!

under /host in jaunty I can see ALL my windows installation and files?

if jaunty cannot be run under ntfs then why does the screenshot of gparted indicate i am running only an ntfs file system.

baffled

---

### Post by NoOne121 on 2009-07-03
another screenshot

---

### Post by merlinus on 2009-07-03
Of course it only shows ntfs.  Wubi installs ubuntu as a directory within your windows partition.

If you are liking ubuntu, then do a regular install, partioning your hdd to make room for it, and then get rid of the wubi installation.

---

### Post by NoOne121 on 2009-07-04
crikey i had no idea. i thought wubi partitioned the hard disk and installed jaunty properly?

back to the drawing board for me then.
So i boot to windows and partition my hard disk and reinstall properly. what will happen to my grub menu though?

thanks for the advice

---

### Post by merlinus on 2009-07-04
Go into windows and disable its paging file.  Should be under system tools.  Reboot, delete pagefile.sys, and defrag several times.

Then you can do a side-by-side install from the ubuntu live cd.  You will be able to resize windows and specify sizes for linux partitions during the process.  There are sliders that will allow you to select how much space to give each.

Grub will be reinstalled, and you wil be able to boot into either os from the menu.

---

