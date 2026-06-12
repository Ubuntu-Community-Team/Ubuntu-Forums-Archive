---
title: "I might have hosed my installation"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by fantomx11 on 2009-07-16
I was trying to reformat a usb drive I have. The steps I was given were:
use dd to zero out the drive
use mkdosfs to make the usb a fat32 (I want use it on windows computers as well)

on the first step I got a little hasty and forgot to change the path to my usb stick and it started to zero out my primary hard drive. I realized what I'd done and stopped it before it finished, but some damage had already been done. I now have to boot from my usb stick (glad I kept that around), but once I'm booted up I can see some of the file system on my hard drive, so I know not everything is lost.

In gparted the primary hard drive is listed as unallocated. (which to me is odd because it can still see the files) I had 3 partitions a windows xp partition, a windows recovery console partition, and the ubuntu partition. I can only see the files on the ubuntu partition when I boot with the usb stick.

My questions are, what is the best way of restoring the ability to boot up without losing any more data or programs? (programs would be ok since I can always reinstall them, but the data would be a pain to lose) Also, is there any way to recover the Windows partitions? I haven't used windows since I moved to Ubuntu, but I like to keep it around just in case.

---

### Post by az on 2009-07-16
> **fantomx11 said:**
> I was trying to reformat a usb drive I have. The steps I was given were:
use dd to zero out the drive
...
on the first step I got a little hasty and forgot to change the path to my usb stick and it started to zero out my primary hard drive. I realized what I'd done and stopped it before it finished, but some damage had already been done. 
Did you dd the whole drive, or only the first partition?  (sda or sda1)


> **fantomx11 said:**
> In gparted the primary hard drive is listed as unallocated. (which to me is odd because it can still see the files) I had 3 partitions a windows xp partition, a windows recovery console partition, and the ubuntu partition. I can only see the files on the ubuntu partition when I boot with the usb stick.

To me, this says you zeroed out the drive starting from the first block, and not just the first partition, so that would explain why you have an empty partition table.  How it'S finding the filesystem on there is weird.  I mean, it's no surprise that the filesystem is still there, since you probably haven't touched it, but it's how the OS is finding it that puzzles me.



> **fantomx11 said:**
> My questions are, what is the best way of restoring the ability to boot up without losing any more data or programs? (programs would be ok since I can always reinstall them, but the data would be a pain to lose) Also, is there any way to recover the Windows partitions? I haven't used windows since I moved to Ubuntu, but I like to keep it around just in case.

I don't know how much you zeroed out, but you can try to use Testdisk to recreate your partition table, then use testdisk to try to use the backup boot sector to repair the NTFS filesystem on the first partition:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If that fails (I would bet that it fails) you can recover files from the remaining partition using photorec.  Save the files to another drive.

[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

Use photorec (included with the testdisk package) to recover files.

Then, clean up the very large pile of files you recovered:
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

Good Luck.

---

### Post by fantomx11 on 2009-07-16
> **az said:**
> Did you dd the whole drive, or only the first partition?  (sda or sda1)

I used sda.
> 
To me, this says you zeroed out the drive starting from the first block, and not just the first partition, so that would explain why you have an empty partition table.  How it'S finding the filesystem on there is weird.  I mean, it's no surprise that the filesystem is still there, since you probably haven't touched it, but it's how the OS is finding it that puzzles me.

I thought it was weird that the filesystem was still reachable even though gparted said it was unallocated, as well. Oddly enough, the filesystem says its 68gb (or whatever it says it is), but the unallocated portion in gparted is the whole drive (186gb).
> 
I don't know how much you zeroed out, but you can try to use Testdisk to recreate your partition table, then use testdisk to try to use the backup boot sector to repair the NTFS filesystem on the first partition:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If that fails (I would bet that it fails) you can recover files from the remaining partition using photorec.  Save the files to another drive.

[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

Use photorec (included with the testdisk package) to recover files.

Then, clean up the very large pile of files you recovered:
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

Good Luck.
Thanks for the info. I'll try it as soon as I get home from work. My main concern is the Windows installation and installed programs. *Most* of my files are backed up, but I never got around to making a system backup of Windows and HP didn't include recovery disks in case I needed to reinstall. If it doesn't work then maybe it's time to cut the cord and go full linux.

---

