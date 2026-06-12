---
title: "Advice on salvaging hard disk info"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by gray-squirrel on 2007-03-05
I'm in a bit of a sticky situation, and would like to proceed carefully:

this past Saturday I was doing a check on one of my hard disks, a 40G Maxtor (partitioned 30-10, both FAT32) (hde) from my brand new Windows XP installation and found out that the on hours count as reported by SMART was greater than 2000 hours, but otherwise was running fine.  I rarely access this drive as it is almost full.

Very early this morning, I decided to reboot.  After three unsuccessful attempts to get into Windows XP (just got a blank screen after going through the GRUB menu), I decided to go into Edgy and see what might be the problem.  During the boot, I get surprised with a series of Buffer I/O errors for hde and [FONT="Courier New"]fsck[/FONT] in progress.  Seeing things were about to get out of control, I tried to stop [FONT="Courier New"]fsck[/FONT] with Ctrl+C, then Ctrl+Alt+Del.  Reboot.  I tried it again, and managed to get to a generic desktop, even though /home is on hdg1.

I switch to booting with Dapper.  Still got the Buffer I/O errors, but I manage to force my way through to my desktop.  I could not get exact messages during the boot process (and I apologize), but here is a snippet from the messages log (it repeats the same message at different points during the boot):

```
03/05/2007 12:03:11 AM	localhost	kernel	[17179714.164000] end_request: I/O error, dev hde, sector 89
03/05/2007 12:03:11 AM	localhost	kernel	[17179714.164000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=89
03/05/2007 12:03:11 AM	localhost	kernel	[17179714.164000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:11 AM	localhost	kernel	[17179714.164000] ide: failed opcode was: unknown
03/05/2007 12:03:13 AM	localhost	kernel	[17179715.848000] end_request: I/O error, dev hde, sector 91
03/05/2007 12:03:13 AM	localhost	kernel	[17179715.848000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=91
03/05/2007 12:03:13 AM	localhost	kernel	[17179715.848000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:13 AM	localhost	kernel	[17179715.848000] ide: failed opcode was: unknown
03/05/2007 12:03:13 AM	localhost	kernel	[17179715.848000] printk: 2 messages suppressed.
03/05/2007 12:03:14 AM	localhost	kernel	[17179717.540000] end_request: I/O error, dev hde, sector 93
03/05/2007 12:03:14 AM	localhost	kernel	[17179717.540000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=93
03/05/2007 12:03:14 AM	localhost	kernel	[17179717.540000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:14 AM	localhost	kernel	[17179717.540000] ide: failed opcode was: unknown
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] end_request: I/O error, dev hde, sector 95
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=95
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] ide: failed opcode was: unknown

```

Looks like hde is near the end of the road.  I already got a new drive to replace it, and have an idea of where to move the data.  Dapper is still up (knock on wood), and currently hde5 is mounted (hde1 is not visible).  I'm wondering if it is safer to copy the files over to another partition, or to use [FONT="Courier New"]ddrescue[/FONT] to image either partition.  I'd like to get as much data saved without making matters worse, but wasn't sure whether copying or [FONT="Courier New"]ddrescue[/FONT] would be a "lesser evil".

Thanks in advance for any advice shared.

---

### Post by gray-squirrel on 2007-03-09
Here is the most recent [FONT="Courier New"]smartctl[/FONT] report.  It says the overall health self assessment test result is "passed".  This is puzzling.  Why would it say that in light of what I posted prior to running the [FONT="Courier New"]smartctl[/FONT] test?

---

### Post by jgcamp99 on 2007-03-09
Check your bios settings for hdd related changes. Sometimes, they change and this happens on cheaper motherboards and their chiipsets. I have an ECS K7S5A (SiS735) that can change on a whim.

---

### Post by gray-squirrel on 2007-03-09
> **jgcamp99 said:**
> Check your bios settings for hdd related changes. Sometimes, they change and this happens on cheaper motherboards and their chiipsets. I have an ECS K7S5A (SiS735) that can change on a whim.

Which changes, specifically? 

I have an Abit VA-20 (with VIA KM400 chipset), and the primary drive hda (with Windows XP and Edgy) is running well.  The HDD in question, hde, is actually on a Promise Ultra100 TX2 IDE controller PCI card.  I do remember that the card has a BIOS (which I have never checked before), so I will check that out once I get home this evening.  When I last rebooted a few days ago, it was reporting the correct drive sizes for hde and hdg.  :?

---

### Post by gray-squirrel on 2007-03-11
> **gray-squirrel said:**
> 
I have an Abit VA-20 (with VIA KM400 chipset), and the primary drive hda (with Windows XP and Edgy) is running well.  The HDD in question, hde, is actually on a Promise Ultra100 TX2 IDE controller PCI card.  I do remember that the card has a BIOS (which I have never checked before), so I will check that out once I get home this evening.  When I last rebooted a few days ago, it was reporting the correct drive sizes for hde and hdg.  :?

I guess I had a misconception about the Ultra100 TX2 BIOS.  It is nothing like that of the Abit VA-20, in that there is no provision to go in to change or check settings.  There is nothing in the manual which even mentions this.  It is still reporting the correct sizes of hde and hdg2; I confirmed that when I booted the Kubuntu Live DVD yesterday afternoon.

Here's an update: I repartitioned hdg so that I can have a place to store the partition images of hde1 and hde5; FAT32 was not going to cut it for big files and I wasn't sure how [FONT="Courier New"]ddrescue[/FONT] would handle piping - I was originally going to pipe the output file to split to break this file into 1G files.  I just converted the last partition on hdg from FAT32 to ext3 (it was empty already) and then resized it from 30G to about 51G (so now the entire drive is partitioned).

After I did this, out of curiosity, I checked hde in [FONT="Courier New"]gparted[/FONT], and found hde5 was detected and identified as FAT32 (this was mounted while I was in Dapper earlier, until I used the Live DVD yesterday).  However, hde1 was also supposed to be FAT32, but [FONT="Courier New"]gparted[/FONT] identified it as "unknown".  Considering these are all read errors I've been getting recently, with nothing even being written to the drives for weeks at least, I doubt the partition table or the FAT for hde1 was corrupted.

I ran [FONT="Courier New"]ddrescue[/FONT] on hde5, seeing that is likely to be problem-free, and took in 10.1G with no errors in under 10 minutes.  Then it was on to hde1.  I had to kill [FONT="Courier New"]ddrescue[/FONT] once during this operation because it looked like it froze.  At the end, about 5.5 hours later, I got this:

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:    30276 MB,  errsize:    380 kB,  errors:      77
Current status
rescued:    30277 MB,  errsize:   45056 B,  current rate:        4 B/s
   ipos:    28062 MB,   errors:      88,    average rate:       18 B/s
   opos:    28062 MB
```


Not bad.

I'm looking over my [FONT="Courier New"]smartctl[/FONT] report and the kernel log (posted earlier) more closely and see that there may be DMA issues also.  So, I'll see what happens if I turn off DMA for the drive and run [FONT="Courier New"]ddrescue[/FONT] again to retry those problem areas.  Perhaps I can get that ~45K of data that I couldn't grab earlier.

---

### Post by charles nicholls on 2007-03-11
If its any help I would download a copy of HDD regenerator,  [http://www.dposoft.net/](http://www.dposoft.net/)
or you can find it with google/ torrent. you need to burn the Iso to CD or floppy, Booting  from either will detect and repair bad sectors, (demo only first sector). hope that helps

---

### Post by gray-squirrel on 2007-03-12
Well, it looks like I've pulled enough data from the drive.  So, I try to mount the partition image [FONT="Courier New"]x.img[/FONT], which is sitting in the [FONT="Courier New"]datarec[/FONT] directory on [FONT="Courier New"]/media/hdg3[/FONT] (mount point of [FONT="Courier New"]/dev/hdg3[/FONT]):


```
sudo mkdir /media/recover
sudo mount -t vfat -o loopback /media/hdg3/datarec/x.img /media/recover
```


I then get the following:

```
mount: /dev/loop1: can't read superblock
```


This is odd.  I didn't think FAT32 partitions even had superblocks.

I'm only trying to mount a partition image, rather than a drive image.  I don't plan to restore this partition onto a new hard disk, but rather try to mount the image so that I can move files to new locations on other hard disks (others will be burned to CD/DVD).  Many of the data recovery instructions I've read at other sites mention partition offsets, but that's only because they are dealing with an entire drive image.

Is there something I'm overlooking?  And if I have to create a single drive image (remember, I had two images, one for [FONT="Courier New"]hde1[/FONT] and another for [FONT="Courier New"]hde5[/FONT]), would it be easier to get the MBR as an image, and then [FONT="Courier New"]cat[/FONT] this plus the two partitions to accomplish this task?  I'm trying not to put additional stress on the possibly failing hard disk.

---

### Post by charles nicholls on 2007-03-12
from the errors you posted 

03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=95
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] ide: failed opcode was: unknown

 The same happened to one of my Maxtor 80gig sata drives which had the first sectors damaged and the only way I could fix it was the little prog I posted above which completely repaired the problem. once I had saved the data I repartitioned the drive leaving the first 5 gig unused, Its been fine since then

---

### Post by gray-squirrel on 2007-03-12
> **charles nicholls said:**
> from the errors you posted 

03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: error=0x40 { UncorrectableError }, LBAsect=95, sector=95
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
03/05/2007 12:03:16 AM	localhost	kernel	[17179719.220000] ide: failed opcode was: unknown

 The same happened to one of my Maxtor 80gig sata drives which had the first sectors damaged and the only way I could fix it was the little prog I posted above which completely repaired the problem. once I had saved the data I repartitioned the drive leaving the first 5 gig unused, Its been fine since then

Thanks for the comments.  Though I do have my own tools which do similar things that HDD Regenerator does (Testdisk is one).  I prefer to work from drive images, as it is safer.

It is not surprising that [FONT="Courier New"]ddrescue[/FONT] encountered errors seconds after I started it.  It just confirms that there are errors at the beginning of the drive.  I think it's more that the hard disk can't read there without causing these errors than the writing to the drive causing problems.  Somewhat good news, I guess.

I wish I could repartition the drive, but in light of the fact that I have had that particular drive for about five years, it is probably safer for me to replace the drive (and the kernel will be at peace as well).  The drive is close to 90% full anyway.  Although, I will admit, if I didn't have as much space used, I would definitely save time using your suggestion.

---

### Post by gray-squirrel on 2007-03-14
The image I made of [FONT="Courier New"]hde5[/FONT] I have been able to mount successfully (and the original [FONT="Courier New"]hde5[/FONT] partition itself is still alive and well).

I was thinking of running [FONT="Courier New"]fsck.vfat[/FONT] on [FONT="Courier New"]hde1[/FONT], but of course the image has to be mounted on a loopback device.  And that is something I've tried to do again today, this time in my normal environment (with [FONT="Courier New"]hde[/FONT] unmounted, too) - and I still get a complaint from [FONT="Courier New"]mount[/FONT] that the superblock can't be read.

I found out that a FAT32 superblock is actually the boot sector for the partition.  Is there a way to fudge the partition image so that I can get its superblock to be read and finally get the image mounted?  Despite three days of searching the 'net, I was not able to find anything on this matter.  I want to be sure this image is reasonably okey before I finally swap drives and finish the file recovery.

I don't know if this helps, but here's output for [FONT="Courier New"]fdisk -lu[/FONT] for [FONT="Courier New"]hde[/FONT]:

```
Disk /dev/hde: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1              63    59135264    29567601    c  W95 FAT32 (LBA)
/dev/hde2        59135265    80292869    10578802+   f  W95 Ext'd (LBA)
/dev/hde5        59135328    80292869    10578771    b  W95 FAT32
```


[FONT="Courier New"]fdisk -l[/FONT]:

```
Disk /dev/hde: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        3681    29567601    c  W95 FAT32 (LBA)
/dev/hde2            3682        4998    10578802+   f  W95 Ext'd (LBA)
/dev/hde5            3682        4998    10578771    b  W95 FAT32
```

---

### Post by UniRecovery on 2007-03-15
I would refrain from caopying the data, as the head may snap on you, causing extensive physical damage, which will lead you to the expesive road of data recovery on your had disk.
Try to clone the drive, then work on the cloned drive..

Good luck

---

### Post by gray-squirrel on 2007-03-15
> **UniRecovery said:**
> I would refrain from caopying the data, as the head may snap on you, causing extensive physical damage, which will lead you to the expesive road of data recovery on your had disk.
Try to clone the drive, then work on the cloned drive..

Good luck

Thanks.  I actually meant to say earlier that I was thinking of running [FONT="Courier New"]fsck.vfat[/FONT] on the _image_ of [FONT="Courier New"]hde1[/FONT] that I created.  I knew I couldn't mount [FONT="Courier New"]hde1[/FONT] itself (a result of the errors in my kernel log at the beginning of this saga), but I was kind of surprised that I couldn't mount the image I created.

---

### Post by gray-squirrel on 2007-03-25
I recently discovered a backup copy of the FAT32 superblock in sector  6, so I went ahead and copied it into sector 1 of my imaged version of [FONT="Courier New"]hde1[/FONT].

Still couldn't mount the drive, but Testdisk and Autopsy report that the files are intact.  And [FONT="Courier New"]fsck.vfat [/FONT]does work, although it now results in ```
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!
```

I did not use the [FONT="Courier New"]-r[/FONT] option because I want to see what happens before committing any changes.  I did not expect it to stop completely.

Thought I might share this just in case others are dealing with similar issues like the ones I'm still dealing with.  I'm still looking for ways to get this to mount so I can actually get those files which are being held hostage, and will post if anything comes up which works (and you all are most welcome to offer ideas and suggestions, thanks.)

---

