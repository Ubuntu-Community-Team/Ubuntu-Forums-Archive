---
title: "New hard drives"
date: 2014-07-12
forum: Hardware
---

### Post by Lappert on 2014-07-12
I've built a box for a new Ubuntu desktop: Asus mother board, Intel Ivybridge CPU, 16 MB DDR3. Boot drives are 2 x SSD-256GB and 2 x WD-2TB. I started with Ubuntu 14.04 Server in order to setup RAID 1 on all 4 drives. Once that was installed, I added Kubuntu desktop on top of the server. Mostly seems to be going OK.

Now I'm trying to add two additional drives from my old Window Vista box. These are 1 & 2 TB drives, both formatted with NTFS, full of data and media (otherwise I would have formatted ext4). Physical installation is OK. But as I boot up, I get the message during POST that says:

Physical Disk
[ID]     [Disk Name]                   [Size]         [Speed]       [Status]
0         HDD WDC WD10EACS      1.00TB        3Gbps         Unconfigured
1         HDD Samsung HD204UI    2.00TB        3Gbps         Unconfigured

So far I have not mounted the drive or modified fstab. I did try a temporary mount command in term - that worked.

But I'm concerned about this message in POST. There are 4 other drives all working. These new drives are sde and sdf. The command lshw shows all six drives.

So is this something that will go away once fstab is modified? Or is there something else going on?

---

### Post by Lappert on 2014-07-12
To add to the mystery, fdisk -l reports...

> Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58946bdb


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63  1953522143   976761040+   6  FAT16


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99b06b4c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT




I had thought both were NTFS as they came right out of a Windows Vista box, but it seems one is FAT16.

And it appears the sde1 drive is "boot" See the asterisk:

> Device Boot Start End Blocks Id System
/dev/sde1 * 63 1953522143 976761040+ 6 FAT16

Is this also an issue needing correction?

Thank you.

---

### Post by yancek on 2014-07-12
Are you using GPT on the computer you are checking the drives with?  fdisk does not report information accurately in that case but usually outputs a warning message to that  effect.  See if you get the same results using gparted.

---

### Post by Lappert on 2014-07-12
I was able to mount the two dives by using blkid and fstab. Now they mount on reboot. (I have not tried gparted - it didn't seem necessary unless I needed to partition)

But I'm still getting the warning at POST when I reboot.

> [COLOR=#000000]Physical Disk[/COLOR]
[COLOR=#000000][ID] [Disk Name] [Size] [Speed] [Status][/COLOR]
[COLOR=#000000]0 HDD WDC WD10EACS 1.00TB 3Gbps Unconfigured[/COLOR]
[COLOR=#000000]1 HDD Samsung HD204UI 2.00TB 3Gbps Unconfigured

So this is still a concern.

While fdisk -l tells me that one of the drives is FAT16

[/COLOR]> Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63  1953522143   976761040+   6  FAT16

and still has a boot flag, whatever that means.

blkid say that both are ntfs

> /dev/sde1: LABEL="Media G" UUID="1810D88810D86DEE" TYPE="ntfs" 
/dev/sdf1: LABEL="Media F" UUID="EA78FC1178FBD9F1" TYPE="ntfs" 



---

### Post by oldfred on 2014-07-12
The boot flag is not used by grub, so that does not matter. Windows has to have a boot flag to know which partition has more Windows boot files in partition boot sector and partition. Since some BIOS need to see a boot flag we usually suggest a boot flag on every hard drive anyway.

I do not think the FAT16 is correct, unless you had originally formatted it on a very old system. And then it may have some corruption. But that it starts at sector 63 does indicate that it is older as that was common with XP and older versions of Ubuntu. Newer partitioned drives start at sector 2048 from both Windows & Linux.

I might see what testdisk shows. In some cases the partition table gets changed but the partition's boot sector will show if NTFS or not.

Or you can quickly run this. My sda1 is NTFS, so partition shows .R.NTFS at beginning:

fred@fred-Precise:~$ sudo dd if=/dev/sda1 count=1 | hexdump -C
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

---

### Post by Lappert on 2014-07-12
Thanks for you reply.

These two drives were never boot drives on my old windows system, and they were all one partition each. They were data drives only. They were on a Vista box and should have been formatted initially as NTFS. I can't imagine how or why the drive could ever have been formatted as FAT16 (or even FAT32). The 2.0 TB drive was purchased in 2010 and the 1.0TB drive was bought in 2008 (checking my Newegg records). That box might have been XP initially giving cause to the start sector being 63 as you suggest, but it's been Vista for as long as I remember.

Running "[COLOR=#000000]dd if=/dev/sda1 count=1 | hexdump -C[/COLOR]", both drives show .R.NTFS -- I assume that's what you were looking for.

I just assumed it was NTFS when I modified fstab, and it seems to be working fine.

However Testdisk reports:

> Disk /dev/sde - 1000 GB / 931 GiB - CHS 121601 255 63Current partition structure:
     Partition                  Start        End    Size in sectors


Invalid FAT boot sector
 1 * FAT16 >32M               0   1  1 121601  32 63 1953522081
 1 * FAT16 >32M               0   1  1 121601  32 63 1953522081

Disk /dev/sde - 1000 GB / 931 GiB - CHS 121601 255 63


Warning: the current number of heads per cylinder is 255
but the correct value may be 32.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

Disk /dev/sde - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0   1  1 121601 254 63 1953536067 [Media G]




Disk /dev/sde - 1000 GB / 931 GiB - CHS 121601 255 63
Analyse cylinder   417/121600: 00%


Warning: number of heads/cylinder mismatches 16 (NTFS) != 255 (HD)
  HPFS - NTFS              0   1  1 121601  32 63 1953522081 [Media G]


So it looks like there are some inconsistencies in sde (I have yet to try sdf). ALthough the drive seems to mount OK and the data is there, do you think it would be prudent to offload the data to another drive, repartition and reformat? If that seems wise, now is the time to do it.

---

### Post by Lappert on 2014-07-12
Performing Testdisk on sdf...

Disk /dev/sdf - 2000 GB / 1863 GiB - CHS 243201 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


 1 P HPFS - NTFS              0  32 33 243201  45 44 3907024896 [Media F]
No partition is bootable

Disk /dev/sdf - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33 243201  45 44 3907024896 [Media F]




I don't see any error messages on sdf

---

### Post by oldfred on 2014-07-12
At least two entries determine format, partition table shown by fdisk or parted and PBR. Since PBR is NTFS you need to update partition table as many tools just read partition table not PBR.

sudo parted -l

If still FAT16, you can use disks to just change partition type to NTFS or type 07. Do not reformat. We want to just change partition table entry.

You can also use sfdisk.

 change sdb7 to type 83 - note extra space in device entry. See man sfdisk for more info.
sudo sfdisk --change-id /dev/sdb 7 83

Yours should then be? 

 change sde1 to type 07
sudo sfdisk --change-id /dev/sde 1 07

---

### Post by Lappert on 2014-07-12
As much as I appreciate your help here, you've lost me.

What is PBR? I can't find any reference to it or even on google.

Is parted the same thing as gparted?

Here is parted -l (for the two recent drives) according to this both are NTFS

> Model: ATA WDC WD10EACS-00Z (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs         boot

> Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs

Wouldn't it be easier and safer to just re-partition and reformat the drive instead of fooling around with something like sfdisk ... territory I really know very little about.

---

### Post by SuperFreak on 2014-07-12
Partition by Range (PBR) ?

---

### Post by oldfred on 2014-07-12
PBR - Partition boot record (sector) or boot sector (BS) which is identical to a MBR in structure but for a partition. It is always the first sector of a partition with MBR(msdos) partitioning. I think gpt is similar. Windows has more boot code in the boot area and the partition part is used for logical partitions. Generally only the one chain entry to next logical partition.

       Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

How did you get a RAID setting on the partition for 2TB drive? That would only be correct if drive is part of RAID set. Did you turn on RAID in BIOS at some point. That can leave RAID meta-data on drive and cause all sorts of issues as if drive is RAID standard partition tools will not work. Either RAID meta-data has to be removed or mounted as part of RAID if really RAID.

Again if really just NTFS change to type 07 with disks or sfdisk command line.

      
 Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Lappert on 2014-07-13
Thanks for the explanation of the PBR.

> [COLOR=#000000]How did you get a RAID setting on the partition for 2TB drive? That would only be correct if drive is part of RAID set. Did you turn on RAID in BIOS at some point. That can leave RAID meta-data on drive and cause all sorts of issues as if drive is RAID standard partition tools will not work. Either RAID meta-data has to be removed or mounted as part of RAID if really RAID.[/COLOR]

Perhaps an explanation is in order. There are six physical disks as of now.

sda and sdb are both 256GB SSD set up as RAID 1 (with about a 17 GB swap partition).

sdc and sdd are both WD Black 2.0 TB drives, also set up as RAID 1 (the entire disk is one partition).

I initially installed Ubuntu Server in order to get the RAID. The documentation for that is _seriously_ wanting and inconsistent, but I got it done.
After that I added Kubuntu Desktop, which worked seamlessly.

Just to help me understand, are you saying standard partition tools (like parted or gparted) will not work on Raid drives?

The last two disks, sde and sdf are the subject of this thread. These are _**not**_ RAID, contain different data and came from my old Vista box. That explains why they are NTFS.

> [COLOR=#000000]Again if really just NTFS change to type 07 with disks or sfdisk command line.[/COLOR]

This is where I get lost ... and why I though it might be safer to just re-partition and reformat the SDE disk. (Is there a utility called "disks"?) For me, venturing into utilities like sfdisk could be dangerous.

---

### Post by oldfred on 2014-07-13
Disks is a gui tool in Ubuntu, not sure what Kubuntu has. In 12.04 it was Disk Utility and has fewer functions.

I did see somewhere that gparted was going to add either LVM or RAID to its capability, but do not think any versions with Ubuntu have that capability. Always best to use the RAID tools for that.
But for the drives that are not part of the RAID you should still be able to use gparted.
The new Disks does some gparted type things, but I have seen some have issues. I prefer gparted for partitioning and Disks just for minor edits if necessary.

Second screenshot shows the edit partition type entry at bottom right in Disk Utility. Disks may be a bit different, but I am in my 12.04 currently.

---

### Post by Lappert on 2014-07-13
Again, thank you.

But the question I still have is wouldn't it be easier/safer just to re-partition and reformat the disk in question (the 1 TB that is reporting FAT16) instead of playing with apps like sfdisk where I could easily make a huge mistake. I do have all the data on the disk backed up elsewhere.

In time I might learn all these apps, but a lot of this stuff is still Greek to me.

Also, I'm still concerned about the warning that started this thread. Even before I get to Grup on boot-up, I'm getting

> [COLOR=#000000]Physical Disk[/COLOR]
[COLOR=#000000][ID] [Disk Name] [Size] [Speed] [Status][/COLOR]
[COLOR=#000000]0 HDD WDC WD10EACS 1.00TB 3Gbps Unconfigured[/COLOR]
[COLOR=#000000]1 HDD Samsung HD204UI 2.00TB 3Gbps Unconfigured[/COLOR]

Is there anything I can do to get rid of this? Or does this mean there's a problem somewhere?

---

### Post by oldfred on 2014-07-13
If you have everything well backed up and do not have to worry then reformatting should be fine. I would also convert to gpt partitioning and include an efi partition at beginning of drive in case later you want to add an install to that drive for testing or emergency boot.

But if reformatting anyway then experimenting and developing a bit of confidence about various commands without worrying about lost data is a way to learn.

Not sure where you are getting that unconfigured from? perhaps it is your UEFI/BIOS saying the are not part of the RAID?

---

### Post by Lappert on 2014-07-14
Thanks, that helps a lot.

---

