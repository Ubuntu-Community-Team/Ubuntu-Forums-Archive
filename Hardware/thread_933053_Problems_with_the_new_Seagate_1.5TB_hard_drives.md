---
title: "Problems with the new Seagate 1.5TB hard drives"
date: 2008-09-29
forum: Hardware
---

### Post by jafa on 2008-09-29
My system has been running Hardy with 3 x 500GB Seagate SATA drives. This worked well.

I have just replaced the drives with 2 x 1.5TB Seagate SATA drives.

Now the system freezes for 30 seconds every so often. Each time it freezes the kernel log indicates an error "ata frozen", "resetting" and the command looks to be a flush-cache-to-disk command. The exact text is below.

This is the same OS install (direct disk copy) that worked with the Seagate 500GB drives.

I have seen the error on both 1.5TB drives.

Any ideas?

Nick

ata1.00: exception Emask 0x40 SAct 0x0 SErr 0x800 action 0x6 frozen
ata1: SError: { HostInt }
ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
         res 40/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x44 (timeout)
ata1.00: status: { DRDY }
ata1: hard resetting link
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: configured for UDMA/133
ata1: EH complete
sd 0:0:0:0: [sda] 2930277168 512-byte hardware sectors (1500302 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by prshah on 2008-09-29
> **jafa said:**
> 
ata1.00: exception Emask 0x40 SAct 0x0 SErr 0x800 action 0x6 frozen
ata1: SError: { HostInt }
ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
         res 40/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x44 (timeout)
ata1.00: status: { DRDY }
ata1: hard resetting link


Surprisingly, this is sometimes due to logical filesystem damage (not physical). I often get this error if the system is not shutdown properly. To resolve it, I boot off a live CD, and run fsck on the filesystem```
sudo fsck -a /dev/sdb
``` If you get an error such as "Unexpected inconsistency - run fsck manually", then you have to run it without the "-a" switch. The status messages when running fsck will be interspread with messages similar to the one above; you can ignore them. When asked to fix anything, give "y" (in fact, I just pres Y+Enter 15 times and then leave the system to do it's thing). You can also try the "-y" flag (assume "Yes").

There is a very real possibility of data loss; so you do this at your own risk. In my own case, I have often lost package information, but luckily enough no data and/or critical files. YMMV.

Post back with your results.

---

### Post by jafa on 2008-09-29
Hi,

There are two files systems, both ext3, and both passed a force check without error.

Nick

---

### Post by jafa on 2008-09-30
Ok, must be a kernel bug in Hardy 2.6.24... upgrading to a stock 2.6.26 kernel fixed the problem.

---

### Post by jafa on 2008-10-01
Scratch that.

With the Hardy kernel the error occurs every 20 mins watching TV (mythtv) but each time recovers after 20-30 seconds.

With the 2.6.26 kernel the error doesn't occur as often, but when it hits it takes the machine down (any disk access returns an IO error).

The motherboard is an AMD based chipset. I added a PCI-E SATA controller (different chipset) and the same errors occur.

Nick

---

### Post by jafa on 2008-10-10
Ok, workaround...

The specific ATA command each freeze turned out to always be a cache-flush command.

Disabling write cache on the drive avoided the problem:
hdparm -W0 /dev/sda

For other people seeing ATA errors - check if the command is exactly "cmd ea/00:00:00:00:00/00:00:00:00:00/a0" - if you are seeing different numbers then you are probably seeing a different error and the above workaround probably won't apply.

Still no idea why the cache flush command causes Ubuntu to freeze with these drives.

Nick

---

### Post by AndreMiller on 2008-10-18
You are not alone in your frustrations with this drive. I was running a 4 drive RAID5 with Seagate 1TB drives and are in process of swapping them out for Seagate 1.5TB drives.

The array has been running fine until I replaced one of the drives. To replace I simply pulled out one of the drives to let the array run in a degraded mode, plugged in the new 1.5TB drive, added it as a spare and then had md rebuild the array.

I received no errors while rebuilding, but now when I watch video off the array I get a couple of seconds lockup and then it would continue.

I saw similar errors in the log file:

[73993.695861] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[73993.695887] ata6.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[73993.695891]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[73993.695913] ata6.00: status: { DRDY }
[73993.695934] ata6: hard resetting link
[73994.336493] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[73994.405922] ata6.00: configured for UDMA/133
[73994.405940] ata6: EH complete
[73994.406323] sd 5:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
[73994.415687] sd 5:0:0:0: [sdc] Write Protect is off
[73994.415696] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[73994.441321] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

I swapped cables, controllers, slots in the hotswap bay, power rails and even bypassed the bay and plugged it in directly. The errors always occur only on the 1.5TB drive.

I'm going to try your suggestion disabling the write cache to see if it resolves the problem, but I'm also curious as to why this is happening.

I'm running Kernel 2.6.24-16.

PS: I also noticed that the drive is always in 3.0 Gbps SATA II mode. I tried forcing it to 1.5 Gbps mode to see if that would help, but putting the jumper in doesn't make a difference, the controller (and Linux) still reports it running in SATA II mode.

---

### Post by AndreMiller on 2008-10-19
Just some feedback.. since making that quick fix of yours jafa the problem has gone away. Although I'm sure it has some impact on performance.

I have also noticed something else in my logs:

[   46.025256] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.027051] ata2.00: failed to set max address (err_mask=0x1)
[   46.027054] ata2.00: device aborted resize (2930277168 -> 18446744072344861488), skipping HPA handling
[   46.027060] ata2.00: ATA-8: ST31500341AS, SD17, max UDMA/133
[   46.027062] ata2.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   46.028493] ata2.00: configured for UDMA/133

I only get that error message on the 1.5TB drive, the other drives don't seem to have that problem:

[   45.386592] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   45.388155] ata1.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   45.388160] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   45.390115] ata1.00: configured for UDMA/133
[   46.664930] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.666465] ata3.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   46.666468] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   46.668379] ata3.00: configured for UDMA/133
[   47.304586] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   47.306191] ata4.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   47.306195] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   47.308167] ata4.00: configured for UDMA/133

Are you noticing the same thing jafa?

---

### Post by tigertech on 2008-10-20
As an additional data point: I am a Debian etch user (etch-and-a-half, kernel 2.6.24) having the exact same problem with the new Seagate 1.5 TB ST31500341A drives.

I have tested two of them, and with write caching enabled (the default), they both fail in a RAID 1 array within minutes of applying heavy disk write load to them, with the same symptoms you're seeing:

```
Oct 11 22:27:57 kernel: ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 11 22:27:57 kernel: ata4.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 11 22:27:57 kernel:          res 40/00:01:09:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 11 22:27:57 kernel: ata4.00: status: { DRDY }
Oct 11 22:28:02 kernel: ata4: port is slow to respond, please be patient (Status 0xd0)
Oct 11 22:28:07 kernel: ata4: prereset failed (errno=-16)
Oct 11 22:28:07 kernel: ata4: reset failed, giving up
Oct 11 22:28:07 kernel: ata4.00: disabled
Oct 11 22:28:07 kernel: ata4: EH complete
Oct 11 22:28:07 kernel: sd 3:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Oct 11 22:28:07 kernel: end_request: I/O error, dev sdd, sector 2929677503
Oct 11 22:28:07 kernel: md: super_written gets error=-5, uptodate=0
Oct 11 22:28:07 kernel: raid1: Disk failure on sdd1, disabling device.
```


Disabling the write cache solves the problem.

This is specifically related to the new 1.5 TB disks: the server also has some 1 TB Seagate drives in it (model ST31000340AS) that do not have this problem.

In answer to AndreMiller seeing a "device aborted resize (2930277168 -> 1844674407234486148), skipping HPA handling" message -- I do not have that problem. That part of my logs looks normal:

```
ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata4.00: HPA detected: current 2930277168, native 18446744072344861488
```

--
Robert L Mathews

---

### Post by AndreMiller on 2008-10-24
I did some more searching and found that there are loads more users with this problem:

Mac User Thread: [http://forums.macrumors.com/showthread.php?t=571843](http://forums.macrumors.com/showthread.php?t=571843)
Synlogy Users Thread: [http://www.synology.com/enu/forum/viewtopic.php?f=26&t=10746](http://www.synology.com/enu/forum/viewtopic.php?f=26&t=10746)
Toms Hardware Users Thread: [http://www.tomshardware.com/forum/247119-32-media-playback-problems-st31500341as](http://www.tomshardware.com/forum/247119-32-media-playback-problems-st31500341as)
Netgear ReadyNAS (They removed it from their compatibility list after user complaints): [http://www.readynas.com/forum/viewtopic.php?f=20&t=20435&st=0&sk=t&sd=a](http://www.readynas.com/forum/viewtopic.php?f=20&t=20435&st=0&sk=t&sd=a)

Hopefully Seagate gets on the ball here and releases a firmware fix.

---

### Post by tigertech on 2008-10-28
I complained to Seagate about this, explaining that I had seen it on Linux but that I'd also heard of similar reports on Macs so I didn't think it was a Linux issue, and received the following "helpful" reply:

> 
Some systems experience issues with partitions larger than 1 terabyte. This appears to be an issue with the way linux handles these large partitions (also affecting Macs which are built on linux). Please try partitioning the drive to a smaller partition (1 TB or less) to isolate the issue to the drive, or the size of the partition.


This seems like nonsense (especially since Macs are BSD based, not Linux), but I guess I'll try it anyway just to prove them wrong. The bad news is that they still aren't to the point of acknowledging the problem yet.

--
Robert L Mathews

---

### Post by dionrowney on 2008-10-29
I also received:

```
Oct 28 19:50:44 nas kernel: [33514.084222] ata1: port is slow to respond, please be patient (Status 0xd0)
Oct 28 19:50:49 nas kernel: [33518.759445] ata1: device not ready (errno=-16), forcing hardreset
Oct 28 19:50:49 nas kernel: [33518.759451] ata1: hard resetting link
Oct 28 19:50:49 nas kernel: [33519.271423] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 28 19:50:49 nas kernel: [33519.329229] ata1.00: configured for UDMA/133
Oct 28 19:50:49 nas kernel: [33519.329244] ata1: EH complete
Oct 28 19:50:49 nas kernel: [33519.329715] sd 0:0:0:0: [sda] 2930277168 512-byte hardware sectors (1500302 MB)
Oct 28 19:50:49 nas kernel: [33519.337081] sd 0:0:0:0: [sda] Write Protect is off
Oct 28 19:50:49 nas kernel: [33519.353894] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 28 19:52:17 nas kernel: [33606.909962]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 28 19:52:22 nas kernel: [33612.276263] ata2: port is slow to respond, please be patient (Status 0xd0)
Oct 28 19:52:27 nas kernel: [33616.951486] ata2: device not ready (errno=-16), forcing hardreset
Oct 28 19:52:27 nas kernel: [33616.951493] ata2: hard resetting link
Oct 28 19:52:27 nas kernel: [33617.459214] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 28 19:52:28 nas kernel: [33617.519218] ata2.00: configured for UDMA/133
Oct 28 19:52:28 nas kernel: [33617.519236] ata2: EH complete
Oct 28 19:52:28 nas kernel: [33617.519614] sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
Oct 28 19:52:28 nas kernel: [33617.528568] sd 1:0:0:0: [sdb] Write Protect is off
Oct 28 19:52:28 nas kernel: [33617.547809] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

and solved it by using the previous suggestion of disabling the write cache on the drive using the hdparm workaround:   

```
hdparm -W0 /dev/sda
```

Would be nice if it just worked.  Not sure who to blame here...  Just thought I would let everyone know what I got to fix the problem.

dion

---

### Post by forger on 2008-10-29
a) Why don't you break your hard drives into 3 smaller partitions?
or
b) Use a different filesystem?
[http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html](http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html)
[http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php](http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)
[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)
or
c) Use ubuntu amd64 as operating system and a 64-bit machine? :)

Hint: Maybe ubuntu's server edition has some "tricks" to cope with such things :)
Edit: Maybe my information is incorrect, not sure! :KS

---

### Post by dionrowney on 2008-10-29
I was using xfs and pretty sure drive cache has little or nothing to do with filesystem.

Partition size maybe but now that drive cache is off it works - I can only suspect drive firmware at this point.

---

### Post by tigertech on 2008-10-31
> **tigertech said:**
> 
(stuff about partition sizes) seems like nonsense (especially since Macs are BSD based, not Linux), but I guess I'll try it anyway just to prove them wrong.


I tried partitioning it to a smaller size, and of course, the problem still happens. It has nothing to do with partition size.

By the way, the problem has since happened to me once even with write caching disabled (with the exact same cache flush error). Turning off the drive cache seems to make it much less likely to happen, but doesn't completely stop it.

--
Robert L Mathews

---

### Post by mdalacu on 2008-11-09
i have the same problems in win xp 32 , i am desperate! :((
Some times Bios doesn't recognize the drive... :-((

---

### Post by flamacue on 2008-11-15
Apparently they're working on it.

[_[COLOR="Blue"]Seagate responds to 1.5TB HDD freezing issues[/COLOR]_]("http://www.pureoverclock.com/story.php?id=3162")

---

### Post by ersestur on 2008-12-24
Anyone still having this issue? Because I bought one of those drives last week, with a different bios and serial number but the same error. Every ten minutes or so when I watch a movie, it pauses for 1-2 seconds. Disabling write cache makes this appear less often, not removing it.

No word back yet from Seagate Support :/

---

### Post by Haventfoundme on 2008-12-27
> ersestur  
Re: Problems with the new Seagate 1.5TB hard drives

--------------------------------------------------------------------------------
Anyone still having this issue? Because I bought one of those drives last week, with a different bios and serial number but the same error. Every ten minutes or so when I watch a movie, it pauses for 1-2 seconds. Disabling write cache makes this appear less often, not removing it.

No word back yet from Seagate Support :/  

[FONT="Century Gothic"]I have experienced this issue recenetly but I do not own a seagate HDD. I have some Maxtor 500GB HDDs that I've owned for almost a year. On Monday I decided to do a fresh install of ubuntu 8.04 on one of my Maxtor drives. I already had ubuntu running on that HDD but it was split up with a vista partition. The fresh install was guided for the entire HDD. After the installation I did not install any applications or updates. I opened up firefox and went to the debian site so I can download etch. 
I came home about four hours later and checked on the etch download. Everything was frozen but my mouse was still able to move around the desktop. HDD light was still on but I couldn't get anything to work/shutdown. I gave it about twenty minutes but then the desktop was gone. Only thing that was displayed on the monitor was a flashing cursor. I decided to restart the computer and grub loaded but as ubuntu was loading the hardrive failed. It made mechanical failure noises, i.e. clicking and springing noise. 
After removing the HDD and attempting to mount it with a live CD , no dice. I have to say that I think the hard drive is gone. It sometimes gets detected by the bios but after the bios detects it the clicking begins and then it just makes a springing noise after a few clicks. So i paid my dues and put that HDD to the side.
Two days ago I decided to take a chance and I intsalled ubuntu 8.04 on another on of my Maxtor HDDs. Everything seemed okay until last night. I was on Apples website and firefox grayed out, "Froze". I was still able to select all the other gui items on the desktop, but after a while the desktop froze again. The only difference with this HDD was that I did install updates and some apps but it was still acting like the failed HDD.
Well I gave it some time and the desktop was gone,replaced with a flashing cursor. Then I got the ata: status: { DRDY } text. I took some pics of the text and can upload that later. It  would not shutdown and just continued to loop the same data. So I dedcided to bite the bullet and restart the box. After the restart no HDD failure but Ubuntu fails to boot correctly. Everything is slow gui is missing and desktop stays frozen.
Later today I will drive scrubb the HDD and reinstall so wish me luck......Sorry for the long reply.[/FONT]

---

### Post by flamacue on 2008-12-28
There is a firmware fix.  Contact Seagate technical support and they will send it to you.

It's a bootable CD from what I'm told.  I assume it'll be an .iso file.  In any case, I'm told Windows is not required to execute the update.  (I should receive mine tomorrow.)

---

### Post by stokkes on 2009-01-08
Alright, I'm having problems with all 3 of my Seagate 1.5TB drives (**with** upgraded firmware).. Note that these drives never worked.

Here's what I get when I boot in dmesg (for each of the 3 drives - ubuntu 8.10 server on intel64):

```

[    5.090034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.091790] ata1.00: failed to set max address (err_mask=0x1)
[    5.091793] ata1.00: device aborted resize (2930275055 -> 18446744072344861488), skipping HPA handling
[    5.091797] ata1.00: ATA-8: ST31500341AS, SD1A, max UDMA/133
[    5.091800] ata1.00: 2930275055 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.093197] ata1.00: configured for UDMA/133

```

Now, what happens when I boot the system is that **none** of the 1.5 drive's partitions are detected (they don't show up in /dev). More specifically, all I see in dev is /dev/sda, /dev/sdb /dev/sdc, the actual partitions (/dev/sda1, etc) are not there. The only way for me to get the partitions detected in /dev is to do: 

```

/sbin/blockdev --rereadpt /dev/sda (or b, or c, etc..)

```

This forces the kernel I'm guessing to re-read the partition table from the drives, which then allows me to mount the raid (otherwise there's no way to mount it). Why I know this is related to ubuntu and not my drives:

[LIST=1]
[*]Happened in 8.04 (kernel 2.6.24) , upgraded to 8.10 (2.6.27-9 server) and still happens.
[*]Booted with the 8.10 Server LiveCD and they don't appear in /dev either (same error in dmesg)
[*]Booting the the GParted LiveCD **does not produce any errors**. All the partitions show up (as they should) in /dev. **Kernel is 2.6.26-1-486**
[*]Formatting the drive in Windows works as well.
[/LIST]

I am completely out of ideas as to what I should be doing next. The drives are OK, the system is OK.. It's something with ubuntu or the kernel.... I am really pulling my hairs out because I can't properly mount the raid.

-- JR

---

### Post by ode on 2009-02-06
Has there been any progress on this situation?
Where are we at now?

Thanks

---

### Post by bavish on 2009-02-15
Interesting new oddity.  I just got 5 more 1.5T drives to go along with 4 others.  4 of the 5 are "different".  Not sure how/why, but they actually aren't meeting the letter of the Seagate specification.  All are running firmware CC1H.

They appear absolutely identical to "hdparm -I" except for serial number and such, AND capacity.

Previous drives:

  LBA48  user addressable sectors: 2930277168

4 of 5 new drives:

  LBA48  user addressable sectors: 2930275055

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=511a8cf6a794b110VgnVCM100000f5ee0a0aRCRD](http://www.seagate.com/ww/v/index.jsp?vgnextoid=511a8cf6a794b110VgnVCM100000f5ee0a0aRCRD) tells us they guarantee 2930277168 sectors per disk.  They've stolen 1M from us!  :)  ok...  not really a big hairy deal to me.  But...

...This is the weird part--they behave differently.  Fire up "dd if=/dev/sdX of=/dev/null bs=1024000" on 3 of the new ones at once and "iostat -xk 5" shows this:

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sdc           246379.80     0.00 2341.20    0.00 124364.80     0.00   106.24     3.36    1.43   0.42  97.74
sdd           30410.00     0.00 1045.60    0.00 125772.80     0.00   240.58     1.78    1.70   0.94  98.76
sde           243043.40     0.00 2129.00    0.00 122560.80     0.00   115.13     3.34    1.57   0.46  98.20

Notice the average request sizes?  Notice the read requests merged per second?  Yep, sdd is the drive with larger capacity.  sdc and sde are the lower capacity drives. 

Mostly just curious since none of this actually impacts me, but what's going on?  They've tinkered with something.

---

### Post by bavish on 2009-02-16
> **bavish said:**
> Interesting new oddity.  I just got 5 more 1.5T drives to go along with 4 others.  4 of the 5 are "different".I think I answered it myself.  What's different about those 4 is I let a RAID device touch them first.  And it replumbed the disks to its liking, reducing the size and tweaking the blocksize.   Put those back and the drives all work like the others.  sigh.

---

### Post by fhuang2 on 2009-05-29
Here's my work around...  I used another known working HD (Maxtor 300GB) and partitioned it as / and swap.  I used the Seagate 1.5T as /home.  So far the update is over 7 days now.  Before when I had all the partitions (/ /home swap) on the Seagate 1.5T, it can stay up maximum of 5 days before freezing/crashing.

I left the write cache enabled on both Maxtor and Seagate drives.

[   54.783142] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   54.785297] ata1.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[   54.785340] ata1.00: 586114704 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   54.788384] ata1.00: configured for UDMA/133
...
[   56.920698] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   56.920749] sd 0:0:0:0: [sda] Write Protect is off
[   56.920791] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.920802] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.920888] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   56.920937] sd 0:0:0:0: [sda] Write Protect is off
[   56.920977] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.920989] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   55.427587] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   55.427679] usb 5-1.1: configuration #1 chosen from 1 choice
[   55.569990] ata2.00: failed to set max address (err_mask=0x1)
[   55.570034] ata2.00: device aborted resize (2930277168 -> 18446744072344861488), skipping HPA handling
[   55.570089] ata2.00: ATA-8: ST31500341AS, CC1H, max UDMA/133
[   55.570130] ata2.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   55.584667] ata2.00: configured for UDMA/133
...
[   57.032056] sd 0:0:0:0: [sda] Attached SCSI disk
[   57.032139] sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   57.032196] sd 1:0:0:0: [sdb] Write Protect is off
[   57.032237] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   57.032248] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   57.032336] sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   57.032407] sd 1:0:0:0: [sdb] Write Protect is off
[   57.032451] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   57.032472] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by Jestersage on 2009-05-29
Wow. I was about to debate between this and the smaller 1TB Caviar Black, but looking at this thread it's caviar black for me.

---

