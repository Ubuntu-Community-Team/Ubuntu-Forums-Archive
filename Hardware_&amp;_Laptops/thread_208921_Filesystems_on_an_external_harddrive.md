---
title: "Filesystems on an external harddrive"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by Peppone on 2006-07-04
I have bought a 500 gb external USB2 harddrive which is NTFS out of the box. I dualboot Dapper and XP on my Thinkpad T41.

Both XP and Dapper find and mount it automatically which is great, but I want write support in both operating systems.

What do you suggest I do?

Writing NTFS is still experimental so that's probably not a very good option.

And the FAT32 4 gb file size limit worries me. Also, from another [thread]("http://www.ubuntuforums.org/showthread.php?t=207685"):
[QUOTE=jgcamp99]I've found fat32, to become corrupt more easily than ntfs and this is when a hdd starts to fail. I'd just assume keeping anything off fat32 for the long haul.[/QUOTE]

If I make it EXT3 then Dapper will be happy. For XP I could use "Ext2 Installable File System for Windows" from [http://www.fs-driver.org/](http://www.fs-driver.org/) but I don't know if it's more stable than the other options. Also, will Windows detect the USB2 drive if it's EXT3?
From the same thread as the quote above
[QUOTE=NiN]fs-driver mounts ext3 as ext2... so always shut down windows properly, or you will have a filesystem check every linux boot.[/QUOTE]

It basically comes down to which is safer; FAT32 or EXT3(2 in Windows)?

---

### Post by tonyr on 2006-07-04
The only real issue I see here is the 4GB file size limit.  If you really expect to have to deal with
file sizes larger than 4G then **ext2/ext3** and **fs-driver** is your only option.  The opinion
expressed in the thread you mentioned about **fat32** reliability is, with all due respect,
one man's opinion.  People have been using **fat32** for a LONG time.  **fs-driver** is
newer/younger and still evolving, but I haven't read anything bad about it. In fact,
everything I have seen says good things about it.  Do more research on your own.

There are issues with external USB drives that you need to be aware of.  Read the
FAQs at [www.fs-driver.com](www.fs-driver.com) .   **ext2/ext3** devices will not be automatically recognized
on the Windows side unless there are Drive Letters assigned to them.  You can do this
with the **IFS** control panel in the Windows Control Panel window.  If you use different
external USB drives with different partition arrangements, you would need to change
the drive letters accordingly.

It is reported that when you unlug an external USB drive from Windows,  the drive
letters to not become unnassigned.  There are workarounds for this at the
fs-driver page.   

Both of these are relatively minor issues.

---

### Post by aysiu on 2006-07-04
I'm with tonyr on this one--FAT32 is the way to go unless you have files that are larger than 4 GB... like DVD images.

Of course, your drive is 500 GB, which is huge! So you could always make a chunk of it Ext3, a chunk NTFS, and a chunk FAT32.

---

