---
title: "Can't mount partition after Gutsy upgrade"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by sledge.svk on 2007-11-16
Hello
I'm a fairly new Ubuntu user, so my terminology might be off at times, but I'll do my best to describe my problem as clearly as possible so we can get it sorted out quickly and get on with our day. Sounds good, so here goes.
Couple of days ago I installed Ubuntu Feisty on my computer and i set it up so it dual booted with Vista which I had already installed. I fiddled around with it for a day or two, setting up everything just the way I wanted with tremendous help from this forum. One of the most important things for me was that I could have access to my NTFS windows partitions (two of those, one with windows system files, documents and whatnot, the other with music, movies etc.), and with Feisty I got it going without any problems. I set them up with the Storage Device Manager so they would mount when Ubuntu booted up, and it worked flawlessly. 
Today though, I decided to upgrade to Gutsy and after it started up, only one NTFS partition mounted. I can still see the other partition listed when I click on Places->Computer, but it's icon looks like a cd-rom icon, and double-clicking it causes this error message:
 "Cannot mount volume. Unable to mount the volume 'Storage'." 
Details: $MFTMirr does not match $MFT (record 1). Failed to mount '/dev/sda2': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

This error is what I started getting after I followed some advice on another thread, which used some terminal commands, if I remember correctly it started with 'mount' and had 'force' at the end. Before I did this, the error I was getting after double-clicking the Partition icon was something to do with permission denied, so I checked the partition's properties and found that the owner is 'unknown', whereas the partition which mounts normally has the owner set as 'root'. I find this suspicious, but don't know if it can be the cause of my problem. That's about all  I can say at this point. Bottom line: it was working right up to the point when I upgraded to Gutsy. Any suggestions are appreciated, sorry for the long read.
I'll post some info which is usually asked for:

sledge@sledge-ubuntu:~$ sudo fdisk -l
[sudo] password for sledge:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f89822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4293    34482176    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4293       26485   178255872    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           26486       30234    30113842+  83  Linux
/dev/sda4           30235       30401     1341427+   5  Extended
/dev/sda5           30235       30401     1341396   82  Linux swap / Solaris

sledge@sledge-ubuntu:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/sda3
UUID=dc21d1f3-6e3d-4b1d-ab00-72d1fb573b43  /               ext3         defaults,errors=remount-ro     0  1  
# /dev/sda5
UUID=bd4e70d9-a342-4e35-8d5b-417a3abeb70d  none            swap         sw                             0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto                    0  0  
/dev/sda1                                  /media/Windows  ntfs         nls=iso8859-1,umask=000,ro     0  0  
/dev/sda2                                  /media/Storage  ntfs         nls=iso8859-1,users,umask=000  0  0  

sledge@sledge-ubuntu:/etc$ sudo blkid
/dev/sda1: TYPE="ntfs" UUID="86480C7E480C6F6D" LABEL="Windows" 
/dev/sda2: TYPE="ntfs" UUID="DE524688524664FD" LABEL="Storage" 
/dev/sda3: UUID="dc21d1f3-6e3d-4b1d-ab00-72d1fb573b43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bd4e70d9-a342-4e35-8d5b-417a3abeb70d" 

sledge@sledge-ubuntu:/etc$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/Windows type fuseblk (ro,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

sledge@sledge-ubuntu:/etc$ ls -l /media
total 20
lrwxrwxrwx 1 root root     6 2007-11-14 22:19 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-11-14 22:19 cdrom0
drwxrwxrwx 2 root root  4096 2007-11-15 11:30 Storage
drwxrwxrwx 1 root root 12288 2007-11-14 21:38 Windows

Thanks or any help.

---

