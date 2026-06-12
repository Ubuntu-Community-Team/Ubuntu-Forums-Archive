---
title: "Karmic can't find hard drive"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by encrypter on 2009-11-07
Yet another grub2 failure thread. I have 3 drives: 2 ntfs and 1 ext4 with Karmic on it. The problem is that Ubuntu can't see its own drive, both from the main installation and LiveCD. On rebooting, grub loads the menu (very slowly, but that seems normal with this new version of it), I choose the Karmic install after which the white Ubuntu symbol hangs on the screen for a bit and drops me to initramfs with the message about /dev/drives/by-uuid/# not being found. As I've said, LiveCD can't see this particular drive either.

I've tried investigating from the grub prompt and here are some results:

```
sh:grub> ls
(hd0) (hd0,2) (hd0,1) (hd1) (hd1,5) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,5) (hd3,1)
sh:grub> ls (hd0)
Device hd0: Partition table
sh:grub> ls (hd0,1)
Partition hd0,1: Filesystem type ntfs, Label System Reserved, UUID 5c48310c4830e704
sh:grub> ls (hd0,2)
Partition hd0,2: Filesystem type ntfs, UUID da4e35a94e357ef7
sh:grub> ls (hd1)
Device hd1: Partition table
sh:grub> ls (hd1,1)
Partition hd1,1: Filesystem type ext2, Last modification time 2009-11-05 20:31:32 Thursday, UUID e806bd91-af02-4d56-a5f9-6d06eba613de
sh:grub> ls (hd1,5)
Partition hd1,5: Unknown filesystem
sh:grub> ls (hd2)
Device hd2: Partition table
sh:grub> ls (hd2,1)
Partition hd2,1: Filesystem type ntfs, Label Data, UUID a4c8c773c8c741f2
sh:grub> ls (hd3)
Device hd3: Partition table
sh:grub> ls (hd3,1)
Partition hd3,1: Filesystem type ext2, Last modification time 2009-11-05 20:31:32 Thusday, UUID e806bd91-af02-4d56-a5f9-6d06eba613de
sh:grub> ls (hd3,5)
Partition hd3,5: Unknown filesystem
```Judging from this the Linux partitions are on devices hd1 and hd3 (no idea why they are duplicated). I couldn't get the /boot/grub/grub.cfg since less/more apparently don't work from grub and I can't figure out how to copy the output. But since I haven't changed anything I figure it shouldn't be special in any way. It's readable and looks normal, save for one detail: in the Linux menu menu entries and in the header of the file it says

```
set root=hd2,1
```which, according to grub's ls is actually an ntfs partition. The UUID is correct there though. I've tried booting after editing it in the menu to replace hd2,1 with hd1,1 or hd3,1 but that didn't work. I don't know how to edit grub.cfg from grub's prompt so that "set root" statement that's above the menu list is out of my reach. 

Windows, which is on hd0,1 boots fine.

---

