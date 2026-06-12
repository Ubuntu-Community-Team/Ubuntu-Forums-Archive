---
title: "[SOLVED] Where did my Hard Drive go?"
date: 2008-08-23
forum: General Help
---

### Post by ddarsow on 2008-08-23
I am not exactly sure what is going on. My system monitor show 0 free space available on my almost empty 80GB hdd and the drive itself no longer shows in the file system tab (it used to). 

I checked GParted and found that the drive shows up correctly there.

The machine is also taking considerably longer to boot and runs noticeably slower than before.

Since I was not even sure how to ask the appropriate question, I attached a couple screenshots as well as the df output.

Thanks.

df output =

:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                 1037140       112   1037028   1% /var/run
varlock                1037140         0   1037140   0% /var/lock
udev                   1037140        44   1037096   1% /dev
devshm                 1037140        12   1037128   1% /dev/shm
lrm                    1037140     39760    997380   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      74328480  11448392  59134136  17% /home/ddarsow/.gvfs

---

### Post by LateNiteTV on 2008-08-23
please post output of "df -h"

---

### Post by coffeecat on 2008-08-23
> **ddarsow said:**
> I checked GParted and found that the drive shows up correctly there.

Have another look at the screenshot you posted. It is not showing correctly. There are no 'Mountpoint' and 'Label' columns. (Perhaps you don't get a label column if you have no partition labels - I don't know.) There should be values in the 'Used' and 'Unused' columns for sda1 (which I guess is your root partition) and I don't like the look of that black triangle with an exclamation mark which I've never seen before.

I don't know what's happening, but if this was my drive I would assume the worst, that it was failing, and make a backup of all important data asap.

**Edit:** in fact, to make backups, I wouldn't boot up again but instead boot up with the live CD and copy off data using the live environment.

---

### Post by jerome1232 on 2008-08-23
Agreed something isn't right, hopefully that partition just corrupted from a hard reboot and there's nothing wrong with the drive, I would backup data and run fsck on that drive from a live cd.

If you right click on that partition with the black exclamation mark and hit information does it tell you what's it's complaining about?

---

### Post by ddarsow on 2008-08-23
> **LateNiteTV said:**
> please post output of "df -h"

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun               1013M  112K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   40K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       71G   11G   57G  17% /home/ddarsow/.gvfs

---

### Post by ddarsow on 2008-08-23
> **jerome1232 said:**
> Agreed something isn't right, hopefully that partition just corrupted from a hard reboot and there's nothing wrong with the drive, I would backup data and run fsck on that drive from a live cd.

If you right click on that partition with the black exclamation mark and hit information does it tell you what's it's complaining about?

unable to find mount point.
see attached

It seems like the volume is obviously being mounted as I can access the files and it does boot and run?

Also does this fsck output mean anything?:

fsck.ext3: Unable to resolve 'UUID=d10a56f4-efdb-4eb7-8d5b-858c659439f7'

---

### Post by ddarsow on 2008-08-23
still need help with this...any more thoughts?

---

### Post by jerome1232 on 2008-08-23
You have to run fsck from a live cd, it's a disk checking utility

boot into a live cd and run fsck -r /dev/sda for it to check the disk then ask you if you want it to repair errors. **Do not run it on a mounted filesystem**

---

### Post by ddarsow on 2008-08-23
OK, I booted the Live CD and ran fsck (sudo fsck -r /dev/sda). This is what I got:

"Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?"

I also checked the drive properties and a screenshot is attached. I do not know if that will be of any use or not, but perhaps.

The following information seemed to be helpful for another person who posted a similar problem:
I noticed that the UUID for dev/sda1 is different in the fstab and blkid outputs...

ddarsow@ddarsow-laptop:~$ **sudo fdisk -l**
[sudo] password for ddarsow: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0c12cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

ddarsow@ddarsow-laptop:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d10a56f4-efdb-4eb7-8d5b-858c659439f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c6faeef9-72b6-4d2f-b461-ceb6263f5691 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ddarsow@ddarsow-laptop:~$ **sudo blkid**
/dev/sda1: UUID="8f1045be-5d05-43b3-b277-663b44ad0d91" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c6faeef9-72b6-4d2f-b461-ceb6263f5691" 

ddarsow@ddarsow-laptop:~$ **mount**
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ddarsow/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ddarsow)
ddarsow@ddarsow-laptop:~$

---

### Post by coffeecat on 2008-08-24
> **ddarsow said:**
> I noticed that the UUID for dev/sda1 is different in the fstab and blkid outputs...

That's curious. I would have thought that your system would fail to boot up at all with a wrong UUID for the root partition in fstab. Why not edit fstab from the live CD and put in the correct UUID and see if this cures the strange symptoms you've been getting? It might be a good idea to make a backup copy of the old fstab first just in case.

---

