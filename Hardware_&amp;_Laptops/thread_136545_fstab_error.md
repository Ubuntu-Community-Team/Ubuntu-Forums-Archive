---
title: "fstab error"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by simon0t7 on 2006-02-26
I'm having a little bit of a problem with m fstab after I added 2 hard drives to my ubuntu machine.


Here's my fstab configuration:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdf1 /home  ext3 defaults,nodev,nosuid 0 2
/dev/hde1 /home/simon/downloads ext3 defaults,nodev,nosuid 0 2


Here's df -hT

> root@ubuntu:/home/simon# df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3    109G  2.8G  101G   3% /
tmpfs        tmpfs    252M     0  252M   0% /dev/shm
/dev/hdf1     ext3     74G  277M   70G   1% /home
/dev/hde1     ext3    111G  129M  105G   1% /home/simon/downloads


During boot up, it says my hdf1 and hde1 aren't ext2 and tells me to hit control-D to continue or run some e2fschk.  After i hit control-d, it'll boot but i'll be missing my home directory because it didn't auto mount

if someone tells me where the boot log is, I can post my error :)

---

### Post by localzuk on 2006-02-26
You could try changing ext3 to auto in fstab for each of the hard disks and see if that stops the complaint.

---

### Post by simon0t7 on 2006-02-26
I changed it to this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdf1       /home               ext3    defaults 0       0
/dev/hde1       /home/simon/downloads               ext3    defaults 0       0


and it works, except it doesn't mount

I see this after i putty in:
> Could not chdir to home directory /home/simon: No such file or directory



will try your setting now


----------------------------


Update:

I tried your suggestion and I got the same error message as above :|

Premount permissions: (/)
> drwxr-xr-x    3 root root  4096 2006-02-26 09:11 home

After I manually mount (mount /home), here's the permission of my home (/home/simon)
> drwxr-xr-x  27 simon simon 4096 2006-02-26 09:12 simon

---

### Post by simon0t7 on 2006-02-26
tried chmod /home to 777 and it didn't work

> Could not chdir to home directory /home/simon: No such file or directory

remains

---

