---
title: "Data recovery suggestions"
date: 2010-05-22
forum: Hardware
---

### Post by 99bluefoxx on 2010-05-22
So I've come into the recent issue of a drive crash in my main  desktop - My D drive, which plays host to %Program Files%, The Page  file, innumerable little pet projects and the likes, suffered the  misfortune of linux crashing in the middle of me moving the partition.  And not just a little crash that a CAB solved either. No, Raising  Elephants did nothing, reset switch failed me. Had to go for the plug to  get the machine to do *anything* other than burn in my tube. Anyhow,  I've pulled the drive in question and stuffed it into an alternate box  used for troubleshooting crap like this, a meager P4 with no OS, but  brilliant for booting live CDs.
So far I've managed to find out  that it's reporting itself as failed via S.M.A.R.T., MHDD on my x86  System Rescue CD fails to recognize it, the latest GRUB boot disc  refuses to complete a check of the drive, telling me little more than to  run chkdsk /f from windows(Which I'm at the moment hesitant to attempt  to boot on my main seeing as half my OS was on there), nor can I copy  the partition onto the 1.5GiB drive I picked up for scratch space for  recovering the data(One more of them and I'll be replacing my current  drives with these in a RAID5 though).
So what I'm wondering now is  what tools can be suggested to me for this purpose? I had some  interesting things for just this sort of thing - but they were installed  on the drive in question, it was never thought that they'd be needed  for this machine. Oh irony, how you mock me sometimes.</span>

---

### Post by oldsoundguy on 2010-05-22
Try running the self booting disk repair tools for that particular make of drive.  THAT will tell you what is WRONG with the drive and you can go from there.  If track zero is gone .. only a recovery service will be able to get the data from the disk.

---

### Post by 99bluefoxx on 2010-05-22
Well I would do that if I could do that, but as of right now I've got no way to burn any kind of optical media. Now excuse me if I come off as exasperated, but that's exactly what I am. Somehow I don't think you read through all of my post, else you would realize I already did my troubleshooting here, and know what my problem is. I posted here hoping to get some tips for recovery of the issue, but apparently no me.

---

### Post by oldsoundguy on 2010-05-22
I did not say BURN anything .. somewhere you SHOULD have kept a copy of the utilities disk for your hard drive.

Apparently you do not have it, or you would have run that.

The POINT being you need to find out if track ZERO is good or not.  From your description, it would appear that a bad track zero is what you have, but only one way to PROVE that.

Does booting with a Live Linux CD and using the GParted partitioning utility under system> administration SEE anything?

---

### Post by tgalati4 on 2010-05-23
Boot a Live Ubuntu CD open a terminal and post:

sudo fdisk -l

If you can see your drive in the device list then you can probably use photorec to see the data.

sudo apt-get install testdisk
man photorec

Drives do tend to fail during massive write operations.  The heads get toasty and burn out or delaminate, rendering the drive inoperative.  That would cause the type of freeze you are describing:  the OS is in an IO wait state with no data forthcoming.  The fact that you tried different shutdown methods is a testament to the type of hardware failure.  What was the SMART error condition?

---

### Post by 99bluefoxx on 2010-05-23
> **oldsoundguy said:**
> I did not say BURN anything .. somewhere you  SHOULD have kept a copy of the utilities disk for your hard drive.
Apparently you do not have it, or you would have run that.

I buy my parts OEM, more cost effective by getting rid of the 'extra fluff' in the packaging. I'm not made of money, which is why I'm not taking this issue to a store either. Sides that, how can I call myself a geek if I can't even rescue my own *** when I suffer a drive crash?

> **oldsoundguy said:**
> 
Does booting with a Live Linux CD and using the GParted partitioning  utility under system> administration SEE anything?
As I thought I stated clearly enough in my opening post, gparted fails to complete a check of the partition. Based on that statement, I thought one might assume that 
a)Gparted can actually see the hard drive and
b)Gparted sees some kind of partition to check.

If my partition was nuked, I'd be looking at testdisk or sommat for trying to read what was left of the partition.

> **tgalati4 said:**
> Boot a Live Ubuntu CD open a terminal and post:

sudo fdisk -l

If you can see your drive in the device list then you can probably use photorec to see the data.

Output from fdisk as follows:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3GB, 1500302920026 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector Size (logical/physical):512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier 0x0003dba7

     Device Boot     Start          End     Blocks     ID     System

Disk /dev/sdb: 320.1GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 - 8225280 bytes
Sector Size (logical/physical):512 bytes / 512 bytes
I/O size (minimum/optimal):512 bytes / 512 bytes
Disk identifier 0x00082959

     Device Boot     Start          End          Blocks     ID     System
/dev/sdb2 *               1       36302     2915783+      7     HPFS/NTFS
ubuntu@ubuntu:~$

```
I'll see if photorec from my RIP linux disc or the System Rescue CD(Forget which had it, think was the former) can see anything, though I'm still baffled as to why mhdd doesn't see anything.
> **tgalati4 said:**
> 
Drives do tend to fail during massive write operations.  The heads get toasty and burn out or delaminate, rendering the drive inoperative.  That would cause the type of freeze you are describing:  the OS is in an IO wait state with no data forthcoming.  The fact that you tried different shutdown methods is a testament to the type of hardware failure.  What was the SMART error condition?
Makes enough sense. I'd slap the drive in question into an enclosure and use smartmontools from my laptop to see what I could, except that I've long known that USB cuts out all the nice ATA commandsets, including ability to read SMART statuses.

---

### Post by tgalati4 on 2010-05-23
True, SMART doesn't work over USB.  It's like doing an necropsy on an old dog.  The dog is dead, regardless of what the cause was.  Morbid curiosity? Perhaps.

Good luck.

---

### Post by 99bluefoxx on 2010-05-23
So, failing to receive any really useful feedback, I went spelunking through the internet for a few hours on my own, and came up with a nice bunch of useful little tools for this kind of thing - for windows.
Fine, we'll do it that way.
I set up an old P4 box, installed XP on it, and after spending ~<30minutes bashing it into acceptable shape, found that WinHex seems to be doing a fine job of recovering what data it can - which seems so far to be most of it.
All I've lost so far is some installer cache files, a couple files out of some mods for games, the odd program or two that I don't use often or just installed, and some temp files.
'Course, that being said, I'm only ~50GiB into ~280GiB of data to salvage, and than I get to see what my windows install does when I plop the drive back in.
Where am I going from here? Well once I've made a list of what I need to reinstall, I'll be reassembling my main desktop, slapping this unhappy drive back in place and seeing what windows does.
If it's no problems, than I'll probably move my pagefile onto C, I'll set the environmental variable for %Program Files% to C and after that, format the drive to make the most of it's space, if I can looking into telling it to avoid bad sectors and the likes. Copy the old contents of Program Files back on, switch that back and search for a replacement. As for linux, well for now it stays on my old SPARC and RISC workstations, and occasionally on a dual CPU server. Next time I want to fisk about with my partitions, I'll be using a gparted live CD or something. Lesson learned - ubuntu doesn't agree with my hardware.
Marking this thread as 'solved', even if I didn't gain much from it.

---

