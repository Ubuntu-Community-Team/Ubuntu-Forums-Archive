---
title: "Partitioning failure at install (+ Wubi incomplete install)"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Zwemshortventje on 2009-05-03
Hi all, a few days ago I decided to try out Linux, so I downloaded the image and burned it to a CD, but the LiveCD wouldn't work. So I used Wubi to install it on my HDD (I think that's what it does). The install worked smoothly until it got stuck at "Creating virtual disks", where it remained for over 15 hours after which I aborted the install. But to my great surprise, Ubuntu was installed and I could start it with GRUB when booting my pc.

So I tried the demo mode and I liked it. Then I tried to install it.

1) By using the normal installing mode, when booting.

It gets stuck at this screens (translated):

First: > [U]Would you like to return to the partitioning program?
[/U]One or more of the partitions which you have made are too small. Make the following partitions at least this size (in bytes):

/2061720064

If you do not go back to the partitioning program and resize the partitions, the installation can fail.

[LEFT]Back / Continue
[/LEFT]
Clicking back takes me back to the same screen. Note: I made the partition 300gb big...
Clicking continue:
> _The installation is being checked_
The system is being installed
(progress bar: 0%)
Cache in partition #1 at /host/ubuntu/disks/swap...

2) By using the 'installer' button on your background

First time I tried this, it would run the installer until the end, except for again a partition problem that would keep asking me the same again.

This morning i tried again, and now it's stuck at step 3 out of 7, at 50% progress bar at the 'Disks are being checked' screen...


Does anyone know what I'm supposed to do, or what I'm doing wrong?

---

### Post by axelsvag on 2009-05-03
I got exactly the same problem. I have used wubi installation since 8.04 and it has worked perfectly. I used the upgrade and 9.04 worked as it should but I wanted to make a clean WUBI installation. And then everything got wrong as you described.  What I also noticed was that the installation produced a a very large log file more then 4 gig. I would also really would like some advice aswell. I think you should file a bug report describing this error.

---

### Post by Zwemshortventje on 2009-05-03
If I just wanted Ubuntu, what you recommend me? That I download 8.04 which hopefully will work, or file a bug report which hopefully will be solved? Where do I find that log btw?

---

### Post by axelsvag on 2009-05-03
I use 9.04 on four of my computers so 9.04 should be fine. But in our cases something seems to be wrong. I succeded to use wubi 8.10 so that wubi should be OK maybe I try for my self tomorrow.

---

### Post by axelsvag on 2009-05-05
I finally succeded in installing. First of all I changed my drive from FAT to NTFS and then I made a chkdsk on the drive. I do not know what made the different but the installation in windows went on as it should and everything installed. So maybe some broken files or  problem with FAT and WUBI 9.04 was the root of the evil..

---

