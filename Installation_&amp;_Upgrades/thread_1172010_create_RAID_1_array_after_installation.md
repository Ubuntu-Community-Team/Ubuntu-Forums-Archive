---
title: "create RAID 1 array after installation?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by gtmarks on 2009-05-28
I've just installed the desktop version of Ubuntu 9.04 on a new computer with two 750 GB hard drives.  I wanted a RAID 1 set-up.  During the installation, when I tried to manually edit the partition tables, I was not given the option to use a partition as "physical volume for RAID."  I went ahead with the installation anyway, creating equal swap partitions, creating an ext4 filesystem on the remainder of both drives, mounting one at root, and not using the other.  After completing the installation I tried to create a RAID array "after the fact" but have not been successful.

I installed GParted.  My hard drives are /dev/sda and /dev/sdb.  Using the partition editor I added "raid" under "flags" for /dev/sda1, /dev/sda2, /dev/sdb1, and /dev/sdb2.  I also installed mdadm.  The command fdisk -l shows the two disks, both with "Linux raid autodetect" under the header "System."  There is an asterisk under "Boot" for /dev/sda2.  When I enter the commands

mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1

and 

mdadm --create --verbose /dev/md1 --level=1 --raid-devices=2 /dev/sda2 /dev/sdb2

I get these errors:

mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: create aborted

(and likewise for the second command).  When I try "umount /dev/sda2" or "umount /" I get an error stating the device is busy.  Google unearthed about ten instances of this problem; I tried every one of the suggested solutions to no avail.  I'm wondering if it is now impossible for me to set up a RAID 1 array because the whole system is running on a partition I'm trying to use as part of the array.

If I can set up RAID, I assume it will erase everything on the drives, so I'd like to do this before installing anything else or putting any of my data on the computer.  Is there any way for me to set up RAID at this point?

---

### Post by ronparent on 2009-05-28
"I'm wondering if it is now impossible for me to set up a RAID 1 array because the whole system is running on a partition I'm trying to use as part of the array."

That is the answer right there. You would have to setup the mddam array from a live cd. Be aware that this will reformat the drive erasing your 9.04. You should use the alternate cd to set it up again so that the raid is active for your setup.

---

### Post by gtmarks on 2009-05-29
Thank you for the quick reply.  I reinstalled using ubuntu-9.04-alternate-amd64.iso and was successfully able to set up RAID 1.

---

### Post by novosirj on 2011-01-25
This actually isn't true. You can do it, but there are some tricks to it. I followed a guide I found on another site.

---

