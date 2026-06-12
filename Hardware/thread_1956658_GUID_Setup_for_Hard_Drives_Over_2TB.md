---
title: "GUID Setup for Hard Drives Over 2TB"
date: 2012-04-11
forum: Hardware
---

### Post by imwithid on 2012-04-11
I had recently purchased a 3TB Seagate Barracuda 7200.14 and put it into a Sans Digital enclosure with a USB and eSATA interface. I use the eSATA connection only.

Initially, I had gone with a MBR partition table (unsure whether to go with GUID) but when I had hooked it up to a computer with Windows XP (x64), it would not detect the drive (even though it was partitioned as a 2TB drive with the remainder unused).

I had thought a GUID partition would solve this. When prompted through Windows, I had initialized the disk and converted it to a GPT (GUID) disk. Usually, anything partitioned through Windows would work through Ubuntu. This time, it had not.Something to do with the way Windows set up the GUID disk (from sector 0).

I had then tried to setup a GUID disk through Ubuntu using Disk Utility and GParted, however, I would get error messages (I cannot recall which or why - I was trying anything). Either way, I would be able to get the drive to work in Ubuntu through Disk Utility or GParted but that would render it useless in Windows. Conversely, if I had set up the disk through Disk Manager in Windows, it would not be detected through Ubuntu.

After hours of experimentation, I found gdisk (version 0.8.4) had allowed the disk to properly work in both, however, through USB only in Windows. I had only tried this because I wanted to know if my Patriot Box Office would detect the drive as a GUID 2.73TB partition (which it did).

Cut short, I had manually set up the drive through gdisk. To properly align the drive on 8-sector (512-byte logical, 4096-byte physical) boundaries, I had set the first sector to 128 and left the same amount at the end of the drive. The reason being was that I was unsure whether the MBR is still in use with a GUID partition table (a fall back, thus requiring the first 0-63 sectors for MBR and the next 34 for GUID with a backup at the end of the drive as an option). I chose 128 as an easy number to go by.

Can anyone clarify if this is correct way to go about setting up a GUID hard drive or can it be set to sector 0 as Windows does?

Why does this eSATA problem exist such that I can use this interface through Ubuntu but not Windows? (I didn't get to test the opposite, but I suspect that had I set up the eSATA interface through Windows that it would only work via USB on Ubuntu).

Thanks in advance.

---

### Post by oldfred on 2012-04-11
I thought XP did not work with gpt? Perhaps your 64 version does.

With XP and older versions of Linux, the partition tools used cylinders so drives started at sector 63. With Vista Windows changed to starting at sector 2048. Linux recently changed to also use sector 2048 also, but as you have noticed the real requirement is 8 sector boundries.

Both Windows & grub use the space from the MBR in the first sector for additional code. Grub stores core.img in the sectors after the MBR, Windows hides DRM code & serial numbers in that space. Grub2 has been updated to avoid one of the more popular DRM vendors flexnet in MBR, not sure how they work with gpt.

The author of gdisk & the rodbooks site used to regularly post here as srs5694.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)
srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

I used gparted to create gpt drives for a small 160GB, 16GB flash and my new 64GB SSD. With gparted it defaulted to 2048. I had used an older version of gparted (whatever was with 10.10) on my 160GB drive and back then it started at sector 34 or not on the correct boundary, but I have not tried to change it as it is not critical on that drive.

If drive will be used with a UEFI system in the future you should have an efi partition as the first partition. And if booting with MBR and grub2 you have to have a small 1MB bios_grub partition. 

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

---

### Post by imwithid on 2012-04-11
Thank you, oldfred. The information you had provided is very helpful.

The intent of this drive is storage only. It will never be a (U)EFI boot drive. It will be used for backing up and creating images of laptop drives. I prefer smaller drives (under 1TB) as boot disks.

What I wanted to know is how GUID disks are supposed to be set up. MBR volumes are a breeze (requiring sectors 0-62; partitions start at 63 or 64), however, my understanding of GUID disks is that the first 34 sectors (0-33; first usable sector is 34 or 36) are restricted. I've read of "protective MBR" with a GUID setup and am confused as to what this means under the GUID volume setup. My understanding is that one should reserve an equal number of sectors at the end of the drive to create a back up of the GUID volumme information at the beginning of the drive.

This [link]("http://msdn.microsoft.com/en-us/windows/hardware/gg463524.aspx") makes things confusing.

It may sound silly, however, I want to maximize the space allocated to one partition as it will not be a boot disk and it will not be repartitioned, hence, I want to also minimize the the sector count allocated to the GUID volume information.

As for Windows XP x64, I am able to fully utilize the GUID disk but only via USB. For some reason, Windows does not like the eSATA interface for GUID disks set up with Linux. As far as I have been able to test, Windows will only read GUID disks created by Windows but then Ubuntu fails to read any partition information. Since I use Ubuntu 98% of the time, I've almost given up hope that I can have an eSATA interface through Windows as long as I have some basic read access to this drive.

---

### Post by oldfred on 2012-04-11
You will not see the protective MBR, as that is just the first sector just like MBR and has one partition table entry to tell MBR formating tools that it is a gpt disk.

fdisk prints this:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7ece7ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1   117231407    58615703+  ee  GPT

```

But it really is this:

```
fred@fred-MavericDT:~$ sudo parted /dev/sdd unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10

```

I just used gparted and it defaulted to 2048 and the few sectors at the end I assume is space for the backup partition table. I have not partitioned with gdisk but I think it defaults to 2048, but you could use 40 as the first sector. 

This user seemed to have drive size issues, but he is the only one I have seen issues with. Partition is beyond end of drive or overlaps backup partition table.  He use Disk Utility which I have not seen used either for gpt. Use gparted or gdisk.

[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

---

### Post by imwithid on 2012-04-11
I've spent almost three days on this and I've just found the UEFI GUID specifications [here]("http://www.uefi.org/specs/download/UEFI_2_3_1_Errata_A.zip").

Section 5 clears up almost everything.

It turns out that if the physical block size is larger than 512 (e.g. 4096 bytes), that the MBR (protective) spans physical LBA0 and LBA1 (the first 2x8 logical blocks, as stated in section 5.3.1 subsection a and b) rather than placed in the first two logical sectors within LBA0. This is what I wanted to know.

Further more, if I read correctly, the breakdown is thus:

```
Type				LBA (4096)	Logical (512)
-------				-----		------------------
Protective MBR			0		0-7
GPT Header			1		8-15
GPT Partition Entry Array		2-5		16-47
First usable block		6		48
/\/\Partition(s)/\/\
*Last usable bock		(max(n)-(5 LBA or 40 Logical from end)
*Backup GPT Partition Entry Array (max(n)-((4,1) LBA or (39,8) Logical from end)
*GPT Header			max(n) LBA or (7,0) Logical from end

*Assuming that the first logical block falls on the beginning of a long physical
sector (aligned on logical block nmod8=0).
```


My understanding is that the first usable sector is 48 (or LBA6) and the last is max block n-40 (LBA max n-5).

This set up is for a data disk only. As you mention, *oldfred*, if it is an (U)EFI boot disk, it is prudent to align the drive on 2048 logical (LBA 256) boundaries for "optimal transfer length granularity" (if I understand it correctly, for RAID purposes or for drives with physical sector sizes greater than 4096).

I used gdisk to partition (using the expert mode to zap the disk to ensure complete erasure of previous settings which at times would not relent). I would then change the allocation unit from the defaulted 2048 to 1 so that I could manually and incrementally set my partitions the way I wanted.

If all I have written here is correct, I can now fully utilize the disk right down to the last sector without restricting the features permitted through the UEFI GUID specifications.

Have I missed anything? Am I wrong in my assumptions?

---

### Post by oldfred on 2012-04-11
First time I have seen those details, sounds reasonable.

But I like to have an operating system on every drive. Part of the reasons are here:

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

