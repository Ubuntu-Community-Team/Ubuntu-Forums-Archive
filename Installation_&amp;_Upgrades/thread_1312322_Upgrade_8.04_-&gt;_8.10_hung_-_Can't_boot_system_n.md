---
title: "Upgrade 8.04 -&gt; 8.10 hung - Can't boot system now"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Robb.Pryor on 2009-11-03
I just tried to upgrade from 8.04 to 8.10 on my Dell Inspiron 8100.  The upgrade hung in the final minutes of installing the software, during "configuring hal".  Now, I can't boot from 8.10 (I'm getting a "kernal panic", something about not finding root?) and my 8.04 installation appears to be messed up as well.  It has no wire internet connection.  How can I recover from this to complete the upgrade?

---

### Post by hal10000 on 2009-11-03
boot from a live-cd (ubuntu, knoppix or similar), then open a terminal window and post the output of
```
 sudo fdisk -l
```
then mount your ubuntu system partition (if it is not already mounted)
```
sudo mount /dev/sdaX /mnt
```
(/dev/sdaX is the partition where your ubuntu system is installed)

and post the output of 
```
cat /mnt/etc/fstab
```
and 
```
cat /mnt/etc/mtab
```

once this is done, we can go further.

---

### Post by Robb.Pryor on 2009-11-03
Hi hal10000,

Thanks for the response.  Here's the info from the commands you requested:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7479d747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        4823    38612227+   7  HPFS/NTFS
/dev/sda3            4824        9729    39407445    5  Extended
/dev/sda5            4824        9589    38282863+  83  Linux
/dev/sda6            9590        9729     1124518+  82  Linux swap / Solaris

ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0ec37a90-a2e6-40c1-82ab-945168f1b5cf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9e7592c7-d049-4bcf-9177-f8914796e7d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

ubuntu@ubuntu:~$ cat /mnt/etc/mtab
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

---

### Post by hal10000 on 2009-11-03
Here are the steps i recommend:
1.) Boot your live-cd.

2.) mount your ubuntu partition to /mnt:
```

sudo mount /dev/sda5 /mnt

```

3.) mount all necessary file systems to the right places:
```

sudo -s
mount -o bind /proc /mnt/sda5/proc/
mount -o bind /dev /mnt/sda5/dev/
mount -o bind /sys /mnt/sda5/sys
mount -o bind /lib/init/rw /mnt/lib/init/rw
mount -o bind /var/run /mnt/var/run
mount -o bind /var/lock /mnt/var/lock
mount -o bind /dev/shm /mnt/dev/shm
mount -o bind /dev/pts /mnt/dev/pts
mount -o bind /sys/fs/fuse/connections /mnt/sys/fs/fuse/connections
mount -o bind /proc/sys/fs/binfmt_misc binfmt_misc /mnt/proc/sys/fs/binfmt_misc binfmt_misc

```
(if one of the above mount commands does'nt work, as long as it's not one of /proc /dev or /sys, just go on, i don't know if they are really all necessary)

4.) chroot into the mounted file system:
```

chroot /mnt /bin/bash

```

5.) reconfigure all your packages:
```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg-reconfigure -a

```
this may take some time. If you are asked for some input, you should choose the defaults where pssible (or just type ENTER, but be careful).

6.) If you need to install grub (the boot-manager):
```

sudo apt-get install grub2
sudo cp /proc/mounts /etc/mtab
sudo grub-install /dev/sda

```

7.) quit the  root account and the chroot environment:
```
exit
exit

```

8.) boot your system

9.)enjoy

---

### Post by Robb.Pryor on 2009-11-04
I was unable to get /dev /proc or /sys to mount:

root@ubuntu:~# sudo -s
root@ubuntu:~# mount -o bind /proc /mnt/sda5/proc/
mount: mount point /mnt/sda5/proc/ does not exist
root@ubuntu:~# mount -o bind /dev /mnt/sda5/dev/
mount: mount point /mnt/sda5/dev/ does not exist
root@ubuntu:~# mount -o bind /sys /mnt/sda5/sys
mount: mount point /mnt/sda5/sys does not exist

I thought i might have not mounted the disk, so I tried again:

root@ubuntu:~# exit
exit
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount -o bind /proc /mnt/sda5/proc/
mount: mount point /mnt/sda5/proc/ does not exist
root@ubuntu:~# exit
exit

I thought something might have changed, but no....

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7479d747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        4823    38612227+   7  HPFS/NTFS
/dev/sda3            4824        9729    39407445    5  Extended
/dev/sda5            4824        9589    38282863+  83  Linux
/dev/sda6            9590        9729     1124518+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0ec37a90-a2e6-40c1-82ab-945168f1b5cf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9e7592c7-d049-4bcf-9177-f8914796e7d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
ubuntu@ubuntu:~$ cat /mnt/etc/mtab
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-15-generic/volatile tmpfs rw,mode=0755 0 0
ubuntu@ubuntu:~$ 

I don't know how to proceed from here.  What would you suggest?

---

### Post by hal10000 on 2009-11-06
I'm sorry, but i made a mistake in some of the commands above. CHange the lines:

```

mount -o bind /proc /mnt/sda5/proc/
mount -o bind /dev /mnt/sda5/dev/
mount -o bind /sys /mnt/sda5/sys

```

into
```

mount -o bind /proc /mnt/proc/
mount -o bind /dev /mnt/dev/
mount -o bind /sys /mnt/sys

```

The other lines are (hopefully) correct.

---

