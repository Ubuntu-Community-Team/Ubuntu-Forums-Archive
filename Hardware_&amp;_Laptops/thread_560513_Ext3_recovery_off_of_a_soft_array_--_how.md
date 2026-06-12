---
title: "Ext3 recovery off of a soft array -- how?"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by tuckie on 2007-09-26
Long story short, my soft raid 5 array decided to drop one of the drives, in the process of trying to figure out why, I nuked one of the five drives.   I am able to get the array back up and running in a degraded state, but its telling me that I have a bad superblock.  If I try to run fsck.ext3 -b 163840 -B 4096 /dev/md0
, I get bunch of warnings like ```
Block bitmap for group 14904 is not in group.  (block 0)
Relocate<y>? cancelled!

Inode bitmap for group 14904 is not in group.  (block 0)
Relocate<y>? cancelled!

```

does this mean my data is hosed?
Is there a way to rebuild the superblock, or is that just the tip of the iceberg?
Is there any software that can recover data from a soft array?

edit: i have yet to actually let fsck run, due to fear of loosing data.  would it be worth while to temporarily get some hard drives to dd 1.5 tb of  the raw data onto?

---

### Post by kidders on 2007-09-28
Hi there,

It's worth checking a few of the basics first. Sorry if this sounds a bit like the fsck equivalent of "Is your printer turned on", but I don't want to jump to any conclusions...[LIST]
[*]Do you really have an Ext3 filesystem?
[*]Are you certain there's a superblock at position 163840?
[*]Is the filesystem block size really 4k?
[*]Is /dev/md0 really the location of your array?[/LIST]The main reason I ask is that this whole thing seems suspicious to me ... a 4-disk RAID 5 array should be well able to tolerate the loss of one component device. Surely a 5-disk array should have even less trouble. I'm having a little difficulty understanding how both your RAID array *and* the filesystem stored on it could both have gotten damaged. Are all your devices the same size?

Anyhow, to answer your questions directly...

*Does this mean my data is hosed?*
It may do, I'm afraid.

[I] Is there a way to rebuild the superblock?
[/I]Not as far as I know. Filesystem superblocks are critical, which is why Ext2, for instance, creates so many backups of them. Certain recovery techniques can do without superblocks, but you may have to lower your expectations regarding the quality of the recovery to use them.

[I] Is there any software that can recover data from a soft array?
[/I]In many ways, the fact that your data is on a RAID array is irrelevant. The only way it might affect your choice of recovery software is on the off-chance some applications are better than others at handling atypically large filesystems.

[I]I have yet to actually let fsck run
[/I]I can understand that. Once you let fsck make changes, you can't go backwards. Imo, if you can't afford to lose your data, you can't afford to trust that fsck won't, with 100% certainty, make your situation worse.

**Edit:** What's on your array?

---

### Post by tuckie on 2007-09-28
[LIST]
[*]Yes, I'm positive I have ext3
[*]I used the default settings, and using tune2fs, it told me the block size is 4k (you can figure out the location from the blocksize)
[*]/dev/md0 is correct
[/LIST]

Basically, mdadm forgot the array existed, so I had to use --assemble, while skipping the one drive that got formatted.  Does the order that the drives are placed matter?  I just purchased 2, 1tb drives to put in a raid0 in order to do a DD of the data, and they decided to take spots sda and sdf.  As long as the correct four, 500gb drives (all wd, 500gb re2) are added to the array, does mdadm care the order?

Also, I tried using testdisk (IIRC that was the name), and it would only look at physical drives, and ignored md0, is there a way around that? Lastly, I used DD to do a direct disk copy, but for whatever reason the file size is slightly different between the raid 5 and the raid 0, so when I try to run fsck on the raid 0 , it spits out an error that the expected file size is different, and forces me to run the scan manually (-y option doesnt work) is there a way around this (I may just make dd make an image file onto the raid0 instead, but idk)?

---

### Post by kidders on 2007-09-28
> **tuckie said:**
> Does the order that the drives are placed matter? Not normally, no. It *might* if you were manually configuring mdadm using /dev node names instead of UUIDs, I suppose. RAID components do have a logical order, but unless you manually instructed mdadm to do something silly, you wouldn't need to even be aware of it.

> **tuckie said:**
> Also, I tried using testdisk (IIRC that was the name), and it would only look at physical drives, and ignored md0, is there a way around that?Odd. I've never used testdisk, but its documentation suggests it's happy to work with RAID. Testdisk's emphasis seems to be on partition tables & bootability though, so I'm not sure how useful you'll find it.

> **tuckie said:**
> Lastly, I used DD to do a direct disk copy, but for whatever reason the file size is slightly different between the raid 5 and the raid 0What did you do exactly? I would suggest dumping the damaged array to a file and performing any recovery operations on that, *not* the array itself.

Were you using the array to store something in particular, or is there a variety of stuff on it?

---

### Post by tuckie on 2007-09-28
The reason I'm concerned about the order, is upon adding the 2, 1tb drives, one took sda, one took sdf.  My original setup consisted of sd[abcde]  then, sdb was removed from the raid (and the computer), but now sda (i think) became sdb, and the 1tb drive took sda's place. 

So far, I have yet to tweak the data on the original array, I used dd if=/dev/md0 of=/dev/md1 and have been seeing if there is anything i could run on md1 (the new raid0 consisting of two 1tb drives).

---

### Post by kidders on 2007-09-28
Ah I see...

As you probably know, you can have mdadm search /dev for component devices using a regular expression like the "sd[abcde]" you mentioned. That doesn't mean, however, that any of those devices will actually become part of a given array ... it just instructs mdadm to *consider* them. In any case, arrays have internal identifiers, allowing your software to distinguish between them. Mdadm would have to be explicitly forced to mix devices from one array with devices from another.

For instance, my mdadm.conf contains the line...```
DEVICE /dev/hda6 /dev/etherd/e1.[0123456789]
```...which tells mdadm to scan for and try to use any of 10 remote hard disks, along with one local one ... but mdadm won't complain if it doesn't find them all. Equally, if /dev/etherd/e1.3 and /dev/etherd/e1.4 turned out to be from from two different arrays, mdadm wouldn't try to somehow "blend" them together.

I'm not sure if I hit your concern on the head ... but i *hope* that helps.

If you're in doubt about anything, you can use "mdadm --examine" or "mdadm --detail" to tell you about "/dev/sd"s or "/dev/md"s, and help you figure out what's what.

> **tuckie said:**
> I used dd if=/dev/md0 of=/dev/md1I would strongly recommend against doing that. Instead, you should try some equivalent of...```
mount /dev/md1 /mnt/guineapig
dd if=/dev/md0 of=!$/array_dump.img
```You shouldn't try to dump 5-disk RAID 5 structures onto a 2-disk RAID 1 array. If, during the course of an attempt to recover data from array_dump.img, or turn it into a valid Ext3 filesystem, you suspect you're only making things worse, you can recreate the disk image and start again.

---

### Post by tuckie on 2007-09-30
Thanks for all your help, I'm backing up to an image now, it should be done in a few hours.  What commands would you recommend I try to get it recovered?

---

### Post by tuckie on 2007-10-01
anyone?

---

### Post by kidders on 2007-10-01
Sorry for the delay in posting back.

Now that you have a disk image to work off, you can do pretty much anything you like. The fsck you were nervous about running before might be a good place to start ... you never know ... the result may well be a perfectly working filesystem!

Assuming fsck just makes a bad situation worse however, I would suggest taking a look through Ubuntu's repos & elsewhere for forensic data recovery software. What to try depends on what's on the broken filesystem, how badly damaged it is, and so on. I would probably start with the least ambitious recovery app you can find, and work up from there. That way, at least you'll know pretty quickly whether there's any recoverable data there at all.

---

### Post by az on 2007-10-01
> **kidders said:**
>  I would suggest taking a look through Ubuntu's repos & elsewhere for forensic data recovery software. What to try depends on what's on the broken filesystem, how badly damaged it is, and so on. I would probably start with the least ambitious recovery app you can find, and work up from there. That way, at least you'll know pretty quickly whether there's any recoverable data there at all.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by tuckie on 2007-10-01
Thanks again all, it would appear I'm FSCKed (original I know ; ) )  Running fsck offered no such luck for me, so its onto seeing if anything can be recovered. does anyone know if there is anything that can recover isos? or even just recover a list of files?

---

### Post by kidders on 2007-10-02
I'm not aware of anything that can recover ISO images specifically. Perhaps az is? In general terms, the fact that they can be quite large is an obstacle. Compared to your average MP3, for instance, it's relatively unlikely that *all* of a very large file would survive a major incident. :-(

I hope you don't mind me back-tracking for a moment, but could you post the output of "mdadm --detail /dev/md0" ... just to be sure your array is alright.

---

### Post by tuckie on 2007-10-02
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 15 15:27:59 2007
     Raid Level : raid5
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
    Device Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Oct  2 09:27:53 2007
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 924216eb:0286f46e:ded1c07b:24d974d7
         Events : 0.339522

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       0        0        4      removed

---

### Post by kidders on 2007-10-02
Thanks. Your array looks in good shape, which is what is so weird about this whole thing, really. Your filesystem should have been in no way affected by the loss of one of your drives. :-( As far as your system is concerned, the array is working perfectly ... yet somehow the fact remains that the filesystem on it is corrupted. As a side note, it's important to try to figure out *how* that happened, so you can avoid a repeat incident.

Anyhow, back to the present. If you've had no luck with any of the common filesystem recovery utilities, all that remains is to try to pull individual files off the array image, using utilities like foremost, which (I think) is mentioned in the link az kindly provided.

As I said before though, quickly invoking something basic & non-invasive like foremost would probably have been my very first step, just to be sure there was *something* worth recovering still on the filesystem image. You see, if metadata-based file recovery utilities can't retrieve anything at all, then it's highly unlikely that other (more ambitious) recovery techniques will produce results. So, assuming you took that advice, I'm not sure what to suggest next, especially since you're reluctant to say too much about what was on your RAID array.

The one thing you did mention was ISO images. Statistically speaking, recovering undamaged files from a corrupted filesystem is far more likely where the files are small. Consequently, even if you can find a utility capable of digging ISOs out of a corrupted filesystem, they may not be intact.

> **tuckie said:**
> Thanks again all, it would appear I'm FSCKedLol ... (sort of). Your situation is looking less and less encouraging with each post. I'm sorry this isn't going very well.

---

### Post by tuckie on 2007-10-02
Thanks for the advice, I ran foremost, and it did pull some stuff from the image, but the bulk of which was corrupted.  I would say that the bulk of the stuff I had on there was isos (movie rips, so I get to go through that process again), as well as rars, a few shell scripts that I'm sad to see go (any way I can do a raw search to find them?), a lot of .avis and .mpgs, which i assume due to their size, are probably corrupted.  Foremost did recover a few rouge jpgs, (and I have to go through it a bit more) as well as some other files, but it seems pretty much hosed.

On a good note, nothing that was stored was irreplaceable, I just wished I at least had a list of all of what was on it.  In the future, I'm going to generate such a list, as well as back up (some/ most of) the array in the future.  I was hoping raid 5 would have prevented some of this, but I guess that only protects from physical disk failure, not a corruption of the partition.

edit: any idea why I get a segmentation fault while working with foremost after its been running for a while?

---

### Post by kidders on 2007-10-02
> **tuckie said:**
> ... a few shell scripts that I'm sad to see go (any way I can do a raw search to find them?)No, not really ... short of manually searching the raw filesystem data for them. By and large, flat text files have no useful structural information.

> **tuckie said:**
> I was hoping raid 5 would have prevented some of this, but I guess that only protects from physical disk failure, not a corruption of the partition.That's true. It's odd to see both happen at the same time though!

> **tuckie said:**
> any idea why I get a segmentation fault while working with foremost after its been running for a while?None at all. :-( Perhaps you've discovered a bug in it. Sorry I can't be more helpful.

---

