---
title: "I think my hard drive is failing"
date: 2018-01-22
forum: Hardware
---

### Post by david_brown on 2018-01-22
Hi,

I have a Ubuntu headless server running on 16.04. The OS is on an ssd and I have several hdd's for data of various make and type. My main drive is a WD Red 3Gb and I think it's got problems and would like to know if I'm thinking along the right lines. I don't want to shell out for a new hdd if I'm not going about checking it the right way.

The symptom is that the drive is put into a read only state meaning I can't copy files to it. I understand that this is done because Ubuntu detects a problem. I unmount it and run fsck. The message I get is "/dev/sdb1 contains a file system with errors. Check forced". I then get messages saying free blocks count wrong - fix? I type y. Next it's Free inodes count wrong - fix? I type y again let it finish and remount the drive. 

At that point I can copy files to it, but it takes forever to copy to, and then it goes into read only state again and copying stops.

I've run smartmontools on the extended offline mode and it says it has completed without error.

I'm still thinking the hdd is the problem - would others agree or are there other checks I should be running before going shopping for a new drive? 

Thanks

---

### Post by TheFu on 2018-01-23
Rather than explaining your interpretation of the commands and results, please post them here, using code tags - Adv Reply (#).  That way you get more eyes who are familiar with the commands, options, and output that can advise.

Try changing the SATA cables.

And be very detail oriented. For example, I doubt you have a "WD Red 3Gb" HDD.  I haven't seen a 3Gb HDD in over 15 yrs.

---

### Post by david_brown on 2018-01-24
Sorry - my mistake! It's a WD Red 3Tb drive. Did they even MAKE a 3Gb one??

The HDD in question is ext4 formatted. If I try to mount the drive as read only using 

```
sudo mount /dev/sdb1 -o remount,rw
```

I get the following error:-


```
mount: cannot remount /dev/sdb1 read-write, is write-protected
```

Running fsck -n /dev/sdb1 gives me the following:-

```
fsck from util-linux 2.27.1e2fsck 1.42.13 (17-May-2015)
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 86114660, i_blocks is 541184, should be 538624.  Fix? no


Inode 86114661, i_blocks is 49152, should be 0.  Fix? no


Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(4421632--4423679) +(17940480--17948671) +(71053312--71061503) +(71346176--71452671) +(71876608--71925759) +(79093760--79098903) +344490046 -(385245184--385253375) -(406211584--406224895) -(406432861--406433180)
Fix? no


Free blocks count wrong for group #11752 (3526, counted=1094).
Fix? no


Free blocks count wrong for group #11753 (18432, counted=0).
Fix? no


Free blocks count wrong for group #11754 (32768, counted=0).
Fix? no


Free blocks count wrong for group #11755 (32768, counted=0).
Fix? no


Free blocks count wrong for group #11756 (32768, counted=884).
Fix? no


Free blocks count wrong for group #12396 (16384, counted=9216).
Fix? no


Free blocks count wrong (191611439, counted=191663664).
Fix? no




/dev/sdb1: ********** WARNING: Filesystem still has errors **********


/dev/sdb1: 14856/183148544 files (1.7% non-contiguous), 540954833/732566272 blocks
```



This is without the -n switch

```
fsck /dev/sdb1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sdb1: recovering journal
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 86114660, i_blocks is 541184, should be 538624.  Fix<y>? yes
Inode 86114661, i_blocks is 49152, should be 0.  Fix<y>? yes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(406211584--406224895) -(406432861--406433180)
Fix<y>? yes
Free blocks count wrong for group #12396 (16384, counted=22528).
Fix<y>? yes
Free blocks count wrong for group #12403 (21091, counted=21411).
Fix<y>? yes
Free blocks count wrong (191499799, counted=191673200).
Fix<y>? yes


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 14856/183148544 files (1.7% non-contiguous), 540893072/732566272 blocks
```

Having done this, it still mounts as read only and I can't copy files using the terminal.

Does this indicate a faulty drive?

Thanks

---

### Post by oldrocker99 on 2018-01-24
The advice about changing the SATA cables is good advice. I had an external USB3 drive fail while I was writing to it, and the problem was with the USB3 cable. I replaced it, and the drive mounted correctly.

---

### Post by TheFu on 2018-01-24
That mount command is missing the target directory/mount point. Also, you say read-only, but used 'rw', which is read-write.

I've never used **fsck -n** - not once. In the old days, I could see why you'd want to know about issues and schedule down time to fix them over a weekend. That just isn't the world anymore.

File system issues are logical and may be physical. Fix all the logical errors. If that doesn't fix everything, then you need to swap cables, and look at failing controllers, bad power, and SMART data from the disk itself.

SMART uses a test-then-report method.  I usually run short-tests manually and schedule log tests monthly during non-busy times.  smartctl.  Looking at 'Reallocated_Sector_Ct|Current_Pending_Sector|Offline_Uncorrectable' from the SMART data is the most useful.  If the reallocated sectors is over 9, I replace the disk. I have 15 yr old disks with 0 reallocated sectors and I've seen 9 month old disks have over 100 reallocated sectors as the failures started impacting things I noticed.

It should go without saying, but if you think there might be a disk issue, having solid, daily, automatic, versioned backups is absolutely critical.   Every disk will fail.  Some give a little warning and others just stop completely suddenly.  SSDs are even worse.

---

### Post by oldfred on 2018-01-24
Sometimes a full fsck works better.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by david_brown on 2018-01-25
Hi, and many thanks for the replies.

It's not a USB drive just to be clear - it's an internal sata drive. And yes, I have two backup sets.

I will change the sata lead tonight, but I have just run the commands in the post above:-


I've unmounted the drive and checked it's not mounted

```

david@ubuntu:~$ cd /media/mainhdd
david@ubuntu:/media/mainhdd$ cd /
david@ubuntu:/$ umount /dev/sdb1
umount: /dev/sdb1: not mounted

```

First command and the response:-

```

david@ubuntu:/$ sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.42.13 (17-May-2015)
/dev/sdb1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes


e2fsck: unable to set superblock flags on /dev/sdb1




/dev/sdb1: ********** WARNING: Filesystem still has errors **********

```

Second command and response:-

```

/dev/sdb1: recovering journal
/dev/sdb1:                                                                      Inode 11665415 has an invalid extent node (blk 46784570, lblk 0)




/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)

```

Running it manually

```

david@ubuntu:/$ sudo e2fsck -C0 -f -v /dev/sdb1
e2fsck 1.42.13 (17-May-2015)
/dev/sdb1: recovering journal
e2fsck: unable to set superblock flags on /dev/sdb1




/dev/sdb1: ********** WARNING: Filesystem still has errors **********

```

Is there any way of fixing this so the drive can operate as read write again, or just get a new one?

Thanks

---

### Post by TheFu on 2018-01-25
Those are all logical checks.  There are methods to recover a superblock. If that fails, I'd wipe the disk and start over.

But the SMART data shows underlying disk issues. Look at that.

Thanks for trying to make code tags.  brackets [] are needed, not GT/LT <> characters.

---

### Post by david_brown on 2018-01-26
Thanks for the replies and sorry 'bout the tags! Noted and will do it right next time.

I've checked the health of the drive with smartmontools and it's coming back as passed. So the decision is that I'm going to check my backups are in order and over the weekend format the drive and see what happens. I'll report back with the outcome.

Cheers

---

### Post by deadflowr on 2018-01-26
Use [noparse]```
 output goes here 
```[/noparse]
not <code> output goes here </code>

---

### Post by TheFu on 2018-01-26
If you aren't absolutely positive about the meaning of the SMART data, it is best to post it. There isn't a standard. Every vendor only has it because the Govt mandated "something" for disks sold to them. They didn't mandate any consistency for what the data is or means.

---

### Post by david_brown on 2018-01-30
Hi again - just checking in with the results.

The drive stopped reading as well as writing so I was just going to bin it and buy new. Just before I did that I thought I'd just change the SATA cable and use a different SATA port on the motherboard. Boot up and the flipping drive works properly - read and write. 

So maybe a lesson for others here - change the cables as advised at the top of the page!

Thanks for all the help and advice.

---

### Post by TheFu on 2018-01-30
Please mark the thread as **solved**, if it is solved. "Thread Tools" at the top. This helps everyone in the community.

---

