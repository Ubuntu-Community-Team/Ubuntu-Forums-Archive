---
title: "USB hard drive switching to read-only after I/O error"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by loopiv on 2005-12-19
Hello All,

Tried this on several systems with the same error.  Initially, I needed to do this on RHES 3.0, but then my co-worker tried his fedora box, then I hooked up the drive to my ubuntu desktop.

In a nutshell, a user has a Maxtor Personal Storage 3100 200GB usb hard drive formatted as FAT32 which he wants to copy approx. 150GB to.  Everything works okay for a few MB, even a Gig, but then I get the following error:

rsync: recv_generator: mkdir "/somedirectory.../dir" failed: Input/output error (5)

After which time the filesystem is read-only.  In dmesg I see:

[7166321.646000] FAT: Filesystem panic (dev sda1)
[7166321.646000]     fat_get_cluster: invalid cluster chain (i_pos 0)

not sure if this is something, but /var/log/messages show:

 localhost kernel:  0)

a few times.

Any ideas why the rsync flakes out?  My rsync command is:

rsync -rluvz -e ssh root@powder:/FS/dir/ /media/usbdisk/dir/

Any help would be much appreciated.

Vip

---

### Post by phyrewall on 2007-12-23
I'm getting the same issue on a 120GB WD Passport USB drive. It's formatted FAT32 as well (so my Xbox 360 reads it).

Running Ubuntu 7.10 with latest updates.

---

### Post by phyrewall on 2008-01-19
Bumping (as much as I hate doing it...)

Please someone help, this is driving me nuts.

---

