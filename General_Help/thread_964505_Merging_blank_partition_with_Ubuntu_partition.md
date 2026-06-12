---
title: "Merging blank partition with Ubuntu partition"
date: 2008-10-31
forum: General Help
---

### Post by punjabdasher on 2008-10-31
I am going to install Ubuntu 8.10 on my laptop which has an existing installation of Vista on it. I plan to set up a dual boot of Vista and Ubuntu, as I need to retain functionality of my laptop as I am still learning on how to use Ubuntu for all of my needs. However, in a couple of months I am looking to remove Windows Vista and move my data over to my Ubuntu installation. My question is this: would i be able to merge my previous Vista (now blank) partition with my Ubuntu partition?

---

### Post by punjabdasher on 2008-10-31
bump.. still need help.

---

### Post by Herman on 2008-10-31
Yes, you can delete your Windowws partition and resize Ubuntu to fill the freed space.

I don't know what you mean by 'merge' the partitions. Vista uses the NTFS file system and Ubuntu uses ext3 or any other Linux file system the user wants. I don't think the NTFS file system is compatible with any other file system, so you would need to move the data somewhere else first, before deleting the Windows partition. Then you would resize the Ubuntu partition to fill up the free space.

  If you do that, one problem is the file system blocks of the start of the Ubuntu partition are very slow to move. Although GParted can move them, it takes a long time.
Most people would need to do that because when they install Ubutnu they normally resize Windows from the end and install Ubuntu after it, at the end of the hard drive.

Before you install Ubuntu, if you resize the Windows partition first and then move it to the other end of the hard disk and install Ubuntu in front of Windows, (at the start of the hard disk), you will save time later.
Ubuntu is fast to resize from the other end.

WIth Windows XP it didn't matter where it was located on the hard disk, as long as the partition number didn't get changed. If it did, you had to edit boot.ini to get it to boot again. I don't think Vista cares about the partition number, instead it is tied to the 'disk signature' in the MBR. GRUB doesn't touch the 'disk signature' in the MBR, but if you want, just to make sure, (since you have Vista), you could make a backup of the first 446 bytes of the MBR with a 'dd' command from the Ubuntu Live CD before you install. [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

Good luck, Regards, Herman :)

---

