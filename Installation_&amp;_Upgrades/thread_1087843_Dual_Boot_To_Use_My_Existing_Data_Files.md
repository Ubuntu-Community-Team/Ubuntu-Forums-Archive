---
title: "Dual Boot To Use My Existing Data Files"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Snappa on 2009-03-05
I want to install the latest Ubuntu onto my hard disk, to dual boot with my existing Win XP.  I have all my data, including Thunderbird, Firefox, and OO profiles, on Drive F, which is an NTFS partition.  I would like to be able to seemlessly use this data from either XP or Ubuntu, slowly moving over to Ubuntu as I gain confidence and experience.

Is this possible ?
Can somebody please recommend the best installation procedure to follow ?  
Will I have to do anything special to achieve my goal ? 
Any other tips ?

Thanks.

---

### Post by Therion on 2009-03-05
Just so I'm so clear...

Single hard drive with your Windows partition/install and a separate partition (F: under Windows) where you're stashing your porn. 

You want to dual-boot XP and Ubuntu on the single drive, keeping the additional partition (aka F:) intact with the idea of migrating it's contents into your Ubuntu applications once you've installed it?

Correct so far?

---

### Post by Snappa on 2009-03-05
You are more or less correct.  Drive F (my data) is physically on a separate drive.  I want to dual-boot XP and Ubuntu on the *other* drive.
I have only ever worked with Windows, so all my data is in this NTFS drive, which I want to keep using from Ubuntu.
Writing this has made me think.  What I have written above is correct.  But, . . . , I will be installing a new, larger, hard drive, which will ultimately contain all 3 partitions, that is, XP, Ubuntu, and Data, ie., I will be reinstalling XP, and all the applications, as well as Ubuntu.  My data *must* be accessible from XP and Ubuntu.
I hope this is not too confusing. 
Your help and advice is very much appreciated.
Thanks.

---

### Post by Therion on 2009-03-05
Okay yeah, I'm following you.

So here's what you wanna do (Readers Digest Version):

Do your backups.
Install Windows.
Install Ubuntu.

You can manually partition the install-drive during the Ubuntu installation to create the shared-data partition or you can go back later and use something like gParted to shrink an existing partition and create the new shared-data partition.  The sticky-wicket, I'm thinking, is going to be getting both Windows and Ubuntu to mount the shared partition.  This should be doable but I might also point out [Explore2FS](http://www.supriyadisw.net/2006/09/how-to-read-ubuntu-partition-on-windows),  an application for Windows that lets you read EXT2/3 from within Windows.

This site has some good information regarding setting up a shared-data partition on a dual-boot system, but I'm not sure how current the information is:

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

Also, what's going to become of the F: drive?  Backups, I suppose.  Good idea.  Dual-drive systems are the ONLY way to fly in my opinion.

---

### Post by Snappa on 2009-03-05
Thanks again Therion.

I've looked at the article you referred to.  Although written in mid 2006, it still uses a FAT32 shared partition.  I have read that in the old days, Linux was not so reliable in reading NTFS, but I had assumed that this had now improved, and a FAT32 partition would no longer be needed. As I have said, I want to be able to read my data from both operating systems, without the nuisance and extra risk of using an extra file system/partition.
What's your take on that ?

---

### Post by Therion on 2009-03-05
NTFS support is now native to Ubuntu.  You can even install a GUI front-end to manage your existing NTFS partitions (ntfs-3g) if you like.  NTFS is also a journaled file system which FAT32 is not.  

In my opinion, NTFS has got it all over FAT32.

---

### Post by Snappa on 2009-03-05
Thanks again Therion.

I've looked at the article you referred to.  Although written in mid 2006, it still uses a FAT32 shared partition.  I have read that in the old days, Linux was not so reliable in reading NTFS, but I had assumed that this had now improved, and a FAT32 partition would no longer be needed. As I have said, I want to be able to read my data from both operating systems, without the nuisance and extra risk of using an extra file system/partition.
What's your take on that ?

---

### Post by Snappa on 2009-03-06
Thanks,
Don't know how that double post happened.
I hope to rebuild the PC over the weekend, then I'll start on the Ubuntu install, without the FAT32 partition.  No doubt, I'll be back on the forum soon. ;)

---

