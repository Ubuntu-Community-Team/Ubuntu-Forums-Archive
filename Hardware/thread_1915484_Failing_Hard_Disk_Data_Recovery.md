---
title: "Failing Hard Disk Data Recovery"
date: 2012-01-26
forum: Hardware
---

### Post by DottM on 2012-01-26
Hi,

I was looking to get some help with a failing hard disk. I regrettably used a single external USB hard drive to hold all my images and documents for some time which has now eventually failed. It was connected to my Windows 7 machine so the drive was NTFS format. 

To try recover the data I have attempted the following steps:

[LIST]
[*]Mounting under ubuntu using live cd with USB connection - Wont Mount - Complaings that it doesnt seem to be a valid NTFS.
[*]Mounting under ubuntu using live cd with hdd removed from casing using SATA connection - Same error
[*]Tried using DD_rescue which has been running over a day now and has generated a file 8.2m but is complaining of error reading block 17378 which seems to be constantly incrementing.
[/LIST]

I have tried taking a copy of the output so far to see if I could mount it in anyway to see if its worth continuing but I cant seem to mount the img file as its complaining of the same errors. 

Ive tried using testdisk and it sees no partition information.

Is there anyway I can have a look at the contents so far so I can get an idea if there is going to be any way to recover this data?

Its a hard lesson to learn but I've ordered a raid 1 nas drive so I wont run into this situation again but its devastating to think how many pictures I will have lost.

Any help would be greatly appreciated.

Thanks
Scott

---

### Post by Mark Phelps on 2012-01-26
IF you have access to an MS Windows PC and can connect the drive to that PC, you can go to Runtime Software and download the trial versions of either RecoverMyFiles or GetDataBack for NTFS.  You have to install them on a Windows PC -- and then run them to see if they can find your Deleted Files.  You have to purchase their product to do actual data recovery.

A similar solution, but free, is Recuva -- also an MS Windows product.

---

