---
title: "The kernel was unable to re-read the partition table on /dev/md0"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by ryanswan on 2009-01-31
I've been trying with no luck to do software raid with 8.10.  I've set up software raids before with Hardy and Edgy but Intrepid baffles me.  I keep getting these type of errors:

&#8220;The kernel was unable to re-read the partition table on /dev/md0 (Invalid argument). This means Linux won&#8217;t know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/md0.&#8221;

Please help, I've been wrestling with this for days now.  I'm trying to do RAID1 and RAID5 with software.

Simple example:
I'm setting up 4 primary partitions on 2 drives all as "physical volume for RAID"
#1 100MB for /boot
#2 2GB for swap
#3 50GB for /
#4 450GB for /home

Then I got to Configure Software RAID and create the md devices.  This has worked in the past for me without trouble.

---

### Post by josheby on 2009-02-11
any luck with this?  I am having the same problem...

I have two 400.1GB hard drives...

RAID 1 /dev/md0 ext3 / "root"
/dev/sda1 396.1GB
/dev/sdb1 396.1GB

RAID 1 /dev/md1 swaparea
/dev/sda2 4GB
/dev/sdb2 4GB

---

### Post by Gonkers on 2009-04-04
I am getting this same error with Debian 5.0. I'm doing almost the same as ryanswan, just different sizes. Very frustrating. I'm downloading Ubuntu now to see if there is any difference, but I'm doubting it.

---

### Post by SkyHiRider on 2010-06-14
Anyone knows whats the cause of this/how to fix it? Getting it on Debian 5 and is heck of annoying to try to fix this by trial and error.

---

