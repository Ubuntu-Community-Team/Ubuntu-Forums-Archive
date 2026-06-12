---
title: "Hard drive recovery, mounting"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by ScottHW on 2007-06-04
I have a crashed Windows XP system/data drive, and as such it is NTFS.  I was unable to chkdisk, or do anything at all with it using other Windows boxes.  I also tried SeaTools, but that would hang at a certain point during the "long scan".

My overall question would be, "How do I recover the data from this drive".  But, I've tried a technique oft described across the net...

I came across references to ddrescue.  So I plugged the HDD in, and booted up my Ubuntu (Breezy, I know it's old, I don't use linux as much as I'd like to).  I used ddrescue to write a copy of anything I could read off the drive (NTFS, 160GB) to my Linux partition.  Around 86GB were written into a file.  Here there is at least a spot of confusion for me; when I "copy" the data from the bad NTFS drive to the Linux ext3 partition, is the FileSystem of the data still NTFS, then?

The real question here is this:  when I try to 
```

sudo mount /image /mount_point -t NTFS

```
I get:
```

mount: /image is not a block device (maybe try `-o loop'?)

```
What does this mean?  I've searched Google, and the forums, but no where is there a clear description of "block devices" or how I work with something that apparently isn't one.

Thanks for any help/advice on this issue.

UPDATE:
```

sudo fdisk -l /dev/loop0

Disk /dev/loop0: 86.6 GB, 86644559872 bytes
255 heads, 63 sectors/track, 10533 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/loop0 doesn't contain a valid partition table

```
No partition table.... that can't be good.  Seems like this could have a serious effect on the ability of the NTFS image to be mounted??

I know that while I was using SeaTools, it said that one of the methods of trying to recover data was to "Erase Track 0 - Remove an old operating system" or similar.  I believe that I did try that option, and still SeaTools couldn't finish a long scan thru the disk.

---

### Post by tommcd on 2007-06-04
This is not free (costs $89.00) but it is supposed to work really well for data recovery:
[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)
If the data is really important, and you can not find a cheaper alternative, you night consider spinrite.

---

### Post by ScottHW on 2007-06-04
The data is not crucial per say, but I do want to have it back.  I apperciate the info, but I would rather try to use this as a learning experience to further my Linux knowledge.

---

### Post by ScottHW on 2007-06-04
I guess now in retrospect, fdisk -l already told me
```

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

So, even before my ddrescue attempts, maybe I need to modify my question to:

"How do I 'recover' the partition table, or work around this issue"?

Is it likely that SeaTools' "Wipe Track 0" deleated my partition table?  That wouldn't seem like a very prudent method of trying to recover damaged hard disks....

---

### Post by ScottHW on 2007-06-04
Well, seems like no one has any ideas for me yet.... so I've kept researching

As mentioned, it looks like the partition table is gone.  So some searching then led me to *gpart*.  It guessed at the partition(s) on the drive, and thinks there should be two: a DOS ~39MB and then Windows (ntfs) for the rest of the ~159GB.  Seems plausible, the drive was from a Dell originally, factor formatted/partitioned and so forth.

Is there any way for me to directly read the partition table information?  GParted shows me "*Disk type: unrecognized*" and the whole thing "*unallocated*", but I want to actually see the bytes.  I guess in this case I'd assume they're all [FONT="Courier New"]00[/FONT].

I could use Gpart to write the guessed partition information to the table, but first, I would like to see if there's anything there now.  And secondly, if this isn't right, can I "undo", and go back to whatever IS there now?

Does anybody think this is a good/bad idea?  I'm open to other suggestions.

---

### Post by daradib on 2007-11-13
I hope this late response will help you.

I do believe Erase Track 0 - Remove an old operating system did format (and delete everything including data, partitions, and partition table). This is a data-destructive method for fixing a hard disk that would otherwise be damaged.

According to Seagate,
> ZERO FILL DATA PATTERN WRITING IS A DATA DESTRUCTIVE OPERATION EQUIVALENT TO ERASING THE DATA OFF THE DRIVE.

A "Defective drive" can often be revived with a data-destructive zero fill data pattern or a low level format. This is because today's modern disc drives contain thousands of spare sectors which are automatically reallocated if the drive senses difficulty reading or writing. Since SeaTools is read-only
(data safe) occasionally a drive with many problem sectors that have not reallocated to a spare sectors can be forced to do so by writing to the sectors. Spare sector reallocation is a
normal intelligent drive operation.

I was having troubled detailed [here]("http://ubuntuforums.org/showthread.php?t=609735"), and I stumbled upon your thread in a search.

---

