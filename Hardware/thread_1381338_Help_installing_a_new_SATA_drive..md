---
title: "Help installing a new SATA drive."
date: 2010-01-14
forum: Hardware
---

### Post by Nugar on 2010-01-14
Hi all,

I'm building a new PC. I bought a 1TB disk, but I first physically installed it on my working PC. I want to format it as ext4, but Ubuntu just can't see it (or a least I don't know how to look).

How do I tell Ubuntu that there is a new disk and that I want to format it?

Just to check, I booted into Win XP, something I hadn't done in months and XP as well as the BIOS can see the drive with no problems.

I'm using Ubuntu 9.10 and the drive is a "Seagate Barracuda 7200.12 1 TB 7200RPM SATA 3 GB/s 32 MB Cache 3.5-Inch Internal Hard Drive ST31000528AS-Bare Drive"

Thanks in advance for any help,

---

### Post by oldfred on 2010-01-14
Ubuntu will not see it until it is partitioned/formated. Use gparted either from a liveCD or you can download it. The download version will only let you modify unmounted drives/partitions, but you can use it to view your drives (key symbol says it can not be edited).

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Nugar on 2010-01-14
Thanks oldfred,

What I did before reading your answer was launching gparted from the installed version I already have, but it didn't work. So I booted into windows xp, formated the drive and when rebooting into Ubuntu, gparted saw the disc. I'm currently formatting to ext4.

Thanks again,

---

### Post by gechert on 2010-01-15
I have a similar problem: installed a new 1 TB SATA drive.  Used Clonezilla to clone my old drive and restore to the new one. I have a dual boot Ubuntu and Windows 7 system.  It works, except I can't use the capacity of the new drive.  I use Gparted and it shows 5 partitions, the last one being "Extended" which I believe is the Linux swap partition.  But it is locked and can't be moved or changed - so I can't expand the size of my other partitions.  Any help would be appreciated.:)

---

### Post by oldfred on 2010-01-15
the lock means it is mounted. You normally need to run gparted from the liveCD and usually still have to use swapoff on the swap partition as it will be mounted by the liveCD.

---

### Post by Nugar on 2010-01-15
Well, now for an update. 

I installed the 1tb drive. 
Formatted it as ext3 (for some reason I couldn't format it as ext4.
Copied all the things I need to it from the 320gb ntfs drive
Installed Ubuntu (9.10 64bit) to the 320gb drive, ext4

And now, I can't see the 1tb drive.

I ran System > Administration > Disk Utility and it shows 1000gb hard disk, MBR partition table, 1000gb free, Unallocated space.

I am sure I formatted it, and the info went to the drive, how can I mount it? I can't see it with any other tool that I know of...

More information:

Once n finished installing Ubuntu to the 320gb drive, and tried to reboot, I got a GRUB error. Error 15, IIRC. It said that there was no boot info. I switched the drives' cables and the OS booted from the 320GB, but the 1tb disk won't show.

For the sake of test, I switched the drives again and booted from the livecd and no dice, the 1tb drive still appears as 1000gb unallocated space.

The only thing I can think of is trying to boot from a XP disc and do a fixmbr (IIRC the command)

Thanks again,

---

### Post by Nugar on 2010-01-16
Also, I found this page:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Does this apply in this case?

Cheers,

---

### Post by oldfred on 2010-01-16
IF you do a this does it show the sdb drive?
sudo fdisk -l  (el not 1 or I)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
If it is there can you mount it 
sudo mkdir media/bigdrive
sudo mount -t ext3 /dev/sdb1 /media/bigdrive

Then can you 
df -Th
Shows usage of mounted partitons.

More info on testdisk which may recover data if it is there.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

to permanently mount it edit fstab or use
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by Nugar on 2010-01-16
I'll check as soon as I get to my PC. Right now, under gparted it shows as unallocated space.

But I'll run that command and get back to you.

Cheers,

---

### Post by oldfred on 2010-01-16
gechert it would be better to have started your own thread as it can get confusing on what answer applies where. 

Your problem sounds like you have used all 4 partitions. Fortunately it sounds like you have one extended partition. You can use gparted to expand the extended partition and then add additional partition(s) to use the space available. You have to use the liveCD and turn swap off with a swapoff command as you can not change partitions that are in use. 

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Nugar on 2010-01-16
> **oldfred said:**
> IF you do a this does it show the sdb drive?
sudo fdisk -l  (el not 1 or I)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
If it is there can you mount it 
sudo mkdir media/bigdrive
sudo mount -t ext3 /dev/sdb1 /media/bigdrive

Then can you 
df -Th
Shows usage of mounted partitons.

More info on testdisk which may recover data if it is there.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

to permanently mount it edit fstab or use
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

Hi again, oldfred,

Today has been one of those days when you want to be near your box but just can't due to a lot of family obligations...

Anyway, what I get when I use the command you provide, is this:

```

user@user-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000 GB, 1000202273280 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 

Disk /dev/sdb: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       37433   300680541   83  Linux
/dev/sdb2           37434       38913    11880067    5  Extended
/dev/sdb5           37434       38913    11880067   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.


```

Quite frankly, I have no idea what this means, but I do see the 1tb disk there. How do I know the data is there?

Cheers,

---

### Post by Nugar on 2010-01-17
This issue is almost solved now. 

As suggested by oldfred, I went to: 

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

And ran testdisk.

That repaired the MBR (or the FAT?) and Ubuntu was again able to see the contents of the hard drive.

I copied the contents of the hard drive to the 320gb drive to be on the safe side.

Now I'm having a GRUB problem, but I will open another thread to ask about this.

Thanks to all that helped solve this issue!

---

