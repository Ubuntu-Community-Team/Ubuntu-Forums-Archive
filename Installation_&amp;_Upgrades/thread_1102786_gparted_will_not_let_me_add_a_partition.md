---
title: "gparted will not let me add a partition"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2009-03-22
I have a 500 gig drive with Ubuntu 8.10 which is using the whole drive.  It is formatted ext3. I want to add a partition in order to move my home directory to it.  When I try to add a 100 gig partion, gparted runs but then stops with errors.

	
resize2fs /dev/sda1 377326655K
     	
nice: resize2fs: Input/output error


How can I fix this?

---

### Post by neilevan814 on 2009-03-22
Are you trying to run gparted from your installed distro?  Because you won't be able to do that.  You need to run gparted from the live CD in order to repartition the OS.  I do believe.

---

### Post by lindsay7 on 2009-03-22
I am using the live cd.

---

### Post by dandnsmith on 2009-03-22
I'm not sure that you can reduce an ext3 partition in size.
You may need to back it up, delete the partition, add the new partitions, and then restore from the backup.

I hesitate to suggest how you do the backup, as you haven't given any indications of size, and whether you can attach external HDDs ...

---

### Post by lindsay7 on 2009-03-22
Is this a problem with Gparted or is this an issue because it is an ext3 partition?

Could I use Acronis Tools to do this? Would resizing the ext3 partition mess up my install of Ubuntu on this drive?

I have looked all over the internet and can not find much that helps. I would have thought that this would have been a common question. The reason why I am trying to do this is I read in this forum that I would be a good idea to move your home directory to its on partition because upgrading would be safer.

---

### Post by lindsay7 on 2009-03-23
Ok, thanks for the help. I have Ubuntu on a 500 gig drive used only by Ubuntu. So it is on sda1 and I want to partition it and use about 100 gigs for a home partition. Gparted runs but them stops and give an i/o error.

Code:

ubuntu@ubuntu:~$ sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1003436         0   1003436   0% /lib/init/rw
varrun                 1003436        84   1003352   1% /var/run
varlock                1003436         0   1003436   0% /var/lock
udev                   1003436      2856   1000580   1% /dev
tmpfs                  1003436       104   1003332   1% /dev/shm
rootfs                 1003436     21892    981544   3% /
/dev/scd0               715592    715592         0 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                  1003436        12   1003424   1% /tmp
/dev/sdb1               995024     16480    978544   2% /media/disk


From the live cd

Code:

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo df
bash: ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ Filesystem           1K-blocks      Used Available Use% Mounted on
bash: Filesystem: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
bash: tmpfs: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
bash: tmpfs: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436         0   1003436   0% /lib/init/rw
bash: tmpfs: command not found
ubuntu@ubuntu:~$ varrun                 1003436        84   1003352   1% /var/run
bash: varrun: command not found
ubuntu@ubuntu:~$ varlock                1003436         0   1003436   0% /var/lock
bash: varlock: command not found
ubuntu@ubuntu:~$ udev                   1003436      2856   1000580   1% /dev
bash: udev: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436       104   1003332   1% /dev/shm
bash: tmpfs: command not found
ubuntu@ubuntu:~$ rootfs                 1003436     21892    981544   3% /
bash: rootfs: command not found
ubuntu@ubuntu:~$ /dev/scd0               715592    715592         0 100% /cdrom
bash: /dev/scd0: Permission denied
ubuntu@ubuntu:~$ /dev/loop0              691712    691712         0 100% /rofs
bash: /dev/loop0: Permission denied
ubuntu@ubuntu:~$ tmpfs                  1003436        12   1003424   1% /tmp
bash: tmpfs: command not found
ubuntu@ubuntu:~$ /dev/sdb1               995024     16480    978544   2% /media/disk
bash: /dev/sdb1: Permission denied
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
bash: ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$


From the drive without the live cd

stevepoulton@stevepoulton-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=c67425dc-c774-4ef9-8be9-b0d47c55e478 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=9d077e0a-cd5f-41ad-9e34-e8e6a9d66095 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
stevepoulton@stevepoulton-desktop:~$



here is the disk info

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d56957a

Device Boot Start End Blocks Id System
/dev/sda1 * 63 965024549 482512243+ 83 Linux
/dev/sda2 965024550 976768064 5871757+ 5 Extended
/dev/sda5 965024613 976768064 5871726 82 Linux swap / Solaris

Disk /dev/sdb: 1019 MB, 1019215872 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1990656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0accb65c

Device Boot Start End Blocks Id System
/dev/sdb1 63 1990655 995296+ e W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
phys=(122, 254, 63) logical=(123, 232, 45)
ubuntu@ubuntu:~$
__________________
Six Saturdays a week for me.
Last edited by lindsay7; 6 Minutes Ago at 01:03 AM.. Reason: more info

---

### Post by boof1988 on 2009-03-23
> **dandnsmith said:**
> I'm not sure that you can reduce an ext3 partition in size.

Please note this website...

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

gparted (on Ubuntu LiveCD) can (in fact) shrink ext3, among many other operations.  The only limiting factor is if you are using a standard Ubuntu install, there may be additional packages needed to give the full functionality to gparted.

The website above indicates the required packages for the extended capabilities of gparted.

---

### Post by Therion on 2009-03-23
You have to shrink the existing partition as step one.
Step two will be the formatting and partitioning of what will be the "unallocated space" after the completion of step one.

Eesh, that's bad even for me...  Let me rephrase that.

Step 1:  Shrink the existing Ext3 partition.  This shrinking will leave you with "unallocated space".
Step 2:  Create and format the new partition in the "unallocated space" created by step 1.

---

### Post by lindsay7 on 2009-03-23
Thanks to all for the help. I downloaded Gparted as an ISO cd and that solved the problem. I could not do this from the Ubuntu live cd.

---

