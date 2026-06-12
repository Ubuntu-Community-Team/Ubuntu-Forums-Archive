---
title: "cannot mount volume"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by xnszxdotnet on 2007-10-02
I have two drives that I need to mount. They both show up in the gui, but when I try to click on they I get popup...
cannot mount volume
unable to mount the volume
details...
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error...

now I think I have the filesystem as UFS (I pulled the hard drive from my freeNAS system).  I would like to get all my movies and music off the drive before I have to reformat it, if it comes to that. is there a way just to get the info?

---

### Post by vinutux on 2007-10-02
use this cammand on terminal 

sudo fdisk -l


it shows u howmuch partitions on there attached to u r system and wich filesystem

.......................

if ur filesystems are ntfs install a program called ntfs-3g for supporting read and write that file system............................

check it now :lolflag:

---

### Post by kellemes on 2007-10-02
yes. fdisk -l will show partitions and filesystems..
Obviously you need the one formatted as UFS, as far as I know UFS is supported by kernel 2.5+ so you should be able to simply..

sudo mkdir /mnt/ufspartition (you can make something up here)
sudo mount -t ufs /dev/theufspartitioninquestion /mnt/ufspartition

Edit: In order to automount at boot you need to edit /etc/fstab

---

### Post by xnszxdotnet on 2007-10-02
OK, fdisk shows that the two drives that I have stuff on are both freebsd filesystems. how do I mount these drives now?

It also is showing the four other disks (two 500gb and two 750gb drives) that I have hooked up to a pci sata controller card. for those four drives it shows "doesn't contain a valid partition table" I don't have anything on these drives. how can I use these also?

---

### Post by kellemes on 2007-10-03
Can you post the output of fdisk -l please?

---

### Post by xnszxdotnet on 2007-10-03
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38643   310399866   83  Linux
/dev/sda2           38644       38913     2168775    5  Extended
/dev/sda5           38644       38913     2168743+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      484521   244198552+  a5  FreeBSD

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      155061    78150712+  a5  FreeBSD

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table


```

---

### Post by xnszxdotnet on 2007-10-04
I still can't get it to work right even after the the whole...
> 
sudo mkdir /mnt/ufspartition (you can make something up here)
sudo mount -t ufs /dev/theufspartitioninquestion /mnt/ufspartition

I found a mention here 
[http://www.linuxquestions.org/questions/showthread.php?t=191184]("http://www.linuxquestions.org/questions/showthread.php?t=191184")
but i don't know how to check what kernel i'm using. the last thing added to the [http://ufs-linux.sourceforge.net/]("http://ufs-linux.sourceforge.net/") site was in 2004. so I'm guessing that it is already added to the kernel that I'm using. 

please, I need help.

---

### Post by Discov3ry on 2007-10-04
Did you try to mount it in read-only mode?

---

### Post by xnszxdotnet on 2007-10-04
yeah, it just gives me the list of options on how to mount.

---

### Post by Discov3ry on 2007-10-04
If this doesn't work:
# mount -r -t ufs -o ufstype=44bsd /dev/sdb1 /mnt/sdb1

# mount -r -t ufs -o ufstype=44bsd /dev/sdc1 /mnt/sdc1

than get a knoppix live cd and try from it...

As far as using the other drives:

use fdisk or gparted, and create new partitions on them, then format them using your favorite file system (either ext3 or raiserfs etc)

sudo /sbin/fdisk /dev/sd[e,f,g] 
or gparted 

sudo mkfs.reiserfs or mkfs.ext3 /dev/sd[e,f,g]

Add those to fstab and you're good to go.

---

### Post by madeddie on 2007-11-20
I had to use ufstype=ufs2 for a volume created on a FreeBSD 6.* system.

fyi

too bad nautilus doesn't understand the -r -o ufstype=ufs2 mount option line

-- 
edwin

---

