---
title: "Problems with an NTFS Partition."
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by amcg06 on 2007-10-09
I'll start by outlining the setup.

Dual Boot machine with Ubuntu 7.04 and Windows 2000. 

Win2k and Ubuntu on /dev/sdb - 18gb SCSI drive, 9.52gb NTFS partition for Windows, works fine in Windows and fine in Ubuntu (can read files on it perfectly well). Remainder is used by Ubuntu. 

And now the problem:

Second drive, /dev/sda - 160GB ATA drive, 127GB NTFS Partition (thank you very much Windows 2k and your inbuilt inability to recognize the drives full capacity - only rectified post formatting :( ). Remainder of space should be blank. Hard drive was simply added and Windows on the SCSI drive did the formatting. Every partitioning tool I've thrown at it (plenty off the UBCD, Gparted, QTparted, etc, etc) has failed to recognize the NTFS partition. Instead my current readout from GParted is: 7.84GiB ! "Unknown" - Flags: boot & 141.21GiB unallocated. 

Since there is data on that drive, I don't want to touch it until I'm getting an accurate recognition of the NTFS partition and preferably the data in that partition. 

Any help is much appreciated.

---

### Post by skyviannes on 2007-10-09
> **amcg06 said:**
> I'll start by outlining the setup.

Dual Boot machine with Ubuntu 7.04 and Windows 2000. 

Win2k and Ubuntu on /dev/sdb - 18gb SCSI drive, 9.52gb NTFS partition for Windows, works fine in Windows and fine in Ubuntu (can read files on it perfectly well). Remainder is used by Ubuntu. 

And now the problem:

Second drive, /dev/sda - 160GB ATA drive, 127GB NTFS Partition (thank you very much Windows 2k and your inbuilt inability to recognize the drives full capacity - only rectified post formatting :( ). Remainder of space should be blank. Hard drive was simply added and Windows on the SCSI drive did the formatting. Every partitioning tool I've thrown at it (plenty off the UBCD, Gparted, QTparted, etc, etc) has failed to recognize the NTFS partition. Instead my current readout from GParted is: 7.84GiB ! "Unknown" - Flags: boot & 141.21GiB unallocated. 

Since there is data on that drive, I don't want to touch it until I'm getting an accurate recognition of the NTFS partition and preferably the data in that partition. 

Any help is much appreciated.
you should be able to download an ntfs driver, im at a school computer right now so im limited and i can't find a link to it, but try downloading and NTFS driver and see if that will let you accurately recognize that partition.  Not sure what your specific problem is, but this may or may not help.

---

### Post by amcg06 on 2007-10-09
But surely as Ubuntu recognizes the NTFS partition on the SCSI drive, NTFS drivers must be present?

---

### Post by dabl on 2007-10-09
*buntu _reads_ NTFS filesystems natively.  To _write_ to them, you must install the package ntfs-3g.  The /etc/fstab line that mounts such a partition needs to be edited slightly to reflect the "ntfs-3g" filesystem type.


It's a little odd that you identified /dev/sdb as the "first" hdd, and /dev/sda as the "second". Are they sequenced that way in BIOS?  I take you added hdd#2 after Ubuntu was installed, because it would not like to go on a SCSI or SATA drive if an IDE/PATA drive were present in the system.

Setting that aside, I think maybe whatever process you used to "expand" the size of that NTFS partition, post XP formatting, has cause the "funny" results in its reported size.  If you're happy with its performance in Windows, you might be well-advised to just leave it alone.  If it's important to use it in Ubuntu, I think I would (a) back up my data from it, and (b) use GParted to partition it into a couple of partitions within XP's limited size restriction, and then let XP format those to NTFS if that's what you want.

:)

---

### Post by amcg06 on 2007-10-09
> **dabl said:**
> *buntu _reads_ NTFS filesystems natively.  To _write_ to them, you must install the package ntfs-3g.  The /etc/fstab line that mounts such a partition needs to be edited slightly to reflect the "ntfs-3g" filesystem type.


It's a little odd that you identified /dev/sdb as the "first" hdd, and /dev/sda as the "second". Are they sequenced that way in BIOS?  I take you added hdd#2 after Ubuntu was installed, because it would not like to go on a SCSI or SATA drive if an IDE/PATA drive were present in the system.

Setting that aside, I think maybe whatever process you used to "expand" the size of that NTFS partition, post XP formatting, has cause the "funny" results in its reported size.  If you're happy with its performance in Windows, you might be well-advised to just leave it alone.  If it's important to use it in Ubuntu, I think I would (a) back up my data from it, and (b) use GParted to partition it into a couple of partitions within XP's limited size restriction, and then let XP format those to NTFS if that's what you want.

:)

I have no plans to write to the NTFS partitions so that's not a problem. 

Hdd#2 was present before and during the install, there are two drives on the system. An 18gb SCSI drive, on which Ubuntu and Windows 2000 are installed. And a 160gb PATA drive on which a 127gb NTFS partition was setup. I chose to resize my Windows partition and install Ubuntu on the SCSI drive because I had the same problem as now during install with the installer failing to recognize my 127gb NTFS partition on the other drive.

I haven't expanded any NTFS partitions. The only NTFS partition which has been modified is the SCSI drive 18gb partition, which was shrunk to allow me to install Ubuntu. 

Thanks for your help so far. :)

---

### Post by amcg06 on 2007-10-09
Any ideas? I'm thinking it might be something to do with how Windows set up the 127GB partition. Perhaps it didn't enter the right/sufficient data into the MBR. Or am I talking a load of rubbish? :p

---

### Post by dabl on 2007-10-09
No, I think you are on the right track -- I think Win XP has messed up the partition data for that drive, somehow.  I'm just not sure that it is "fixable" as such, for Linux purposes. Win XP seems happy with it, but I'm afraid anything you do to make it work with Linux is going to screw it up for Win XP>  :(

---

### Post by amcg06 on 2007-10-09
Aye you're probably right :(. I might look at some way to alter and correct the MBR in future, but as it's not urgent, I'll leave it for now. Silly Windows.. :(

---

### Post by amcg06 on 2008-01-22
Update on this, I believe now that it is down to a pre 127GB hard drive BIOS version without 48-bit addressing that fails to recognise the drive properly. 

It shows up incorrectly in BIOS and also fails to display the right capacity in numerous UBCD hard drive diagnostics tools. Not due to Windows poor formatting after all.

---

