---
title: "Removing one version of Ubuntu"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by kenanton on 2009-05-09
I have a Toshiba laptop which had 8.04 LTS and Vista installed. I upgraded 8.04 to 9.04 internally. Then I did a clean install of Vista in its old partition. After this Grub would not work, so I used my 8.04 install disk. I thought I would then have 8.04 LTS and Vista but now I have 9.04, 8.04 LTS and Vista. At some point I would like to remove either 8.04 or 9.04 and reallocate the disk space and keep Vista as is. What is the easiest way to do this.

Thanks

---

### Post by tommcd on 2009-05-09
> **kenanton said:**
> I have a Toshiba laptop which had 8.04 LTS and Vista installed. I upgraded 8.04 to 9.04 internally. Then I did a clean install of Vista in its old partition. After this Grub would not work, so I used my 8.04 install disk. I thought I would then have 8.04 LTS and Vista but now I have 9.04, 8.04 LTS and Vista.
So after reinstalling Vista, you booted up the 8.04 CD and did a *new install* of 8.04? Is that correct?
> **kenanton said:**
> 
 At some point I would like to remove either 8.04 or 9.04 and reallocate the disk space and keep Vista as is. What is the easiest way to do this.

So you now have 8.04, 9.04, and Vista istalled? And you can boot all three operating systems? Is that correct?

Post the output of:
```
sudo fdisk -l
```
and tell us what partition has 8.04 and what partition has 9.04. Also mention what each partition is for (/home, etc).
Also post the output of:
```
cat /etc/fstab
```
You could use a Parted Magic or GParted live CD to remove the unwanted partition and then merge the free space with another contiguous partition.

---

### Post by kenanton on 2009-05-09
So after reinstalling Vista, you booted up the 8.04 CD and did a new install of 8.04? Is that correct? Yes

So you now have 8.04, 9.04, and Vista istalled? And you can boot all three operating systems? Is that correct? Yes

student@student-desktop:~$ sudo fdisk -l
[sudo] password for student: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff41a76d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9832    77432832    7  HPFS/NTFS
/dev/sda3            9833       19457    77312812+   5  Extended
/dev/sda5            9833       10458     5028313+  83  Linux
/dev/sda6           19060       19457     3196903+  82  Linux swap / Solaris
/dev/sda7           10459       18703    66227931   83  Linux
/dev/sda8           18704       19059     2859538+  82  Linux swap / Solaris

Partition table entries are not in disk order


student@student-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=74c2ae93-40f4-4f3e-bb37-1688e7f9d629 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=af059d07-6600-40f8-8330-32ad67ba7df7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
student@student-desktop:~$ 

Which is better for my needs Parted Magic or GParted live CD?

Thanks again!

---

### Post by kenanton on 2009-05-09
How do I determine which partition has 8.04 and what partition has 9.04?

Thanks again!

---

### Post by tommcd on 2009-05-09
> **kenanton said:**
> How do I determine which partition has 8.04 and what partition has 9.04?

I was hoping you would know what partition each distro was installed to.
Since you don't, boot 9.04 and run:
```
blkid
```
This will produce an output similar to this:
```

bash-3.1# blkid 
/dev/sda1: UUID="420CB81A0CB80B45" TYPE="ntfs" 
/dev/sda2: UUID="48cd7f68-aece-4f72-a380-2a60f87bf677" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="4533b483-1af3-455e-8ef4-9936467fc292" 
/dev/sda5: UUID="54e761dc-3847-4f90-9ea8-5f466c893c0a" TYPE="ext3" 
/dev/sda6: UUID="9d10d416-c356-4b87-907c-2f5e3bc62594" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="1c82c3df-d1de-4d0a-a20c-2321803b4410" TYPE="ext3" 

```
Then compare the UUIDs of the 2 Linux partitions to the UUID for 9.04's root partition in fstab. The UUID that matches the root partition in 9.04's fstab will be 9.04's root partition. The other Linux partition will then be 8.04.

You have some unallocated space at the beginning of your drive as /dev/sda1 for some reason. Do you know what that is?

You have 2 swap partitions. You only need 1.

Assuming you want to keep 9.04, you could then boot up the Parted Magic live CD (my preference, although GParted is fine also) and delete the unwanted 8.04 and the swap that is contiguous with it. Then format the newly created free space as ext3 and use it as a home partition. See this as a guide for creating a separate home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Your other option would be to boot up the 9.04 live CD and do a clean install. Choose manual partitioning, and delete everything except the Vista partition. Then create 3 partitions:
/root (10-12 GB depending on how much space you have)
swap (1GB)
/home (the rest of the drive)

---

### Post by kenanton on 2009-06-14
I am writing this update in the hope that my misadventures might help others.

Before trying any of tommcd's suggestions I wanted to backup the entire hard drive as there were programs on the Vista partitions that I wanted to keep. Thus I burned a CD of "PC Backup Utilities 2008 Free Edition" and stated to clone to an external USB drive. This was horribly slow. After about six hours, it was not half done.  So I stopped.  When I rebooted the computer it went straight into Vista, without loading Grub.

Inspection of the drive using Parted Magic indicated all the partitions described above were still there. I decided to go back to a Vista only system for a while. Thus, I used the instructions given here:[http://vistarewired.com/2007/02/16/h...windows-vista/](http://vistarewired.com/2007/02/16/h...windows-vista/). The result is a hard drive with a 1.46 GB EISA partition and a 147.58 GB NTFS partition.

Who knows what will happen next!

---

