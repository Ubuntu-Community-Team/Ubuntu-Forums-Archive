---
title: "How to format a 2tb drive with 4k sectors"
date: 2011-05-09
forum: Hardware
---

### Post by Fracta on 2011-05-09
The subject pretty much says my problem. I can't find too much information on this topic, and many people say different things. I just bought a 2tb seagate drive, ST2000DL003, and I want to get the most out of it.

Here are the things I need to learn how to do:

Select the partition table (gpt probably)
Select the filesystem (ext3)
Tell drive to start at sector 64 (I think) and to use sizes of 4096 bytes. 
Format drive correctly for use.

Thanks for your help in the past. I hope this page will help out lots of other people in the future.

---

### Post by srs5694 on 2011-05-09
You don't *need* to use GPT on a 2 TB disk. MBR's limit is 2 TiB (2^32 sectors x 512 bytes per sector), but 2 TB (2 x 10^12) is less than this. That said, I gather from posts here that Ubuntu's installer switches from MBR to GPT as the default partitioning system somewhere between 1 TB and 2 TB. Also, GPT does offer some advantages over MBR, even on disks much smaller than 2 TIB. There's no distinction between primary, extended, and logical partitions, for instance.

If you want to force use of one system or the other, you should partition the disk before running the Ubuntu installer. You can use GParted; use Device -> Create Partition Table, click Advanced, and select "msdos" for MBR or "gpt" for GPT. Alternatively, use fdisk to create an MBR table or gdisk (you'll have to install it by doing "sudo apt-get install gdisk") to create a GPT.

If you use GPT, you should be sure to create a [BIOS Boot Partition.](http://replay.web.archive.org/20090613031004/http://grub.enbug.org/BIOS_Boot_Partition) If you don't, you might run into GRUB problems -- although you might also get lucky and encounter no problems. The GPT can be as small as 32 KiB, but 1 MiB is a good size, given typical modern alignment. Set its "bios_grub" flag using GParted or parted; or give it a type code of EF02 in gdisk.

If you use a recent version of GParted, GNU Parted, or gdisk, the tool will create partitions that align on 1 MiB boundaries by default, which will provide optimal performance. To be sure, use a tool that shows partition start points in sectors and ensure that every partition begins on a sector value that's divisible by 8. For instance, in gdisk:

```
$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2E8FE240-FC7A-0294-7068-8EB94CBF4005
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 6 sectors (3.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40             439   200.0 KiB   EF02  BIOS boot partition
   2             440          410039   200.0 MiB   EF00  EFI System
   3          410040          819639   200.0 MiB   0700  Linux /boot (unused)
   4          819640         1229239   200.0 MiB   0700  Linux /boot (unused)
   5         1229240      1953525134   930.9 GiB   8E00  Linux LVM

```

Every one of those partitions' start points is divisible by 8 (yielding a whole number when divided by 8), so all the partitions are properly aligned.

One exception: If you use MBR, you do *not* need to align your extended partition, if you use one, in this way; but you *do* need to align the logical partitions it contains to 8-sector boundaries. (You must also align primary partitions in this way.)

FWIW, I'd probably use ext4fs or XFS on bigger partitions; they perform a bit better than ext3fs on large drives. I'd use ext2fs on a /boot partition, though, if you use one. If you install Linux to this drive, I recommend creating a ~20 GiB root (/) partition, a swap partition of 1-2x your RAM size, and the rest as one or more data partitions (probably /home, if this will be a desktop system).

---

### Post by Fracta on 2011-05-10
Firstly, "create a [BIOS Boot Partition.]("http://replay.web.archive.org/20090613031004/http://grub.enbug.org/BIOS_Boot_Partition")" Is this for booting from the drive? It will only ever be used for storing files and will only ever be accessed by linux OSes.
Secondly, I will not be partitioning the drive. Should I still use ext4?
This is essentially the simplest formatting you can do. Just one partition, ext3/4, never booting from it, with 4k sectors.
Thank you for your fast reply!
No other forums I use are as helpful

---

### Post by srs5694 on 2011-05-10
If the disk isn't to be used as a boot disk, then you don't need a BIOS Boot Partition; however, creating one won't do any harm (it'll just consume ~1MiB of disk space, which is trivial on a 2 TB drive).

You *should* partition the drive, even if you just create one partition. Although it's possible to place a filesystem directly on an unpartitioned drive, this is an unusual configuration that could confuse some disk utilities, potentially leading to data loss if you happen to run the wrong tool. (I know of no specific utilities that I know will have this effect, but there are a *lot* of disk utilities out there, and I'm not willing to wager that there are none with bugs that would damage an unpartitioned disk.) Also, if you partition the disk now, you'll be able to resize the partition in the future should you need to -- say, if you must start using the disk as a boot disk. If you just drop a raw filesystem on it, this won't be possible, so you'd need to back up everything, partition the disk, and restore your data.

Note that not partitioning the disk is different from partitioning it with just one partition. A 1-partition disk still has a partition table (MBR, GPT, or something else). If you don't partition the disk, this vital data structure won't exist and shoehorning it onto the disk will be difficult or impossible. If you create a 1-partition disk, of course, you must ensure that the one partition you create is properly aligned, as I described earlier.

---

### Post by Fracta on 2011-05-10
Ah thank you. By not partitioning it, I meant there would only be one partition. I can see I am probably going to have to use command line tools to do this. I don't see an option in gparted to choose the start sector. 
Also, how do I choose alignment? And is 1MiB optimum for my drive? What is alignment and how does that relate to sectors?
Do you have any links on this subject so I can learn more? I want to get it right first time because I have a LOT of data on disk that I only want to copy over once.
Thanks!

---

### Post by srs5694 on 2011-05-11
Alignment in this context just refers to the sector on which the partition begins, and whether it's divisible by some number -- the cylinder size (for cylinder alignment), a 1 MiB (2048-sector) value, etc. An Advanced Format drive requires 4 KiB (8-sector) alignment, so as I wrote in this thread's post #2, just be sure that every partition begins on a value that's divisible by 8 and you'll be fine. Since 2048 is divisible by 8, the new default of 1 MiB alignment works fine. The only drawback to starting a single-partition disk's partition on sector 2048 vs., say, sector 64, is that you lose those 1984 sectors' storage. That's only 992 KiB, which is absolutely trivial, so I wouldn't worry about it.

I wrote [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks over a year ago on this topic. It's still applicable, although the partitioning tools have become friendlier to Advanced Format disks since then.

---

### Post by Fracta on 2011-06-05
Now that I finally have internet again and have had resources to get me through this, I have finally finished formatting my drive. Please let me know if this is correct so I can mark the thread as solved for everyone else.

I used a combination of gparted, parted, and gdisk.

Using gparted first (from memory) I made the drive gpt.

Then I started parted, changed units to sectors, and made the bios partition. It is not formatted with a filesystem.

Then I used gdisk -l to show me how many sectors remained and trimmed it down til it was divisible by 8 and made the data partition. 

Then I used gparted to format the partition as ext4.

now my gdisk shows:

```
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): 316CE1C4-D38F-4231-A1EA-4BC824A201CB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 12 sectors (6.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40             439   200.0 KiB   EF02  BIOS boot partition
   2             440      3907029128   1.8 TiB     0700  primary

```

I couldn't get it to show me "Partition will be aligned on 8-sector boundaries" like you did, but does that matter?

---

### Post by srs5694 on 2011-06-06
What you've got looks fine -- both 40 and 440 are divisible by 8. 

The lack of a "Partitions will be aligned on 8-sector boundaries" message has to do with the version of gdisk you used -- 0.5.1 is ancient! (Thankfully, Ubuntu 11.04 ships with something more recent.)

---

