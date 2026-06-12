---
title: "Adding new internal Hard Disk DIrve"
date: 2008-12-19
forum: Hardware
---

### Post by RogerThompson on 2008-12-19
System: Dell Optiplex 755
OS: Ubuntu 8.10

A hardware tech installed an additional disk dirve in my machine early this morning.  He indicated that the BIOS can see the disk correctly.  So, the question is How do I get Ubunto to mount this.  i've looked in the forums and seen the discussion of adding a line to /etc/fstab, but I don't know what the device name should be.  If I do "ls -l sd*"  in /dev I get:
brw-rw---- 1 root disk 8,  0 Dec 19 06:43 sda
brw-rw---- 1 root disk 8,  1 Dec 19 06:43 sda1
brw-rw---- 1 root disk 8,  2 Dec 19 06:43 sda2
brw-rw---- 1 root disk 8,  5 Dec 19 06:43 sda5
brw-rw---- 1 root disk 8, 16 Dec 19 06:43 sdb

when I do a "df" I get:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230528596   8537340 210281080   4% /
tmpfs                  1993860         0   1993860   0% /lib/init/rw
varrun                 1993860        96   1993764   1% /var/run
varlock                1993860         0   1993860   0% /var/lock
udev                   1993860      2816   1991044   1% /dev
tmpfs                  1993860       104   1993756   1% /dev/shm
lrm                    1993860      2380   1991480   1% /lib/modules/2.6.27-9-generic/volatile


pluse some other drive that are mounted over the network using fuse.

Is the new disk the sdb in /dev ?

If this has been discussed already please point me to the appropriate forum entry.

Thanks

---

### Post by logos34 on 2008-12-19
This should answer all your questions:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

enjoy

---

### Post by RogerThompson on 2008-12-19
ok, this has gotten me to the place where I am editing the /etc/fstab file.

I notice that the drives have a UUID=<some very log hex> is this important for the new drive?

---

### Post by logos34 on 2008-12-19
you can use UUID or '/dev/sd_' format. To find the UUID of the new drive:

sudo blkid

( or sudo blkid -c)

or 

sudo vol_id /dev/sdb?

---

### Post by RogerThompson on 2008-12-19
OK, problem solved, and thanks given

---

