---
title: "how to remove partitions"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by davidlarg on 2009-06-27
I am new to ubuntu and what to try it out. 

So I installed Windows XP and partitioned half the drive for Windows XP and left the rest un-partitioned with the idea of installing ubuntu there.  

When I installed ubuntu 9.04 the partition changed and the area for ubuntu was too small.  I reinstalled ubuntu and relized there was a slider bar to change the partition size.  I set the partion for ubuntu to be have of my hard drive.  Now my hard drive has 5 partions.  I know one is for windows XP and the rest have something to do with ubuntu. 

How many paritions does ubuntu require?
How can I remove the partions that are not needed?

David
:confused:

---

### Post by merlinus on 2009-06-27
You can use gparted to delete unwanted partitions and assign the freed-up space to others.

First, open a terminal and post results of:

```

sudo fdisk -l

```Then open gparted -- System/Administration/Partition Editor you can install it from Applications/Add/Remove if it is not there) -- and post a screenshot of what it is showing.

Ubuntu needs at least two partitions.  One is the filesystem, /, and the other is /swap.  You can also create a separate /home partition, which will make upgrading to new versions easier.

---

### Post by mikewhatever on 2009-06-27
By default, the installer creates two partitions. You can remove the unneeded ones using Gparted from the repositories.

---

### Post by davidlarg on 2009-06-27
Here is the terminal info:

```

david@david-desktop:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06120611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20915   167999706    7  HPFS/NTFS
/dev/sda2           20916       30401    76196295    5  Extended
/dev/sda5           30076       30379     2441848+  83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris
/dev/sda7           20916       29696    70533319+  83  Linux
/dev/sda8           29697       30075     3044286   82  Linux swap / Solaris

Partition table entries are not in disk order
david@david-desktop:~$ 


```In GParted do I just select the partition and deleted it?

Also I have another un-formated hard drive is there a way to make it so that it can be read from both Windows XP and ubuntu?

Thanks for your help.

David

---

### Post by merlinus on 2009-06-27
You will have to unmount the partitions before you can delete them.  But first we need to figure out which is root.  Run this command:

```

df -h

```

Is your unformatted hdd external or internal?  In any event, you can use gparted to format it as ntfs, which can be read-write for both ubuntu and windows.

---

### Post by davidlarg on 2009-06-27
Here is the terminal output:

```
david@david-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              67G  2.5G   61G   4% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M  108K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  164K 1006M   1% /dev
tmpfs                1006M  484K 1006M   1% /dev/shm
lrm                  1006M  2.2M 1004M   1% /lib/modules/2.6.28-13-generic/volatile
david@david-desktop:~$ 
```

---

### Post by ajgreeny on 2009-06-27
So it looks as if your extended partition sda2 contains all four linux partitions, is that right?  If so I suggest you boot to your ubuntu live CD and use gparted from that.  If you have two different linux installs each with a swap partition, you can delete the install plus the swap you no longer want, but make sure you get the right one.  Incidentally, you do not need to use a separate swap for each linux install you have, they can all share the same one.

As merlinus says, a screenshot of gparted would be helpfull as your partitions are not in numerical order on the disk, and it will make life simpler to be able to see the disk layout; just make sure you know which partition is which install and then we can tell you how best to proceed.

---

### Post by merlinus on 2009-06-27
From df -h it seems linux root is on sda7, no?  If so, sda5 and sda6 can be deleted.

---

### Post by raymondh on 2009-06-27
> **ajgreeny said:**
> So it looks as if your extended partition sda2 contains all four linux partitions, is that right? 

As merlinus says, a screenshot of gparted would be helpfull as your partitions are not in numerical order on the disk, and it will make life simpler to be able to see the disk layout; just make sure you know which partition is which install and then we can tell you how best to proceed.



I Agree ...and to be sure ... a sreenshot will be of great help.

---

### Post by ajgreeny on 2009-06-27
> **davidlarg said:**
> Here is the terminal output:

```
david@david-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              67G  2.5G   61G   4% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M  108K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  164K 1006M   1% /dev
tmpfs                1006M  484K 1006M   1% /dev/shm
lrm                  1006M  2.2M 1004M   1% /lib/modules/2.6.28-13-generic/volatile
david@david-desktop:~$ 
```
OK, so sda7 is your ubuntu install you want to keep and sda8 is your swap (as I say you only need one) so you can delete the sda5 and sda6, by the look of things and then either add the free space to your sda7 by resizing sit, or just make a new ext3 partition to use for storage, or use ntfs if you want both ubuntu and windows to be able to see and use it.

---

### Post by davidlarg on 2009-06-27
Here is an image of GParted:

[ATTACH]119139[/ATTACH]

---

### Post by merlinus on 2009-06-27
sda5 and sda6 can be deleted.  The free space can be added to sda7.  Post back if you want details on how to do that.

Another option after deleting is to shrink sda7 and make space for moving /home there.  It is very large, unless you have lots of data which will have to be backed up and restored should you need to reinstall ubuntu or want to install a newer version in future.

---

### Post by davidlarg on 2009-06-27
When I try to delete sda5 and sda6 I get the following message.

Unable to delete /dev/sda5 
please unmount any logical partitions having a number higher than 5

---

### Post by merlinus on 2009-06-27
Boot from the live cd and run gparted from there.  You cannot do anything with mounted partitions.  Also, you can try clicking on those two (or right-clicking) and select unmount, and then you should be able to delete them.

---

### Post by davidlarg on 2009-06-27
When I removed the two partitions my computer would not boot but gave error 22.

I went ahead and reinstalled Windows XP and partitioned the whole drive for XP.
Then installed ubuntu and partitioned the drive on install.  I did not lose any info for the computer is a new build. 

I am impressed with all the free help you gave.  

Thank you,
David

---

### Post by merlinus on 2009-06-28
Glad it worked out.  When you deleted the partitions, the numbering changed, and that is probably why grub threw up the error.  

For future reference, it could have been fixed, but in any case the fresh install is working, and that is most important.

Post back if you run into any difficulties, and happy ubuntuing.

---

