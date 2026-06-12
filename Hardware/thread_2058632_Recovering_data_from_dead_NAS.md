---
title: "Recovering data from dead NAS"
date: 2012-09-16
forum: Hardware
---

### Post by VeeDubb on 2012-09-16
I'm trying to recover the data from my recently dead Seagate Blackarmor NAS 110.  

It's got a 1TB SATA drive, which I had previously assumed was formatted NTFS.

The NAS died today, and while it won't be the end of the world, I have over 650GB of data that I'd really rather not lose.

I removed the drive (no easy task) and hooked it up inside my desktop.  Much to my everlasting surprise, it's not formatted NTFS.  It's actually got 3 ext3 partitions and a linux-swap partition.  (plus a couple chunks of unallocated space)

What's throwing me off is that even though there's one partition that is obviously the data partition at 928GB, and the others are quite small, gparted shows that all 4 partitions are flaged as RAID.

Does anybody have any idea where I should get started with trying to get these partitions mounted so I can move my data to a new NAS?

---

### Post by VeeDubb on 2012-09-16
If it makes a difference, the current allocation is:

unallocated | 95.37MB

/dev/sdc1 | ext3 | 1019.48MB | 150.23MB used | raid

/dev/sdc2 | linux-swap | 1020.43MB | raid

/dev/sdc3 | ext3 | 509.26MB | 50.35MB used | raid

/dev/sdc4 | ext3 | Label NASRAID | 928.84GB | 679.00GB used | raid

unallocated | 96.21MB

---

### Post by VeeDubb on 2012-09-16
When I just try 
```
sudo mount /dev/sdc4 /arbitrary/folder/i/made
```

It returns an error that says

```
mount: unknown filesystem type 'linux_raid_member'
```

I'm very familiar with the concept of RAID, but I've never worked with it before, and I don't know of any type of RAID that would be configured with 4 partitions of different sizes, including a swap space.  I'm also at a complete loss as to why there would be a raid set up using multiple partitions on a drive of fairly mundane size.

---

### Post by VeeDubb on 2012-09-16
```
sudo mount /dev/sdc4 -t ext3 /arbitrary/folder/i/made
```

That did the trick.  As far as I can tell, there is no raid, just incorrect flags.  Otherwise, it looks like the drive is fine, but the NAS is shot.  Now I've got a spare 1TB drive at least.  Now if I only had a working NAS, but that's really not a technical issue.  lol

---

### Post by cwsnyder on 2012-09-16
From your description and what I know of NAS devices (not much), it looks to me as if the first 3 partitions are used for the NAS Linux operating system, while the 4th is used for the stored data.  It would attach by a SAMBA or NFS share (smb:// I assume from the data) and would mirror any portion of the drive to another drive if you had more than one drive.  I am in the dark as well as you on RAID on a single disk partition.

---

### Post by cwsnyder on 2012-09-16
I did some more checking and it looks as if your drive was set up to be a part of a RAID array so that you could hot swap drives to your NAS.  You may need a RAID controller to access any of your data.

---

### Post by VeeDubb on 2012-09-16
I had the same concern, but apparently not.  This is a single drive, non-expandable NAS.  By simply telling Ubuntu that sdc4 is a regular old ext3, it mounted right up, and the data is there.

---

### Post by ihuntinde on 2013-03-26
I know this is a relatively old post, but I wanted to let everyone know what I had to do to get my data back.

As some background, my NAS110 had 90gb of photos (kids baby pics, vacation, hobby, etc...), 200gb of videos (baby videos, vacation, holidays, etc...) and 75gb of Itunes music... In order to save my marriage, I had to get this back... according to my wife...

After hours of googling how to restore data from a crashed seagate nas110 and getting a lot of forum posts saying that the data was gone, send the NAS back to Seagate and let them see what they could do, etc... I decided to do a google search for NAS Data Recovery and found a piece of software with that exact name that allowed me to connect the hard drive directly to my Windows 8 desktop.  Runtime.org has a piece of software called NAS Data Recovery Version 2.12.  You can download a trial version for free from the website.  I ran this software on a trial basis at first just to make sure it would work, and believe it or not it recognized the XFS file system that the NAS110 used and I was able to browse the hard drive from within the software without any issues.  The only problem is that the trial version of NAS Data Recovery doesn't allow you to save the files or execute them, only view them through their software.  However, for $99.00 you can upgrade to the full version which gives you the ability to restore the files to another hard drive.  I quickly gave runtime.org my credit card information and after 4 hours or so hours of restoring, I now have ALL of my photos, videos and music off of the NAS hard drive.  It was by far the BEST $99.00 I had spent in a while.

---

### Post by ndbeser on 2013-12-07
I realize this is an old thread, however the topic is rather current for me. My daughter was using Blackamor NAS 110 to back up her graphic design artwork, and we are now getting a solid amber light indicating a drive failure. Was that the same type of error that you ran into when your NAS systems went up? I have a linux system that I can use to attempt a recovery, and I am willing to purchase the software that was reference in the thread if it helps. My concern is that if the drive has died, then it may not be possible to mount it again. 

Thank-you for any help on this problem. 

Nick

---

### Post by Jan-Borre on 2014-03-13
Old thread - I know, but here is a way to get data from NAS 110 storage for free :)

-Download DiskInternals Linux Reader from [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) and install. Mount NAS storage and get started.
-Create Image of NAS Storage (biggest partition), and then you mount it in Linux Reader.
-Taddaa..! And there are you're files ready to save or recover (if recover you must download Linux Recovery from DiskInternals.com). 

It used 4 ours to create image file of NAS storage when I managed to get data from Black Armor NAS 110 storage. Hope this helps :)

PS! My english is a little rusten.

Borre

---

### Post by milleralexis768 on 2014-04-03
You may try this hard drive data recovery solution which helped me before: [hard drive data recovery]("http://www.asoftech.com/articles/pc-hard-disk-data-recovery.html")

It's easy to follow and works well for me.

---

### Post by scott57 on 2014-07-29
Reviving an old thread here, but I just experienced a similar problem. My Seagate BlackArmor NAS died and took one mirrored drive with it. The drive has four partitions, the three small ones hold housekeeping stuff for the NAS device. The large one holds the data. In my case one of the first three partitions was corrupted, so I had trouble with all of the windows and osx based solutions. This is what finally worked for me using ubuntu 14.04, which i booted off a USB flash drive.

$ sudo dd bs=512 if=/dev/sdd4 of=/mnt/2TB_A/NAS_recover/sdd4.iso
$ sudo losetup /dev/loop1 /mnt/2TB_A/NAS_recover/sdd4.iso
$ sudo mdadm &#8211;assemble /dev/md3 /dev/loop1

The first command copies the partition to an image file. My drive was sdd4, yours might be sdc4, or sdb4. Check beforehand using the "disks" utility app or, via the command "sudo parted --list". "/mnt/2TB_A/" is a new drive i bought, with ample space to hold my 1TB nas volume

The second command links the file to a "loop" stream on dev. This is needed because mdadm will only read from /dev/, not from actual files. (loop0 was busy already)

The third command tells mdadm (linux raid volume manager) to assemble a raid volume on /dev/md3, using the existing data in /dev/loop1. (md1 and md2 were already in use) It also creates a mountable thingy in /dev/mapper/, called "vg0-lv0". 

At this point, ubuntu automatically mounted my disk as "/media/ubuntu/DATAVOLUME". If it hadn't I imagine the following would worked:

$ sudo mkdir /media/ubuntu/DATAVOLUME
$ sudo mount -t ext3 /dev/mapper/vg0-lv0 /media/ubuntu/DATAVOLUME


Moral of the story: Don't buy cheap off-the-shelf NAS devices. I'm taking an old computer and turning it into an ubuntu-based RAID box. I might even use the cloud functionality to maintain an off-site backup as well.

---

### Post by tgalati4 on 2014-07-29
I have never found an off-the-shelf NAS (to quote Bart Simpson) that didn't "simultaneously blow and suck."

At least with home-built, recovery is easier since the partitioning scheme is straight-forward.

---

### Post by noel2 on 2014-08-11
Jan-Borre not sure if you would see this in time but doesn't this mean i would need another 1 or 2 TB drive to create the image to, even though the information i have on the drive is way less that 1tb ...
VeeDubb , i am a bit of a new user here , i copied and pasted your terminal code hoping it would work but it returns a notice of mount point not existing ...
mount : mount point /arbitrary/folder/i/made does not exist .....to be exact 
ihuntinde ...would you personal message me and take a partial pay donation to share your license code thought it would not hurt to ask...

---

### Post by coffeecat on 2014-08-12
March 26th, 2013:

> **ihuntinde said:**
> I know this is a relatively old post

December 7th, 2013:

> **ndbeser said:**
> I realize this is an old thread

March 13th, 2014:

> **Jan-Borre said:**
> Old thread - I know

July 29th, 2014:

> **scott57 said:**
> Reviving an old thread here

:rolleyes: Repose in peace, old thread, in memory of the NAS for which you were started. :wink:

If anyone wants help recovering data from a defunct NAS, please start a fresh thread.

Thread closed.

---

