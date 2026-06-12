---
title: "Gparted - won't move Ubuntu to the left?"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by msimon1960 on 2009-10-16
I installed Ubuntu in a dual boot with WinXP Pro.

I'm liking Ubuntu 9.04 so much I'd like to allocate more space on the drive for it.

I shrunk the windows partition ok but gparted (live CD) won't move the partition to the left to take up the unallocated portion of the disk.

Any suggestions?

---

### Post by hal10000 on 2009-10-16
post the output of
```
sudo fdisk -l
```
so we can see how your drive is partitioned

---

### Post by ztomic on 2009-10-16
This is probably a situation where the swap partition is still mounted while you are trying to modify the disk. Try **swapoff -a** then moving the partition.

---

### Post by msimon1960 on 2009-10-18
Thank you for helping...I'm booting from the latest Live CD.

sda1 is a small partition containing the installation files for the laptop (Vista - ugh).
sda2 is the Windows system drive
sda3 is the problem partition -- I freed up the space using gparted -- it's not marked 'unallocated'
sda5 is my Ubuntu partition
sda6 is the swap partition.

I'd like to move sda5 into the space into the 'unallocated' area and resize it to use the whole area.

----------------------------------------------------------------

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9cbb9cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  12  Compaq diagnostics
/dev/sda2   *        1021        6119    40957717+   7  HPFS/NTFS
/dev/sda3           12045       14593    20474842+   5  Extended
/dev/sda5           12045       14480    19567138+  83  Linux
/dev/sda6           14482       14593      899608+  82  Linux swap / Solaris

---

### Post by hal10000 on 2009-10-19
/dev/sda3 is not a problem partition, it's the extended partition, which acts as a "container" for /dev/sda5 (Linux System) and /dev/sda6 (linux swap) partitions.

Here comes a small "mini-howto" in patitioning-theory:

Partitions are generally divided in "primary" and "logical" partitions. This is NOT os-specific, it applies to all operation-systems. Linux-specific is only the naming convention for the partitions. In linux (and in other unix-like systems) the **primary ** partitions are named /dev/sda1, /dev/sda2, /dev/sda3 and /dev/sda4.
**logical ** partitions are named /dev/sda5, /dev/sda6, /dev/sda7 ....)
As you can see in your harddisk, /dev/sda1 (Compaq diagnostics), /dev/sda2 (Windows NTFS) and /dev/sda3 (Extended) are primary partitions. 
Extended partitions are always primary. They act as containers for logical partitions and they are used if you need more than four partitions in your system (remember you can only have four primary partitions).
Your /dev/sda5 and /dev/sda6 (Linux system and Linux swap) are logical partitions inside your extended partition (dev/sda3)

You have shrunken your Windows System (/dev/sda2), which is a **primary** partition, and now you have unallocated space behind /dev/sda2. This unallocated space is **outside** of your extended partition and you can not simply move your linux system (/dev/sda5), which is **inside** your extended partition, to make it use of your unallocated space.

You now have the choice between three variants:

1.)
Create a new primary linux partition. Remember that you just have three primary partitions (/dev/sda1, /dev/sda2 and /dev/sda3), so you can have one more primary partition. You could then use this new partition to save your own data on it (your videos, music, images, Documents etc.).
This is the easiest way to make use of your unallocated space and the one i would prefer, because your data is then separated from your system, which is always an advantage.

2.) 
The second choice is to enlarge your whole extended partition (/dev/sda3) to the left, then you can create one or more new logical partitions in the now enlarged extended. You may then also use these new logical partitions as data partitions

3.)
The third choice is to also enlarge your extended to the left and then enlarge your linux system partition (/dev/sda5), but that's not a good idea to do. You would then have a big linux system partition of about 70 GB and in the very most cases it makes no sense to have such a big linux system partition. It's much better to have your system and your data separated, so i recommend to use one of the first two choices.

Post here what you want to do and then we can help you to make use of your new space.

---

### Post by msimon1960 on 2009-10-19
Thank you for the information on how Linux treats partitions.

I was going for option #2 but gPartEd wouldn't let me extend sda3 to the left.

I was then going to move sda6 to the left as well.

I was then going to use the space left at the end to create /home consistent with your option #1 (I wholeheartedly agree that systems and user files should not be on the same partition).

Is this just a flaw in gPartEd or have I missed some subtlety in your explanation?

Thanking you in advance...

Matt.

---

### Post by hal10000 on 2009-10-20
> I was going for option #2 but gPartEd wouldn't let me extend sda3 to the left.
If you booted from an ubuntu live-cd and the live-cd finds a swap space (like yours in /dev/sda6), then it will use this space. Because your /dev/sda6 is seated in the extended partition, the partition program can't make any changes to the extended partition.
So you first have to swapoff:
```
 sudo swapoff /dev/sda6
```
Then you should be able to do the steps again

---

### Post by ajaaskel on 2010-11-03
Thanks, disabling swap (sudo swapoff -a) solved also my problem with moving partition to left !

---

### Post by Ms. Daisy on 2012-10-09
> **ajaaskel said:**
> Thanks, disabling swap ```
**sudo swapoff -a**
``` solved also my problem with moving partition to left !
That part is worth repeating because I didn't find it anywhere else.
```
**sudo swapoff -a**
``` 
is the key.

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

