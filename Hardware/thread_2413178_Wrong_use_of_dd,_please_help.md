---
title: "Wrong use of dd, please help"
date: 2019-02-22
forum: Hardware
---

### Post by johndsears on 2019-02-22
I can see I am not the first one, and I doubt I will be the last.  I tried to make a copy of my micro sd card (64gb) onto an external hard drive ( 500Gb)..  A couple of seconds into the dd operation, I had a feeling that it wasnt quite right, so stopped the process.  However, when I look at my hard drive (500gb) it showed only 64gb and the rest as unallocated.

I've tried reading around the subject by various people, using testdisk etc, but I'm a bit stumped as to what to do exactly.  I am fairly hopeful that a substantial amount of my data is still intact on the external  hard drive, but dont want to mess it up further by blundering into a process..  I am definitely a newbie when it comes to linux and computer hardware!

I dont currently have a spare large hard disk to start transferring  stuff onto and am rather hoping that something like increasing partitio size will make all my old data visible again, but the warnings are frightening , in therms of loosing data. 


Any help wouldbe appreciated..  picture of gparteed hard drive attached
Thanks,
John

---

### Post by yancek on 2019-02-22
Have you tried to access the data on sdb1 and if so, how?  You have an exfat (windows) filesystem so is this just a data partition?  You should be able to use GParted to either create a new partition from the unallocated space or to extend sdb1 to the end of the disk.

---

### Post by oldfred on 2019-02-22
Is/was 500GB drive gpt or MBR. gpt has a backup partition table at end of drive.

Whatever size of MMC card is, was what dd would overwrite on drive and it would overwrite partition table and first part of data. Data overwritten will not be recoverable. I expect the exFAT partition is your MMC card's partition table.

What does testdisk show? You may need to know if gpt or MBR(msdos).
       [https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
If deeper search shows any files, immediately use that to backup those files to another drive.

Part of testdisk family is photorec. I have used to to recover some text files. I had to leave run overnight to fully process drive, it only found files by extension and recovered every deleted copy on drive. Some I had saved multiple times since last backup and it found all of them. Took days to compare files to recover most current version.
       
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by johndsears on 2019-02-22
I can see the file structure on sdb1, and a few files.  My guess is that  because I pulled the plug on the transfer, only a few files were  actually transferred.  I can these transfered files using standard  "files" icon at sine ( file explorer?) 
I dont seem to be able to extend the partition.  and I was too scared to create a new one ( without knowing what I was doing)

---

### Post by johndsears on 2019-02-24
Sorry , late reply, weekend got int he way.  and the tesk disk too some time! 
Im rpresuming it is a MBR, as it is an MSdos  drive..

Tesk disk doesnt show me that much on the quick scan ... 

==================================
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              2  10  9  7783 139 36  125009920











Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
exFAT, blocksize=131072, 64 GB / 59 GiB
=============================

Listing files / deeper search only shows the file names that were on the  SD card, not the onew which I am hoping is in the unallocated area.  The same goes for Photorec..  none of the original files can be seen. 

Do I need to change the type  or add a partition?
Thanks !

---

### Post by oldfred on 2019-02-24
I would expect photorec to see entire drive and find files on it.
It seems you are only seeing the first part of drive that is the MMC copy.

Was drive only one partition?
Is found partition in testdisk the full drive or the size of the MMC card?

---

### Post by johndsears on 2019-02-24
origional 500gb HD drive was only one partition  ( as far as I am aware) 
found partition   in test disk is the size of the mmc ( 64gb)

---

### Post by oldfred on 2019-02-25
Then writing the first 64 GB or part wrote the beginning of the drive.
There are some backup structures in drive, but if testdisk does not see them, not sure any way to recover.

But photorec should be able to scan entire 500GB.
What was format of drive, if NTFS then Windows tools may work better.

---

### Post by slow-speed on 2019-02-25
Please clarify; did the original 500GB external drive have anything on it to begin with?

---

### Post by johndsears on 2019-02-25
Thanks!,

Ill try out on a windows machine at the weekend.  Otherwise I guess I will buy a new drive and grep the whole lot..  there must be something there ( I say hopefully) !

---

### Post by johndsears on 2019-02-25
Hi Slow-speed  
Yes.  the 500GB had about 400GB of data on it...  ( maily photos)

---

