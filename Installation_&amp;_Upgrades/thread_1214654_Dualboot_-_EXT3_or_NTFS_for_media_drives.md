---
title: "Dualboot - EXT3 or NTFS for media drives?"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by AlfAlf on 2009-07-16
Hi guys,

I've been running an XP/Ubuntu dual boot setup for a couple of months now and I use Ubuntu for general daily stuff, but I'll be keeping XP around for a few programs that won't work under WINE or in a virtual machine.

Seeing as I'm using Linux most of the time, I was wondering if there would be any performance benefit to converting my two media drives to EXT3? I'm going to be reinstalling XP and Ubuntu anyway as they're both a bit of a mess! I've got 3 IDE drives (old system!) partitioned as follows:


[FONT="Verdana"]**HDD1: (~80gb)**

Windows XP, 20Gb, NTFS
home, 20Gb, EXT3 (I'll also be using this instead of My Documents)
Ubuntu, 20Gb, EXT3
SWAP, 2Gb
Games, backup, etc, 20Gb, NTFS



**HDD2: (120Gb)**

Music, 120Gb, NTFS


**HDD3: (180Gb)**

Video, 180Gb, NTFS[/FONT]


I've got all EXT3 partitions mounted natively in XP using [http://www.fs-driver.org/](http://www.fs-driver.org/) which works really well, I haven't had any problems so far. However, my concern is that this driver was designed for reading EXT2 filesystems, which means any journaling benefits of EXT3 will be lost.
In the event of a power cut, sudden shutdown etc, wouldn't there be an increased risk of data corruption using this driver?
Does Linux perform better reading NTFS than XP reading EXT3?
Would one be more stable than the other when being used in the "wrong" OS...?

---

### Post by Revolutionary101 on 2009-07-16
I think you should stick with NTFS. The only reason I think you should is because NTFS offers compression built into the file system.

---

### Post by Chaos Punk on 2009-07-16
Well I've never had any problems reading NTFS in Ubuntu, have you tried looking for Ext3 specific Winblows drivers?

---

### Post by AlfAlf on 2009-07-16
Thanks for your replies.

I haven't had any trouble reading NTFS in Linux either, I'm just wondering if things would work **better** in Linux if music and video was being accessed from an EXT3 drive. There don't appear to be any EXT3 specific drivers for Windows, but there are a few explorer-style programs. It's not really an elegant solution though.

I've heard EXT3 runs faster than NTFS (possibly due to a lack of fragmentation, but I don't know for sure) but wanted to see how much faster - would I notice a difference in everyday use, or is it only better when hammering the system with a benchtest?

Assuming it is worth converting the drives to EXT3, what are the risks of data corruption if the computer crashes whilst I'm in Windows? Bearing in mind the IFS driver will be treating the drives as EXT2, so I'm guessing there will be no journaling?

---

### Post by Revolutionary101 on 2009-07-30
If you are just using those drives for external storage then performance should not be an issue. EXT3 and NTFS will run both run well with little performance difference. The only time where fragmentation becomes an issue is when your OS is on a highly fragmented drive.

---

### Post by thrud00 on 2009-08-11
Actually I've had some serious performance problems running virtual machines from an NTFS partition mounted through NTFS-3g under linux.

---

