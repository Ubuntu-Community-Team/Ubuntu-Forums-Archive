---
title: "NTFS Partition's Content Completely Disappeared ! Please help"
date: 2013-08-10
forum: Hardware
---

### Post by medim on 2013-08-10
Sorry if I am asking this question in a wrong place

I have a dual boot laptop (12.04/Win7) I hadn't used win for at least 7-8 months, however for some Visio works I logged in windows and when I come back to ubuntu I found my extended-logical NTFS partition (D:) completely wiped, as if it is formated (only 'system volume information' is there)! I switched to win and it was the same.

I have checked it with 'testdisk' which couldn't find any of my lost data (actually shows nothing as deleted), I was wondering if anyone has had the same problem, or knows what I can do ?

Cheers,

ps. I have already googled this issue, I found out similar problem had happened to people before, but I couldn't find any helpful solutions/answers:
[http://superuser.com/questions/472214/how-to-save-a-ntfs-partition-which-suddenly-became-empty](http://superuser.com/questions/472214/how-to-save-a-ntfs-partition-which-suddenly-became-empty)

---

### Post by Mark Phelps on 2013-08-11
You're really faced with two very different problems, each of which tends to work with a very different solution ...


1) Recovering the partition.

This is not data recovery, per se, but restoring a prior partition table that got replaced. There is more than one copy of a partition table stored on a drive, for just this situation. If you can locate an old copy and restore the partition using that, it will then look like it did when that table got created ... but any changes since then will not be seen.

For Windows filesystem partitions, the Windows utilities typically include the option for recovering the partition. That option hunts for copies of the former partition table and gives you the option of picking one. When there are several, you start with one, select it, your table gets rewritten -- and then you look at your drive to see how well it worked. You might have to go through several selections to get a useful one. This process is not actually changing the data on your drive, it is just replacing the default partition table.

The Minitool Partition Wizard boot CD (free) used to offer the Partition Recovery option but I think they removed it from recent versions. You can try the EASUS Partition Master recovery CD. You have to Google for both, download the ISOs and burn CDs of them.


2) Recovering the data

This is totally unlike the above. When directories and files are created, entries are written to the drive. Even when those files and directories are later removed, their entries remain -- they are just modified so they are no longer seen. Windows Data Recovery utilities know what these entries look like and can restore their original versions. IF the file associated with each entry has not been overwritten, you can get all of it back. Since these utilities do NOT use the partition table, it doesn't matter that you reformatted or repartitioned your drive, as long as you didn't "wipe" it, and the file data was not overwritten.

Recuva is a Windows data recovery app that is free. The better ones (from Runtime Software) cost money. They allow you to install, use the app, and view the results, including the contents of found files, but actual file restore requires buying a license.

---

