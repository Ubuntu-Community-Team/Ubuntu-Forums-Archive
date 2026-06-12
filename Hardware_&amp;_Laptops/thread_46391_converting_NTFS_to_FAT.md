---
title: "converting NTFS to FAT"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by clumsy1007 on 2005-07-04
Hi,

I've installed Ubuntu 5.04 to dual boot with my Windows XP Service Pack 2. I have two hard drives (200gb and 40gb) with three partitions:

c: 130 gb (ntfs)
k: 60 gb (ntfs)
f: 40 gb (ext3) - although it's not really f: because its my linux drive

*NOTE: the c: and the k: drives are partitions of the same physical hard drive - a 200gb western digital.

So I want to make my k: drive (the second half of my big hard drive) use the FAT format so both Windows and Ubuntu can read from it. Problem is, I don't have a floppy drive - so I can't do the fdisk option many of the threads have suggested. I've also read a lot about how converting between NTFS and FAT is a one way street - and I'm going the wrong way. Is there anything I can do without having to buy Partition Magic? I'd like to avoid third-party software if available.

Also, it's important that whatever I do to the k: drive doesn't effect the c: drive. My c: drive is currently filled to capacity with documents, music, programs, etc that I really really really cant afford to lose.

Thanks for your help!

---

### Post by wolphin on 2005-07-04
Well, as far as I know you can't just convert NTFS to FAT without special tools like Partition Magic...Have you considered reformatting it? You could back up your stuff and then format it, so that you'll be able to read and write to it from both Windows and Linux.

Wolphin

---

### Post by clumsy1007 on 2005-07-04
That's what I want to do - reformat it. 

The drive is currently empty. That is why my c: drive is so filled - I temporarily moved EVERYTHING from the k: drive to the c: drive. Sorry, I guess I wasn't clear - I don't mind losing what's on the k: drive (nothing) - so reformatting it wouldn't be a problem provided that it wouldn't effect my c: drive (currently holding windows and all documents/music) or f: drive (currently holding Ubuntu 5.04)

Problem is, when I went to Administrative Tools -> Computer Management the only option offered for the reformat was NTFS. Is there any way to get this to include FAT? 

This has to be a common problem - I just want to share files with Windows and Ubuntu!

---

### Post by wolphin on 2005-07-04
[QUOTE=clumsy1007]That's what I want to do - reformat it. 

The drive is currently empty. That is why my c: drive is so filled - I temporarily moved EVERYTHING from the k: drive to the c: drive. Sorry, I guess I wasn't clear - I don't mind losing what's on the k: drive (nothing) - so reformatting it wouldn't be a problem provided that it wouldn't effect my c: drive (currently holding windows and all documents/music) or f: drive (currently holding Ubuntu 5.04)

Problem is, when I went to Administrative Tools -> Computer Management the only option offered for the reformat was NTFS. Is there any way to get this to include FAT? 

This has to be a common problem - I just want to share files with Windows and Ubuntu![/QUOTE]
 OK, first post the output of "fdisk -l" from the terminal (that's an L not a 1-one-), and then from there you can find out what drive your k: drive is. Then just go to terminal and type in "mkfs -t vfat /dev/hdxy" , where _x_ and _y_ are what you found out from fdisk. If you are unsure what drive your k: drive is, then please post again. Best of luck,

Wolphin

---

