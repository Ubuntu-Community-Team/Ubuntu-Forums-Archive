---
title: "Prepping 2TB WD drives for RAID-5, Misalignement Error"
date: 2011-09-15
forum: Hardware
---

### Post by morilibus on 2011-09-15
Hello,

I'm trying to set up a software raid-5 under ubuntu 11.04.

I used to have a sotware RAID-5 under ubuntu 9.10 with 5 x 1TB WD drives.  Now I'm trying to slowly increase the size of my array by adding in 2TB drives.

So now in Ubuntu 11.04 I'm trying to create a new array using 4 x 1TB drives and 2 x 2TB drives, the goal is to add a 2TB drive as a spare, then remove one of the 1TB drives until I have 6 x 2TB drives ( keeping my last remain sata port as a means of swapped in drives.

I'm pretty new to the linux scene and usually search for how-to's everytime I need to do anything, but I'm more familiar with it then I was a year ago.

note: This RAID-5 array is only used for storage, The OS is installed on a separate 500GB drive.

PROBLEM:
When I try to Partition the 2TB western Digital drives I get the error 
> WARNING: The partition is misaligned by 3072 bytes. This may result in very poor performance. Repartitioning is recommendedI've been googling around and it seems for the most part that error can be ignored, except when you dealing with WD drives.

I originally used fdisk to partition the drives as a primary MBR, I would get the same error, however I could use the -u & -c commands to fix the problem.

However, It seems that steering clear of MBR is ideal for larger drives. Thus I'm trying to partition the drives with a GUID Partition Table instead.  But now I'm getting the same error as before, but I'm not sure how to remedy it this time.  I was trying to do this just with the GUI Disk Utility, but it doesn't really give you many options( or any ).

So what's the best course of action here? Is there a different partition program I should try?(Gparted? or can I do a GPT using fdisk?)

My Raid-array is being constructed at the moment, so I'm thinking of tearing it apart 'again' to try to fix those 2 drives, then rebuild.

Unfortunately I didn't notice the misalignment this time till I had already started the building process.

Here is** fdisk -l** to Start with, let me know if more info is needed.
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f29c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       60802   468852737    5  Extended
/dev/sda5           60194       60802     4881408   82  Linux swap / Solaris
/dev/sda6            2432       60194   463970304   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121602   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121602   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761527   ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      243202  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      243202  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
Note: sector size is 4096 (not 512)

Disk /dev/sdi: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c54a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       45600  2930232320   83  Linux
Note: sector size is 4096 (not 512)

Disk /dev/sdj: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00050bc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       45600  2930232320   83  Linux

Disk /dev/md0: 5001.0 GB, 5001018081280 bytes
2 heads, 4 sectors/track, 1220951680 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 2621440 bytes
Alignment offset: 3072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by srs5694 on 2011-09-15
> **morilibus said:**
> PROBLEM:
When I try to Partition the 2TB western Digital drives I get the error 
I've been googling around and it seems for the most part that error can be ignored, except when you dealing with WD drives.

I'm not sure of the exact numbers, but my impression is that most new drives today use [Advanced Format](http://en.wikipedia.org/wiki/Advanced_format) technology, which is at the root of the issue. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote a while back for performance details and some tips on how to work around it. Be aware, though, that partitioning tools have moved on a bit since I wrote that article, and more than just WD drives now use this technology. (I've got at least one Seagate drive that uses Advanced Format, and maybe two. I didn't even bother to check on the second one's status; I just partitioned it as if it were an Advanced Format drive, since it was an emergency replacement for a failing drive and I didn't have time to look up the details.) Note that Seagate makes some very misleading claims about their Advanced Format drives; they compare their drives with misaligned partitions to *competitor's* drives with both aligned and misaligned partitions, without showing the relevant comparison of aligned to misaligned on one of their own drives.

> However, It seems that steering clear of MBR is ideal for larger drives. Thus I'm trying to partition the drives with a GUID Partition Table instead.

MBR's limit is 2^32 sectors, which works out to 2 TiB, given 512-byte logical sectors, which most modern drives use. (Advanced Format uses 4096-byte physical sectors, but the logical sector size remains 512 bytes, which is at the core of its alignment requirements.) There's no difference in the advantages vs. disadvantages of MBR vs. GPT on a 2 TB (~1.8 TiB) drive vs. on a much smaller drive; it's not like MBR degrades as the drive size increases. Thus, you can safely use MBR on modern 2 TB drives.

That said, GPT does offer advantages even on much smaller drives, as described [here.](http://www.rodsbooks.com/gdisk/whatsgpt.html) IMHO, the biggest advantage of GPT on sub-2TB drives is that GPT does away with the tedious primary/extended/logical partition distinction.

> But now I'm getting the same error as before, but I'm not sure how to remedy it this time.  I was trying to do this just with the GUI Disk Utility, but it doesn't really give you many options( or any ).

Some tools offer a way to view and specify partition sizes in sectors. When you use such an option (such as appending an "s" to a partition start point in parted, or using a value without a unit in gdisk), you can specify start points that are exact multiples of 8 and you should be fine. Most tools released in the last year or so default to creating partitions on 2048-sector (1 MiB) boundaries, which works fine. GParted's got an option to do this, which is set by default. (Other GParted options include cylinder alignment and no alignment. Cylinder alignment is a relic of the past that's been irrelevant for years.) The very latest versions of fdisk default to 1 MiB alignment, but the last I checked, the version in Ubuntu was a bit older and would do cylinder alignment by default. You can change the behavior with the -u and -c options, which have different but related effects -- see the fdisk man page for details.

> So what's the best course of action here? Is there a different partition program I should try?(Gparted? or can I do a GPT using fdisk?)

fdisk doesn't do GPT, but my [GPT fdisk (gdisk, cgdisk, and sgdisk)](http://www.rodsbooks.com/gdisk/) package provides a similar user interface for GPT, and recent versions align to 1 MiB boundaries by default. Recent versions of GParted align to 1 MiB boundaries, as I say, so they're good for GUI tools. I've found parted to be awkward to use for this, but it can be done if you're careful about specifying units in sectors.

Whatever you do, I strongly recommend you check the alignment after you create partitions and before you begin using them for storing data. The easiest ways to do this are with parted, gdisk, or fdisk, although fdisk won't produce useful data for GPT. The commands would be (assuming /dev/sda as the target disk):

```

sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda
sudo fdisk -lu /dev/sda

```

Any of these commands will produce the partition data in sector units. Take each start value and divide by 8. If the result is a whole number, it's fine. If not, it's improperly aligned. (An exception: Alignment on MBR extended partitions is irrelevant. Alignment on [BIOS Boot Partitions](http://en.wikipedia.org/wiki/BIOS_Boot_partition) is also not likely to be important, but from your description, you're not likely to have one of those.)

> Here is** fdisk -l** to Start with, let me know if more info is needed.

Ubuntu's "fdisk -l" produces output in cylinder units, which is insufficiently precise to be of use in determining proper alignment for Advanced Format disks. You'd need "fdisk -lu" to produce useful data. Also, any fdisk output is useless to determine alignment of GPT disks; you need parted or gdisk's output to get data for them, as just noted.

---

### Post by morilibus on 2011-09-15
Great,

Thank you for the prompt response.  That sounds straight forward enough and within my Linux capabilities.  I will try to re-partition using Gparted later today when I get home.  I will post my results.

Thank you

[UPDATE]

OK I tore down the RAID-5(again) and reformatted the two 2TB drives using GParted.  I chose to "create a new partition tabel", then chose advanced, and chose GPT.

I took the output of **sudo fdisk -ku /dev/sd*** before and after, I can't tell the difference, however I used fdisk as I had it already installed and it doesn't support the GPT that was created both times, but here they are anyway.
[B]
Before using GUI Disk Utility:
[/B]
> WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
marc@Tri-serv:~$ sudo fdisk -lu /dev/sdh

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
[B]
After: Using GParted
[/B]> WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
marc@Tri-serv:~$ sudo fdisk -lu /dev/sdh

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

It does no longer says "The partition is misaligned" when looking at the drive in the GUI Disk Utility.  So it would seem that that did the trick.

I appreciate your help with that, if I missed something or should be checking something else, perhaps using you gdisk to output the results since that supports the gpt.

Otherwise I'm going to start rebuilding the array...I can always tear it down again if needed.  Until I get the data back on that is, as I suspect that will take a few days to transfer it all back.

Thank You

---

### Post by srs5694 on 2011-09-15
> **morilibus said:**
> [UPDATE]I almost missed your new information because editing an existing post doesn't seem to make the thread show up as having a new information. I recommend using the reply function rather than editing a post if you want new information to be read.

> I took the output of **sudo fdisk -ku /dev/sd*** before and after, I can't tell the difference, however I used fdisk as I had it already installed and it doesn't support the GPT that was created both times, but here they are anyway.Except for diagnosing problems with the "protective MBR" portion of a GPT disk, the output of fdisk is useless on GPT disks. I therefore can't tell from your output whether your partitions are properly aligned. If you want advice on that, please post the output of "sudo gdisk -l /dev/sda" or "sudo parted /dev/sda unit s print", as I specified in an earlier post.

Also, when posting the output of text-mode programs, please place the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This preserves the columnar output of many such programs (including fdisk, gdisk, and parted), making it easier to read. The [noparse]> [/noparse] and [noparse][/noparse] tags you used don't do this, rendering the output much harder to understand. The forum software also doesn't include quoted text in subsequent quoted responses, which makes it more difficult to respond if it's desirable to include the code output in the response.

> It does no longer says "The partition is misaligned" when looking at the drive in the GUI Disk Utility.  So it would seem that that did the trick.It probably is OK, but I don't know the exact rules for when it produces this warning. It's best to check with a utility that will produce the exact sector start values for the partitions.

---

### Post by morilibus on 2011-09-16
Sorry I didn't realize I quoted the terminal stuff.  I normally do the code, as I did in my first post.  But thanks for the reminder, hopefully that will get 'code'd into my head.

And good point about reposting instead of editing, I wasn't sure if would show as being changed.

Alright here it is:
```
marc@Tri-serv:~$ sudo parted /dev/sdg unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdg: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name            Flags
 1      34s    1953525167s  1953525134s               RAID: Tri-RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdh unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdh: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name            Flags
 1      34s    1953525167s  1953525134s               RAID: Tri-RAID  raid

marc@Tri-serv:~$ 

```

---

### Post by srs5694 on 2011-09-16
> **morilibus said:**
> Alright here it is:
```
marc@Tri-serv:~$ sudo parted /dev/sdg unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdg: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name            Flags
 1      34s    1953525167s  1953525134s               RAID: Tri-RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdh unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdh: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name            Flags
 1      34s    1953525167s  1953525134s               RAID: Tri-RAID  raid

marc@Tri-serv:~$ 

```

I'm afraid those are showing your partitions as beginning on sector 34, which is not evenly divisible by 8 (34/8 = 4.25), so those partitions are *not* properly aligned. I recommend you do one of two things:


[list=1]
[*]Check with the disk manufacturer to find out if the disks are Advanced Format models. This information can be hard to track down sometimes. Seagate in particular seems to be rather coy about the issue, and they downplay the performance problems with misaligned partitions on Advanced Format disks.
[*]Start over and partition using tools that enable specifying sector-precise values.
[/list]


Option #1 can save you some effort if you've already begun using the disks, but only if you discover that the disks are *not* Advanced Format models. If you find that they are Advanced Format, you'll either suffer [performance degradation](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) or you'll have to redo it (option #2) anyhow.

---

### Post by morilibus on 2011-09-16
Awesome, I thought as much after seeing that number, but figured I'd wait for your input before proceeding.  I have yet to do anything with the array, it finished building late last night.

It looks like they are advanced format from what I can tell, and from googling around.

So I'll just bite the bullet and get it done right.

I will try using your gdisk...

ok got it gdisk installed.  Operates like fdisk so pretty straight forward.

One question:

What sector should I set for the starting one?  Again it has 34 as default, and when I was researching before I hear mention of setting to 64 as the start point.  Is that the best way to go, or any multiple of 8 is good, as in round up to 40?

Thanks again for your ongoing help.

-----EDITING----

I redid all drives using gdisk, set starting sector to 64, one of my older 1TB drives set the sector to 2048 however.

Here is terminal of all drives being re-partitioned:

```

marc@Tri-serv:~$ sudo parted /dev/sdg unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdg: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    3907029134s  3907029071s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdh unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdh: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    3907029134s  3907029071s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdb unit s print
Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdb: 1953523055s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      2048s  1953523021s  1953520974s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdc unit s print
Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdc: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    1953525134s  1953525071s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdd unit s print
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdd: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    1953525134s  1953525071s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sde unit s print
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sde: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    1953525134s  1953525071s               Linux RAID  raid

marc@Tri-serv:~$ sudo parted /dev/sdf unit s print
Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdf: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name        Flags
 1      64s    1953525134s  1953525071s               Linux RAID  raid

```Here is sdb that had the different msg when creating new partition table:

```

Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-1953523021, default = 34) or {+-}size{KMGTP}: 64
Information: Moved requested sector from 64 to 2048 in
order to align on 2048-sector boundaries.
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-1953523021, default = 1953523021) or {+-}size{KMGTP}: 
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): fd00
Changed type of partition to 'Linux RAID'

```In fact I don't plan on adding that drive into the array, or possible added in as a spare, then using that empty sata connection to switch new drives in.

Also, is the hex cpde fd00 the proper one to use? Disk Utility shows them as having no free space to add them into the raid, I could try directly using mdadm as see what that outputs.

---

### Post by morilibus on 2011-09-16
Updated Above reply.

---

### Post by morilibus on 2011-09-16
Ok I've been mucking around with gdisk and googling some more.

This is what I have done thus far.

I used gdisk to create partition tables on all drives i intend to use for the raid-5, 4x 1TB & 2x 2TB

I set starting sector size to 2048, only reason is I got the msg noted above but for the 2 TB drive this time, new msg to follow:

```
marc@Tri-serv:~$ sudo gdisk /dev/sdg
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): d
No partitions

Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-3907029134, default = 34) or {+-}size{KMGTP}: 40
[COLOR=Red]Information: Moved requested sector from 40 to 2048 in
order to align on 2048-sector boundaries.[/COLOR]
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-3907029134, default = 3907029134) or {+-}size{KMGTP}: 
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): fd00
Changed type of partition to 'Linux RAID'

Command (? for help): w       

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.
marc@Tri-serv:~$ sudo gdisk -l /dev/sdg
GPT fdisk (gdisk) version 0.6.14

```so I just put them all at the same. don't know if it makes a performance difference if they all have the same starting sector.

Then I used mdadm to create the array

```
marc@Tri-serv:~$ sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=6 /dev/sdg1 /dev/sdh1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Wed Sep 14 20:13:42 2011
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 976760320K
mdadm: largest drive (/dev/sdg1) exceeds size (976760320K) by more than 1%
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```And then when I watch the progress it notes a completion time of about 4 hrs.  which is over twice as fast as when I did it previously with the misalignment issues.  That time it took almost 10 hrs to complete.

So this seems to indicate to me that it has been done properly this time.

I'll await your input again before I start throwing stuff back onto the drive again, just in case I did something stupid. 

```
marc@Tri-serv:~$ sudo gdisk -l /dev/sdg
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdg: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): F3BA2474-6C85-4EB2-BA21-E5A1B68AF00D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3907029134   1.8 TiB     FD00  Linux RAID
marc@Tri-serv:~$ sudo gdisk -l /dev/sdh
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdh: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 313CBD59-3139-4F3B-AEC5-2D748A4916FC
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3907029134   1.8 TiB     FD00  Linux RAID

```

---

### Post by srs5694 on 2011-09-16
It looks good to me!

Concerning starting sector numbers, gdisk uses a set of rules to determine partition alignment, as described under "Partition Alignment Issues" on [this page.](http://nessus.rodsbooks.com/gdisk/advice.html) In brief, gdisk defaults to 2048-sector alignment on blank disks, but it will adjust this value down if it detects an existing set of partitions with a lower alignment rule. This is done to avoid unnecessarily scaring people with warnings about improper alignment on existing disks. On moderately large disks that might plausibly use Advanced Format, the alignment value will never be auto-adjusted down below 8, though.

These rules are probably why you could set a starting sector of 64 on most of your disks but not on all of them -- you could set a value of 64 on disks that had existing misaligned partitions that you deleted, but the default went to 2048 on one disk because it was a blank disk, a disk with partitions aligned on that value, or if you used the "o" option to create a fresh partition table. You would have been fine with the original mix of 64 and 2048 as starting values, but switching to have consistent start points of 2048 is fine, too.

---

### Post by morilibus on 2011-09-16
Ok that makes sense, and explains the confusion with that msg only appearing sometimes.

Thank you again for you help, could to know about the sector, and that setting them all to 2048 only results in a tiny bit of wasted space.

I'll mark this as SOLVED

---

