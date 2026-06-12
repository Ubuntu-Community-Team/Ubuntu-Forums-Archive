---
title: "[SOLVED] Partition problems"
date: 2008-11-02
forum: General Help
---

### Post by wgg on 2008-11-02
When I start GParted I get the following error:

> The kernel is unable to re-read the partitiontables on the following devices:
- /dev/mapper/minotaur-root

When checking the info of this partition I get the following warning:

> e2label: No such file or directory while trying to open /dev/mapper/minotaur-rootp1
Couldn't find valid filesystem superblock.

I'm not having any problems accessing files on this drive, but this message worries me.  I haven't made any changes to my partitions for well over a year, but I did recently have a power outage that forced my computer to reboot unexpectedly.

Does anyone know what my problem might be?

---

### Post by Pro-reason on 2008-11-02
Perhaps you should boot from the live CD and run *fsck* on all your drives.

---

### Post by wgg on 2008-11-03
Thanks for your help, Pro-reason.  I tried that and got the following:

> ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I also tried fsck on the numbered (partitions?) under sda:

> ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 42/62248 files, 49457/248976 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.lvm2pv: not found
fsck: Error 2 while executing fsck.lvm2pv for /dev/sda5


What I don't understand about all this is if there is something wrong with the drive/partitions, why am I able to use it without any problems?

---

### Post by Pro-reason on 2008-11-03
Do this to get info about your drives:

```

sudo fdisk -l
sudo blkid

```

---

### Post by wgg on 2008-11-03
Here's what I got from fdisk -l:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f34ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976   83  Linux
/dev/sda2              32       38913   312319665    5  Extended
/dev/sda5   *          32       38913   312319633+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3767544a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


And from blkid:

> /dev/mapper/minotaur-swap_1: TYPE="swap" UUID="91cf150c-8253-4235-a904-95e1856b57c4" 
/dev/mapper/minotaur-root: UUID="76fd42f8-0655-41bb-9abf-30d21f742493" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="a92b6336-8987-4873-9984-b7b590f49f45" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="65cDYg-vxJf-qHYd-9V3U-8UzM-2Gtt-uGJEoI" TYPE="lvm2pv" 
/dev/sdb1: UUID="5dd70fc7-386c-4f69-91f0-c49cf42c5234" TYPE="ext3" 


---

### Post by easoukenka on 2008-11-04
I have had 2 brand new usb drives and I have always gotten bad superblock messages along with other erros.  Drives on 2 year warranty so I will just see what happens I guess.  

I have  a post at [http://ubuntuforums.org/showthread.php?t=964625](http://ubuntuforums.org/showthread.php?t=964625) no replies yet though

I have run all the scans on it but no luck.  I did backup my partition table just in case.

---

### Post by wgg on 2008-11-06
Can anyone help?

---

### Post by Pro-reason on 2008-11-09
> **wgg said:**
> Here's what I got from fdisk -l:



And from blkid:

There is something very strange about your /dev/sda5.  It is marked as having a “lvm2pv” file system, instead of the more usual “ext3”.  I have never heard of this, and can't find anything on-line.  This is very weird.  Do you know anything about it?

I would back up my files and re-install.

---

### Post by wgg on 2008-11-09
Ahah, that rings a bell.  Back when I first installed Ubuntu (feisty fawn, I think) I had the option to partition my drive using Logic Volume Manager (LVM2).  I didn't understand enough about partitioning (and still don't) so I just choose all the default and/or recommended options.

So, having looked around a bit I've discovered that physical partitioning tools such as gparted, parted, fdisk, etc, can't handle virtual partitions such as the ones created by LVM.

To manage these partitions you need to use LVM tools, such as lvm (command line) or system-config-lvm (graphical user interface).  For anyone wondering these tools can be installed using apt-get or the Synaptic Package Manager.

Voila, problem solved.

---

