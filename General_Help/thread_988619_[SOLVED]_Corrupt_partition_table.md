---
title: "[SOLVED] Corrupt partition table"
date: 2008-11-20
forum: General Help
---

### Post by Pro-reason on 2008-11-20
There is some sort of problem with my partition table.

My motherboard recently died, and I replaced it.  I took this as an opportunity to do a fresh installation of non-beta, 64-bit Kubuntu Intrepid Ibex.  I then dual-booted into Windows XP, and realised that I had no sound.  I couldn't get the operating system to see the sound card of the new motherboard.  So, I decided to reinstall Windows.  I booted from the Windows CD, deleted the Windows partition, and tried to create a new one in the resulting space.  I'd done this before without problems.  This time, it didn't work.  

[B]I rebooted into Kubuntu in order to use GParted.  To my horror, it reported that the drive in question was completely empty, with no partition!  Then, however, I realised that nothing had been lost.  The drive still contained my swap space, my reiserfs root partition, and my ext3 home partition.  Only the Windows partition was gone, as I had intended.

I've run fsck on the reiserfs and ext3 partition, and a couple of things were fixed, but GParted still reports the drive as unpartitioned.  This means I can't do any partitioning without wiping the drive.[/B]

I thought that reinstalling grub to the MBR might cause the partition table to be regenerated correctly, but grub reports "no such partition".

Any ideas?

---

### Post by taurus on 2008-11-20
I assume you are running Kubuntu from the LiveCD!  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Pro-reason on 2008-11-20
> **taurus said:**
> I assume you are running Kubuntu from the LiveCD!  

No, no.  The drive is perfectly functional.  GRUB presents its list as usual; I am running Kubuntu from the drive right now, and I can access all my files.

It's just that GParted cannot see any partitions.  The GRUB installer also does not work.

In other words, the system works, but these problems mean I cannot make any changes.

Here's the drive in question (sda is fine):

```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132        5317    41656545    7  HPFS/NTFS
/dev/sdb3            5318       19457   113579550    f  W95 Ext'd (LBA)
/dev/sdb4           10418       19457    72613768+  83  Linux
/dev/sdb5            5318       10417    40965687   83  Linux

```

I tried QTParted instead of GParted, and it crashed, saying &#8220;Error: Cannot have overlapping partitions.&#8221;

---

### Post by caljohnsmith on 2008-11-20
> **Pro-reason said:**
> 
```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132        5317    41656545    7  HPFS/NTFS
/dev/sdb3            5318       19457   113579550    f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sdb4           10418       19457    72613768+  83  Linux[/COLOR]
/dev/sdb5            5318       10417    40965687   83  Linux

```
Looks like you definitely have a partition table problem, because sdb4 is inside your sdb3 extended partition, and yet it is labeled as sdb4 which would be a primary partition. How about downloading and running testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you have Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like me to help you reconstruct your partition table.

**If you have Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like me to help you reconstruct your partition table.

---

### Post by lisati on 2008-11-20
One thing I notice from the output from fdisk posted in this thread is that the "bootable" flag seems to be missing...

I had a similar problem on a couple of occasions (see [here]("http://ubuntuforums.org/showthread.php?t=936850")) I can't remember exactly what I did to fix it, but concluded that maybe one of Windows updates did something odd somewhere.

---

### Post by Pro-reason on 2008-11-20
OK, thanks for the tip to use testdisk.  I've recorded a log; here it is attached.

I think I'll go out and buy a new hard drive so I can back stuff up before I make any more repair attempts.

---

### Post by caljohnsmith on 2008-11-21
```

   [COLOR="Red"]P[/COLOR] Linux Swap               0   1  1   130 254 63    2104452
   [COLOR="Red"]*[/COLOR] FAT32 LBA              131   0  1  5316 254 63   83313090 [WINDOWS]
   [COLOR="Red"]L[/COLOR] Linux                 5317   2  1 10416 254 63   81931374 [Kubuntu]
   [COLOR="Red"]L[/COLOR] Linux                10417   1  1 19456 254 63  145227537 [Erin]
```
Fortunately it looks like your partition table should be easy to repair; above is the results for your deep scan, but I've marked the partitions as "P", "*", "L", and "L" as I believe they should be, based on your fdisk output. So just run testdisk again, do the deep scan, and once you get the above results, use the up/down arrow keys to select each partition above and mark each as either P, *, or L as shown above using the right/left arrow keys. Proceed to the next screen, and then choose "write". After that, reboot, and please post the output of:
```
sudo fdisk -l
sudo parted /dev/sdb print
```
If the second command doesn't give any errors and shows your correct partition table, then gparted should also be able to recognize your partitions on sdb just fine. Let me know how it goes or if you run into problems. :)

---

### Post by Pro-reason on 2008-11-22
In the end, I decided to buy a new, 500GB drive.

I connected it, and started to rearrange my data.  I inserted the XP installation CD again in order to complete the installation.  This time, I was careful to make sure I was installing to a drive that had nothing else on it.  I was giving the whole drive to Windows.  I made very sure that I selected the right drive.

Unfortunately, the Windows CD went crazy and destroyed all data on the 500GB drive, after I'd backed everything up onto it for safekeeping while I formatted the other drives.

I've spent all day using MagicRescue to recover fragments of deleted files.

I've just re-installed Kubuntu Intrepid, and I shall now try XP yet again.  This time I'm going to physically disconnect all other drives during the installation.

Thanks for your suggestions.

---

