---
title: "3TB storage drive recognition"
date: 2012-04-16
forum: Hardware
---

### Post by hotdoog on 2012-04-16
Hi,

Summary: I have a 3TB external backup disc with data on it that one of my computers can see and the other cannot. The drive was formatted by palimpsest unusually because it is so big. I think I can get the drive to be read by the 2nd computer if I put a GPT/MBR partition table on it. I need to know if it is possible to do that without wiping the disc.

Main Question: Can you tell me how to put a simple partition table (one partition GPT MBR GUID UEFI... whatever works!) onto a 3tb drive that has data on it already?

Details:
I have a new 3TB external storage drive that I use for backups. It is a WD30EZRS (Western Digital Caviar Green). I put it into NexstarCX enclosure and connect to it with eSATA.

This drive I formatted using my main work computer (2006 era AMD64 Ubuntu 10.04 64 - up-to-date with aptitude) via the Palimpsest Disc Utility to be ext4 everything default setting. I then moved about 1.3TB of data (mostly redundant backups but not entirely) and reallocated the space where that data came from (ie I can't easily just copy the data off the disc and not wipe it - due to the size of data) I realise now that I made a mistake. I should have tested this blank disc on all the systems I needed to use it on. Instead I skipped that step because it seems to work fine with my main work computer.

When creating this I did not specify any partitions. Palimpsest says "not partitioned". I notice now that GParted cannot read this disc but says: *e2label dumpe2fs error can't find superblock.*

This disc cannot be read on my main home computer. That is a Dell Intel Ubuntu 32 bit 10.04 laptop 2008 era (also up-to-date packagewise). That computer will not automount it and both palimpsest and gparted show errors about the block count not matching - I have not tried a force mount. These programs do show it being 3TB so I don't think the hardware is totally preventing this from working (I could be wrong)

I'm hoping I can reformat just the MBR/Superblock (?) using the AMD64 computer that does read it. I know it isn't good to do that with data on there, but most of it is just backup data and I don't want to have to transfer 1.3TB again (takes a day each direction)

My understanding is that MBR has a 2.2TB limit so one must use a GUID solution like GPT to do this for a 3TB drive. I've installed gdisk to try and do that but apparently gdisk can't read this either. I'm quite mystified by how palimpsest formatted this drive to ext4 - especially as it doesn't have a verbose output!

Here is the output:
```
rusl@feinberg:~$ gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdc: 5860533168 sectors, 2.7 TiB
Disk identifier (GUID): 07D93CA8-2223-0C63-7A74-3C2921502A19
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
rusl@feinberg:~$ gdisk -l /dev/sdc1
GPT fdisk (gdisk) version 0.5.1

NOTE: Write test failed with error number 2. It will be impossible to save
changes to this disk's partition table!

Problem opening /dev/sdc1 for reading! Error is 2
```

And with fdisk:
```
rusl@feinberg:~$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

At this point I really don't know what to do. I know it is possible to manually create MBR with dd and since the drive is only one (or none?) partitions that could theoretically be done? But I've only ever done that sort of thing cut and pasting other people's instructions. And I guess I would need to manually do a GPT not a MBR anyway?

Is it possible to do this without a reformat/wipe data?
Does anyone know what formatting scheme palimpsest might have used here? If I know how the drive is currently being read then maybe I could figure out how to fix the problem?

Another idea I have is that MBR supposedly can do larger than 2.2TB if you make more than one partition and the first one is less than the 2.2TB limit. Apparently this technique only works on linux and isn't bootable but that is OK with me for this instance. So if I could get Gparted to read the drive properly I could resize the partition and make a 2nd one. However, I can't get gparted to read this properly on either computer. Maybe if I relabelled it using Gparted but AFAIK that would wipe data.

Thank you very very much for reading this and any help you can provide.

FYI:```
rusl@feinberg:~$ uname -a
Linux feinberg 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:10:32 UTC 2012 x86_64 GNU/Linux

```

I guess I should also get the kernel of the laptop, it is the newest from standard repos.

---

### Post by oldfred on 2012-04-16
I have seen where it is possible to just format a drive without partitions like one big floppy drive or CD. I did not pay attention as I could never see a reason for not partitioning as all the tools expect partitions and one very large partition makes for me makes little sense. I want to break it up into several partitions just so if I have to repair, run e2fsck, or recover data I can work on part of a drive not the entire thing.

I do not see how you can add partitions to a unpartitioned but formated drive. Perhaps someone else does know.

Since it is 3TB, I would have suggested using gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. Or use gdisk.

---

### Post by hotdoog on 2012-04-16
Thanks for responding oldfred,

I have in the past made too much complication with many partitions and LVM and RAID5 disasters. I learned the hard way about making things more complicated than I should have. So I now try to simplify and for OS drive to only have OS, home, and swap. But this is a separate backup drive so I figured just make it all one - then I can move files around easier on it. I'm not sure what advantage I would get having sectioned off this drive as it is all just storage so I don't really need to have it live to fix it or anything.

I would not have chosen to do it without a partition table but palimpsest did that automatically. I should have been more aware of what it did.

When you say gparted or gdisk create partition table, can that be done without destroying data? Usually the GUI throws up warnings saying data will be wiped for those operations IIRC?

---

### Post by oldfred on 2012-04-16
I would think that creating the partition table would overwrite parts of your data and destroy the current file tables. Which would destroy all your data. 

Unless someone has a partition tool that moves the data from the specific areas that a partition table needs, I do not see how. Again, someone else may have a solution, but I do not know.

What does testdisk show, anything?

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by hotdoog on 2012-04-16
Thank you! I forgot about testdisk. I will play with that some and report back in a couple days. Cheers.

---

### Post by hotdoog on 2012-04-24
OK, testdisk says this:
```
rusl@feinberg:~$ testdisk /list
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
...
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63, sector size=512
Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 364801 255 63, sector size=512

...
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition			Start        End    Size in sectors
 1 P Linux                    0   1  1 243200 254 63 3907024002 [codexgigas]
No partition is bootable
Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 364801 255 63
     Partition			Start        End    Size in sectors
   P ext4                     0   0  1 364801  80 63 5860533168 [SSHeartofGold]

```

The drive in question is sdc 3TB. I left sdb in just for comparison. That is part of my system (not external) and is basically the same thing - a large ext4 drive. However that one has an MBR. Also I'm not sure where the warning "No partition is bootable" is meant to be with sdb or sdc. It isn't really relevant because it shouldn't be bootable anyway. However maybe it indicates something? I see there is no number 1 before the "P" for sdc which I take to mean no numbered partition.

Now what? I'm reading some testdisk howto's so maybe I'll find something there. 

I take the Start 0   0  1 364801 to mean there is nothing written before 364801 so conceivably I could write a partition table before that. But it can't be MBR because too big. I don't know how. Also I'm a little worried that the 2nd number is a 0 for sdc and a 1 for sdb. But again I'm not literate enough to know what that really means.:confused:

Thanks for any insight you may have. Cheers,
rusl

---

### Post by oldfred on 2012-04-25
I do not have any solutions. 

Teskdisk still uses the old cylinders, head, sectors which have not really been used since hard drives went over 8GB. BIOS had to convert to LBA to allow large drives with MBR partitioning.

Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

It is just saying you have the entire drive as storage space, but no partitions.

For pure storage some do not partition, although the consensus was to partition.
[http://forums.cnet.com/7723-7588_102-331189/partition-or-not-partition/](http://forums.cnet.com/7723-7588_102-331189/partition-or-not-partition/)

---

### Post by hotdoog on 2012-05-04
Thanks Fred.

The output of testdisk on the other system (the ubuntu32 that can't mount it) is slightly different:

```
Disk /dev/sdb - 3000 GB / 2794 GiB - CHS 364801 255 63, sector size=512
...
No partition is bootable
Disk /dev/sdb - 3000 GB / 2794 GiB - CHS 364801 255 63
     Partition			Start        End    Size in sectors
   P ext4                     0   0  1 364801  80 62 5860533167 [SSHeartofGold]
```

The difference being 62 vs 63 and the last digit of the big number off by one. Does this mean anything important?

I thought LBA and BIOS recognition of the MBR were only relevant to booting which in this case doesn't matter? but you know more about this than I do?

I sort of want to just try running the testdisk program to create a GPT table. However all the howto I read are MBR not GPT. But I may just backup the small amount of data on this drive that is unique (relatively small, still a few hundred GB) and then try it to see if it works and if  id doesn't I'll try to start anew using GParted this time to create a single ext4 partition which hopefully should work. Perhaps I'll even use this 32bit laptop for it. OTOH I like to do that movement of data on the other system because it has an eSATA port which really speeds it all up.

Cheers,
rusl

---

### Post by oldfred on 2012-05-04
I do not think testdisk converts to gpt. I do have gpt on my new SSD, a flash drive (just to see if it works, it does) and my 10.10 install on a 160GB drive. The 10.10 install has been my working install until I converted to 12/04 on my SSD.

Supposedly you can convert a MBR to gpt with some caveats. I have not tried it but just used gparted to create new partition table and totally reformat.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

I do not know enough about the inner working of hard drives. And the one or two that do, that I learned what little I think I know, have not posted for ages.

---

### Post by hotdoog on 2012-05-10
I finally found some time to backup the data on this disk (1TB takes time) and am now playing with it. I just noticed that the first 446 bytes of my 2TB drive (single ext4 partition) and the 3TB drive (somehow now partitioned ext4) are identical. (I used dd to copy and diff to compare)

So I think what happened is palimpsest tried to partition this drive exactly like normal with MBR but wrote a number too big for MBR (because of the 2.2TB limit). So I should probably file a bug with palimpsest. For some reason this computer 64bit Lucid reads it fine but the 32bit Lucid machine I have gets thrown off by the mistake. Maybe some hardware differences account for that.

Anyway i'm now going to try to convert to GPT. I'll let you know.

---

### Post by oldfred on 2012-05-10
It sounds like it may be a bug in palimpsest. I would look at it an see if something has been reported.

bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility)
I did not find anything on search for gpt or large drives, not sure what to search other than just reviewing them.

---

### Post by hotdoog on 2012-05-11
Well, I couldn't doing it without wrecking the data. Good thing it was backed up.

Here is what I did:
I tried to use gdisk to create a new GPT partition. That worked but meant the old data was lost. I think because I had no partition to begin with there wasn't the empty space to write the GPT partition table in so it overwrote the beginning of the old "non-partition" ext4 partition. At least that is my best guess. If I really understood this properly I wouldn't be here figuring it out.

So I just started new with a GPT partition then with a ext4 format inside that. Even that part was quirky. GPT is clearly a new technology and the tools are not so well designed to handle it yet. For example read the long list of known bugs in the gdisk manpage!

Issues with installing the GPT partition: (to the best of my understanding, please correct me if you know I am wrong)
-palimpsest will not do it correctly
-gparted will, however it starts the partition at bit 34 instead of aligning it with a physical sector head. The interface of gparted (select by megabytes) doesn't seem fine grained enough to set it to byte 512 or 4096.
-gdisk does it all but is a program for experts who really understand this technical hard drive stuff better than the average user. I tried to do cgdisk which is supposed to be included in the gdisk package but it wasn't there. (ubuntu repo package) gdisk will also default to starting at the first available byte instead of the sector boundary.
-the naming of the partition types for gdisk is very different from fdisk. In fdisk the linux partition is "83" but in GPT it is a different code (lumped with windows data?) that shows up as "ee" in fdisk:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      267350  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

```

I'm hoping I got the sector alignment issue proper. Palimpsest helpfully throws up an error if you start the partition at the wrong place saying that you are (paraphrased) '3072 bytes misaligned and there will be serious performance issues.' If you read [http://www.rodsbooks.com/gdisk/workarounds.html](http://www.rodsbooks.com/gdisk/workarounds.html) he says it can be 25x slower to write small files on a misaligned file system so you don't want to make a mistake.

What I ended up doing was using gdisk to create the GPT partition table (the "o" option) and manually setting that to start at 4096. Thus palimpsest stops complaining. Then I used gparted to create the ext4 filesystem structure and labels (much more user friendly than gdisk) Note that gparted shows an unused 2MB before my partition as free space. This is because I manually set it to start at 4096.

That is what I did. hope it is helpful to someone. I have tested the new partition on my other laptop (that was unable to read it before) and it is recognised properly there now.

Final Conclusions:
-Read [http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html) as much as possible before undertaking
-Palimpsest has a bug currently preventing it from being safe to use to partition disks larger than 2.2TB
-Stick with MBR (better understood, widely supported) as long as you can because GPT is not yet ready for the average idiot like myself level of consumption.

I am what I am because of who we all are!

Rusl

---

### Post by oldfred on 2012-05-11
I know gparted changed in the last year or so to use 1MB or 2048 boundaries. 

Fdisk does not work on gpt drives and just finds the protective MBR table which is just there so old MBR tools do not mess with gpt drives.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by hotdoog on 2012-05-11
Jeepers yeah my Gparted is 5.1-ish which is ~2010 - that is the Lucid Repo version. I would have thought it would be more current. Sourceforge says latest stable is 12.1!

So I found a PPA: [http://www.ubuntuupdates.org/ppa/nathan-renniewaldock_ppa?dist=lucid](http://www.ubuntuupdates.org/ppa/nathan-renniewaldock_ppa?dist=lucid) which gets me up to 10.1 which is a lot better now.

Wow, new gparted has an "undelete" style data recovery. [http://www.webupd8.org/2011/02/rescue-lost-partitions-data-with.html](http://www.webupd8.org/2011/02/rescue-lost-partitions-data-with.html) Maybe if I had run that I would have avoided the 10 hours waiting for all this data to transfer. Live and learn.

Cheers,
rusl

---

### Post by oldfred on 2012-05-11
While I usually just use the gparted on the current liveCD, I often download the gparted liveCD as I have several ISOs I boot directly with grub2's loopmount  from my flash drive, so I do not have to burn a new CD for every version change.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

