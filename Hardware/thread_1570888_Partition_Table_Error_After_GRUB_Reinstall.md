---
title: "Partition Table Error After GRUB Reinstall"
date: 2010-09-08
forum: Hardware
---

### Post by VincentValentine on 2010-09-08
Hi.

This evening I decided to blow away my Windows partition to make my Ubuntu partition bigger (since I don't really use Windows that much). Throughout this process, I pulled to major "don't do"s:

1. I didn't back up my data. I've resized several times before without backing up, and decided that the risk was minimal. I was wrong.

2. I didn't know enough to stop and get help when I got out of my normal range of linux command line operations that have a great impact on system operability.

The Result:

](*,)

I resized the partition successfully. I checked from the LiveCD, and all of my data was there. I attempted to reboot from the partition on sda. I got a nice blinking cursor. I waited. I hoped. Nothing.

My assumption at this point was that through the resize process, I had somehow totally hosed GRUB. So I went about following the GRUB 2 reinstall procedure I have included at the end of this post. I rebooted. Nothing. I booted back into the LiveCD only to run fdisk -l, and be shown that sda2 is my only device (I believe sda2 was present before, but my boot device {e.g. the one with all of my data on it} was sda5). Viewing in Gparted it shows as unallocated space. 

I visited the Ubuntu data recover page ( [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) ) and tried the parted recovery option (which I highly doubt I was doing correctly), and received the message "invalid partition table", an idea that might seem to be reinforced by the fact that nothing is displaying my partitions correctly.

Normally, I would just count it as a loss since I use my computer mostly for internet (and all of my media is on an external), but this particular install had some virtual machines that I put a lot of time into configuring, many email and calendar accounts syncing within evolution, and several extensive "stalker folders" for several new acquaintances :shock: .

If anyone has any ideas for how I can restore a valid partition table and defeat the evil demon overlord, I would be most humbly grateful.

I thank you in advance.

David

(Hopefullly) Helpful Information:

The output of "fdisk -l" on the drive in question:

> ubuntu@ubuntu:~$ sudo fdisk -l
Warning: invalid flag 0x0820 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       14594   117220351+   5  Extended


The GRUB 2 reinstall procedure that I followed:

> Reinstalling GRUB 2 from LiveCD
If you cannot boot from GRUB 2 and need to reinstall it:

* Boot to the 9.10 Karmic LiveCD Desktop.
* Open a terminal - Applications, Accessories, Terminal.
* Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
* If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
* Mount your normal system partition:
Code:

sudo mount /dev/sdXX /mnt

o Note: substitue the correct partition: sda1, sdb5, etc.
o Note: GRUB 2 counts the first drive as "0", but the first partition as "1"
* Only if you have a separate boot partition:
o
Code:

sudo mount /dev/sdYY /mnt/boot

with sdYY being your /boot partition designation.
* Note: If you have any other system partitions such as "/usr" these should also be mounted in a similar manner.
* Mount devices:
Code:

sudo mount --bind /dev/ /mnt/dev

* Chroot into your normal system device:
Code:

sudo chroot /mnt

* Reinstall GRUB 2:
Code:

sudo grub-install /dev/sdX

*
o Note: Substitute the correct device - sda, sdb, etc. Do ''not'' specify a partition number.
* Verify the install:
Code:

sudo grub-install --recheck /dev/sdX

o Note: Substitute the correct device - sda, sdb, etc. Do ''not'' specify a partition number.
* Exit chroot: CTRL-D
* Unmount devices:
Code:

sudo umount /mnt/dev

* If you mounted a separate /boot partition:
Code:

sudo umount /mnt/boot

* Unmount last device:
Code:

sudo umount /mnt

* Reboot. 

Please don't hesitate to ask for anything I neglected to include. :)

---

### Post by srs5694 on 2010-09-08
Your best bet is probably to use [TestDisk,](http://www.cgsecurity.org/wiki/TestDisk) which is a tool that can scan a hard disk for lost partitions and recover them; however, this isn't guaranteed to work.

---

