---
title: "1TB external drive shows up as 2.2TB"
date: 2011-01-08
forum: Hardware
---

### Post by shoryuken on 2011-01-08
Hello,

This isn't really an Ubuntu issue but since the problem started while using Ubuntu and given the wealth of expertise in this forum I thought I consult you good folks here.

I recently had a glitch with my 1TB WD My Book external USB drive which resulted in a panic attempt at trying to recover pictures and music stored on the drive (or spend a significant amount of time in the dog house). The drive started making some clicking noises and would give limited and sporadic access to the data (perhaps similar to click of death that many have reported). After several days of attempts (including 2 freezer sessions for the drive), I was finally able to have access long enough to get almost everything off the drive sing a Windows machine. I tried doing scandisk on windows to see what the problem was and if it was fixable and nothing showed up except that all of a sudden (can't remember exactly how or when) the drive showed  up as a 2.2TB drive with the original 1TB partition plus a 1.2TB unformatted partition which was not formattable. I then went back to my Ubuntu machine to try to figure out why the drive was reporting itself as a 2.2TB Drive.

I know that the drive is really 1TB only drive. I've tried fixing the drive using many approaches. Now I'm not an expert, but after much reading and because of some of the errors reported during formatting attempts were related to possible problems with superblock issues, I tried:
```
sudo mke2fs -n /dev/sdb1
```
 which returns:
```
mke2fs 1.41.12 (17-May-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
67108864 inodes, 268435451 blocks
13421772 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
8192 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

```

no matter which super block backup I try using:
```
sudo e2fsck -b 32768 /dev/sdb1
```

I get the same error:
```
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```


Using GParted or Disk Utility, I can format the entire 2.2TB partition using FAT format or I can split the drive into 2 x 1.1TB partitions and format using ext format but can only format 1 of the two partitions (formatting the second one kills the first 1.1TB partition).

Since I've already recovered all that I could recover this is now a learning exercise for me and a challenge of man vs. machine :) This seems to me like something must have been improperly  duplicated in the drive that makes it present itself as a 2.2TB drive. Is there anyway that I can reset the Drive so that it stops thinking it's a 2.2TB drive? 

I've attached a screen shot of what Disk Utility reports back about the drive.

I've looked at the SMART Data results and 2 things pop up in red:
Relocated Sector Count (Normalized:188; Worst:188; Threshold:140; Value:96 Sectors) and Current Pending Sector Count (Normalized:200; Worst:200; Threshold:0; Value:44 Sectors).

Initiating self-test seems to go nowhere and I've had to cancel it.

I'd appreciate any guidance as to how I could completely reset this drive.

TIA

---

### Post by coffeecat on 2011-01-08
Perhaps the partition table has some bad data. Before attempting to create a new partition table, open a terminal and post the output of:

```
sudo fdisk -lu
```That will tell us what's there now.

Also - I'm a bit concerned about the SMART 'Disk has a few bad sectors' message. But let's look at the partition table first. If it's bad, you can deal with that with Gparted (I can tell you how if you need) and then see what shows up.

---

### Post by psusi on 2011-01-08
Weird, that is one busted drive.  Time to RMA it.

---

### Post by shoryuken on 2011-01-08
> **coffeecat said:**
> Perhaps the partition table has some bad data. Before attempting to create a new partition table, open a terminal and post the output of:

```
sudo fdisk -lu
```That will tell us what's there now.

Also - I'm a bit concerned about the SMART 'Disk has a few bad sectors' message. But let's look at the partition table first. If it's bad, you can deal with that with Gparted (I can tell you how if you need) and then see what shows up.

Thanks coffeecat for the quick reply.
So right after I posted my initial thread, I disconnected the drive and put it aside as I I was preparing to leave the house. As I was about to head out I saw your post and re-connected everything to do what you suggested and the drive showed up again as a 1TB drive :?


Just to show that I'm not crazy I had done "sudo fdisk -l" last night and this is the result I got then:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48b9d15a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         863     6928384   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         863        7719    55068359+   7  HPFS/NTFS
/dev/sda3            7720       14593    55215374+   5  Extended
/dev/sda5            7720        9063    10795648+  83  Linux
/dev/sda6           14307       14593     2305296   82  Linux swap / Solaris
/dev/sda7           11364       14306    23639616   83  Linux
/dev/sda8            9064       11363    18474718+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c697c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      267350  2147482624   83  Linux

```


Here is the result to your suggestion:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48b9d15a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13858815     6928384   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    13858816   123995534    55068359+   7  HPFS/NTFS
/dev/sda3       124005796   234436544    55215374+   5  Extended
/dev/sda5       124005798   145597094    10795648+  83  Linux
/dev/sda6       229825953   234436544     2305296   82  Linux swap / Solaris
/dev/sda7       182546658   229825889    23639616   83  Linux
/dev/sda8       145597158   182546594    18474718+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```


I've also attached a new screen shot of Disk Utility screen.

Thanks again for your help.

Cheers

---

### Post by shoryuken on 2011-01-08
> **psusi said:**
> Weird, that is one busted drive.  Time to RMA it.

:) Can't RMA since I pulled the drive out of the case to try directly connecting it to the computer in the off chance that the problem was the usb to SATA interface.

---

### Post by coffeecat on 2011-01-08
> **shoryuken said:**
> Just to show that I'm not crazy I had done "sudo fdisk -l" last night and this is the result I got then:

Yes, that is weird. I have no logical explanation. :)

Anyway, since you are now getting...

```
Disk /dev/sdb doesn't contain a valid partition table

```I think it's time to create a new partition table. Either use Gparted from the live CD or install Gparted to your hard drive install. Open Gparted (System > Administration) and make sure your 1TB drive is showing in the main window. You don't want to re-create the partition table on your sda drive! :-s From the Device menu > 'Create Partition Table'. The default is a ms-dos/mbr table which is OK. Once it's made the partition table, you might as well use Gparted to create and format a partition. Now, hopefully, you will be able to see how the SMART self-tests go in Disk Utility, and see how the drive behaves over the next few days and weeks.

Good luck!

---

### Post by psusi on 2011-01-08
> **shoryuken said:**
> :) Can't RMA since I pulled the drive out of the case to try directly connecting it to the computer in the off chance that the problem was the usb to SATA interface.

So?  Shove it back in the enclosure and RMA it.  Take a look at the SMART numbers first though.

---

### Post by shoryuken on 2011-01-10
> **psusi said:**
> So?  Shove it back in the enclosure and RMA it.  Take a look at the SMART numbers first though.

It'll be obvious that the case was open. Would they even accept it? 
I guess it doesn't hurt to try. I'll contact WD to find out.

---

### Post by shoryuken on 2011-01-10
> **coffeecat said:**
> Yes, that is weird. I have no logical explanation. :)

Anyway, since you are now getting...

```
Disk /dev/sdb doesn't contain a valid partition table

```I think it's time to create a new partition table. Either use Gparted from the live CD or install Gparted to your hard drive install. Open Gparted (System > Administration) and make sure your 1TB drive is showing in the main window. You don't want to re-create the partition table on your sda drive! :-s From the Device menu > 'Create Partition Table'. The default is a ms-dos/mbr table which is OK. Once it's made the partition table, you might as well use Gparted to create and format a partition. Now, hopefully, you will be able to see how the SMART self-tests go in Disk Utility, and see how the drive behaves over the next few days and weeks.

Good luck!

Thanks again coffeecat,

I did what you suggested and the self test took over 8hrs to complete. The results are as follow:
- 157 bad sectors
- Relocated Sector Count Warning: Normalized 186; Worst 186; Threshold 140; Value 106 Sectors
- Current Pending Sector Counts Warning: Normalized 200; Worst 200; Threshold 0; Value 51 Sectors

Would partitioning the drive be safer than leaving a single 1TB partition?

Cheers

---

### Post by psusi on 2011-01-10
> **shoryuken said:**
> 
- 157 bad sectors
- Relocated Sector Count Warning: Normalized 186; Worst 186; Threshold 140; Value 106 Sectors
- Current Pending Sector Counts Warning: Normalized 200; Worst 200; Threshold 0; Value 51 Sectors


Definitely call WD and tell them the drive is failing and RMA it.

---

