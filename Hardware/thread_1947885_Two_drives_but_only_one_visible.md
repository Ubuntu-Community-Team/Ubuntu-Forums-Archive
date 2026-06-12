---
title: "Two drives but only one visible?"
date: 2012-03-27
forum: Hardware
---

### Post by Chazzer on 2012-03-27
I have a DELL Studio 1737 laptop which I discovered recently has space for a second HDD. Because I have a spare 250Gb disk with Windows installed on it I decided to fit the disk for dual booting. This would be useful because sometimes I need to run Windows.

When I enter the BIOS I can see both disks listed and either one can be selected as the main boot drive. However once the computer is running only the boot drive used by the active OS is visible, whether Ubuntu 11.10 or Windows 7.

I would have hoped that in either case the other disk would be visible so I could access the file structure.

Does anybody know why only one drive shows up and whether it's possible or not to make the other drive visible too?

Many thanks

Chazzer

---

### Post by SemiExpert on 2012-03-27
Windows doesn't read EXT4, but Linux does read and write to FAT32 and NTFS.  To format a second HDD, you can use the Disk Utility in an Ubuntu Live Disc.

---

### Post by Chazzer on 2012-03-27
Thanks for your input. I figured there was a good chance Windows wouldn't be able to read from an EXT4 formatted disk but thought it might be able to 'see' the disk at least. I also thought that Linux would be able to see the NTFS disk and also read from it, as it does on another desktop machine I used to use.

Is there any software required for Linux to properly support NTFS formatted drives?

---

### Post by Yellow Pasque on 2012-03-27
> **Chazzer said:**
> Thanks for your input. I figured there was a good chance Windows wouldn't be able to read from an EXT4 formatted disk but thought it might be able to 'see' the disk at least.

Yes, Windows disk manager should recognize the disk as an unknown (partition, volume?). I would check SATA options in your BIOS. Maybe you need to enable AHCI or something.

---

### Post by ijumpship on 2012-03-27
use this 

sudo lshw -C disk

or this

sudo blkid

The Start at the bottom part of this tutorial  and mount the drive.Use Samba  for the windows to see it

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Remember this though
Ubuntu now recommends to use UUID instead, see the instructions here:[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

