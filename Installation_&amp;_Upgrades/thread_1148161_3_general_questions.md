---
title: "3 general questions"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by ron_jeremy on 2009-05-04
Ok, I'm thinking of installing Ubuntu on a 68GB SCSI disk I have laying around. Once installed, I will slave 2 more hard drives:

#1 - 500GB SATA data disk (data only & no OS files, taken from my Windows 7 pc)
#2 - 500GB SATA unformatted disk (brand new)

My questions are:


[LIST]
[*]after working with (adding files, etc) the data disk that used to be in my Win 7 pc, will the disk still be readable to Windows if I slide it back into my Windows box, or will Ubuntu mess with the file table/structure/etc?
[*]how can I format the brand new disk so that if I move it to over my Windows box I'll be able to read the data? Will I be able to format it NTFS in Ubuntu or does this need to be done from within Windows?
[*]I plan on using the 2 500GB SATA disks as my "Home" storage, where all my pics/movies/music/etc will be stored. How should I partition the SCSI system disk so I don't have my home (user?) storage on it thus creating unecessary duplicates & stuff?
[/LIST]
Thanks for taking the time to read my post :)

---

### Post by Sef on 2009-05-04
> after working with (adding files, etc) the data disk that used to be in my Win 7 pc, will the disk still be readable to Windows if I slide it back into my Windows box, or will Ubuntu mess with the file table/structure/etc?

You can [dual boot ]("http://psychocats.net/Ubuntu")Windows and Ubuntu.  Windows 7 could be like Vista where you need to use its partitioner to partition the hard disk.

> how can I format the brand new disk so that if I move it to over my Windows box I'll be able to read the data? Will I be able to format it NTFS in Ubuntu or does this need to be done from within Windows?

If you format that section as NTFS, windows file system, then download NTFS-3G from Add/Remove.

> I plan on using the 2 500GB SATA disks as my "Home" storage, where all my pics/movies/music/etc will be stored. How should I partition the SCSI system disk so I don't have my home (user?) storage on it thus creating unecessary duplicates & stuff?

You can make that your home partition.

---

