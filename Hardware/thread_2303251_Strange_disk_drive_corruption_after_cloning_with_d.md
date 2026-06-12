---
title: "Strange disk drive corruption after cloning with dd"
date: 2015-11-17
forum: Hardware
---

### Post by spacexion on 2015-11-17
Hi everybody,

This morning I tried to clone a 120GB SSD (a bootable system disk with Ubuntu 12.04)  towards a classic 500GB drive. The 500GB was a brand new, never used and unformatted HGST unit.

I used a very basic dd command, as I was just doing some tests on the fly:

```
[FONT=Consolas]dd if=/dev/sda of=/dev/sdb bs=32M[/FONT]
```

dd just finished without any errors. I then installed the 500GB  destination disk in a laptop and started it.
On system loading, I had a big bad error about X which could not start, but I still was able to operate the system through command line. Also "ls" gave some strange errors (but finally listed the home directory content after some tries) which let  me suppose that nonetheless some errors  occurred during the cloning process. (Actually not a big problem at that moment I thought, as I was just testing....)
I did a reboot and grub was still working but on this second try the system didn't start at all: after grub menu, I just got a blank screen.
I did another reboot and then the disk drive was totally dead, even not recognized in BIOS.

I tested it on another machine (a completely different computer with different SATA cables) and the drive is definitely dead: it spins but BIOS can't see it.

I really have no clue about what happened. Does dd can corrupt a disk at such low level that even BIOS won't recognize it anymore?
Or maybe the drive, even new and freshly unpacked, was faulty on its own from the beginning?

Thanks!

---

### Post by sudodus on 2015-11-17
> **spacexion said:**
> Hi everybody,

This morning I tried to clone a 120GB SSD (a bootable system disk with Ubuntu 12.04)  towards a classic 500GB drive. The 500GB was a brand new, never used and unformatted HGST unit.

I used a very basic dd command, as I was just doing some tests on the fly:

```
[FONT=Consolas]dd if=/dev/sda of=/dev/sdb bs=32M[/FONT]
```

dd just finished without any errors. I then installed the 500GB  destination disk in a laptop and started it.
On system loading, I had a big bad error about X which could not start, but I still was able to operate the system through command line. Also "ls" gave some strange errors (but finally listed the home directory content after some tries) which let  me suppose that nonetheless some errors  occurred during the cloning process. (Actually not a big problem at that moment I thought, as I was just testing....)
I did a reboot and grub was still working but on this second try the system didn't start at all: after grub menu, I just got a blank screen.
I did another reboot and then the disk drive was totally dead, even not recognized in BIOS.

There might be problems if the two drives are using different sector size. It can be checked with

```
sudo parted -l
```

I tested it on another machine (a completely different computer with different SATA cables) and the drive is definitely dead: it spins but BIOS can't see it.

I really have no clue about what happened. Does dd can corrupt a disk at such low level that even BIOS won't recognize it anymore?
Or maybe the drive, even new and freshly unpacked, was faulty on its own from the beginning?

Thanks!

I'm using dd a lot, particularly via shell-scripts (to wrap a safety belt around it). For example, dd is used under the hood in [mkusb](https://help.ubuntu.com/community/mkusb).

dd has ***never*** corrupted a disk for me at such low level that even BIOS won't recognize it anymore. Even if the partition table or a file system is damaged, the drive is still recognized as a mass storage device as /dev/sdx, where x is the drive letter, a, b, c ...

-o-

Drives with an MSDOS partition table can be cloned with dd to a drive with the same size or bigger, and the partitions can be moved to use the whole new drive afterwards. But the GUID partition table (GPT) makes it harder to use the whole target drive if it is bigger than the source drive, because data belonging to the partition table are written behind the end of the last partition. In such cases you should copy manually or with a tool, that first creates a partition table and then copies the content of the partitions.

[Clonezilla](clonezilla.org) is a tool for cloning drives, making compressed images and restoring data. It copies only used blocks, which makes the process faster, particularly when the source drive is far from full with data.

I suspect that the hard disk drive was bad, that it is a hardware defect (mechanical or electronical).

---

### Post by oldfred on 2015-11-17
If grub loads and you get black screen and it is a different computer then it has to do with video drivers.
Have you tried nomodeset?
What video on old and on new system?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

