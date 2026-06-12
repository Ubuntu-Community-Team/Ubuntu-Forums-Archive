---
title: "WD Advanced Format Drive 4096 Byte speed issues"
date: 2010-05-29
forum: Hardware
---

### Post by psych1610 on 2010-05-29
Hey everyone, I've got a 2 TB WD Green Drive. It's one of those advanced format drives with 4096 byte sectors instead of whatever the normal is. Needless to say, I'm suffering from many of the performance issues others are, specifically, speed.

Here's what I'm encountering:

I just want one partition. Upon the first format of the drive using Lucid (Kernel 2.6.34) and gparted (latest) I can  get ~ 56 MB/s transfer speed from /dev/sdb to /dev/sdc (the advanced format drive). Upon reboot speeds drop to ~ 330 KB/s. Abysmal, to say the least.

I've followed the directions [here]("http://thread.gmane.org/gmane.linux.utilities.util-linux-ng/2926") (it's the post by Aleksander Adamowski on January 25th) detailing how to "fix" the issue using parted (btw I'm using 2.2). I've also run across how to fix it using fdisk and the same parted method on the [WD forums]("http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395").

After following those directions the speeds are ~56 MB/s again. Terrific! However, upon reboot the drop to ~ 1 MB/s. Not good, but about 3x faster than what they were when I originally formatted the drive using gparted. Clearly the fix is doing something, but performance is still terrible.

I've performed my amateur tests copying over my Music, Pictures, and ISO folders (of various OS's). Copying my music directory of 25 GB would take ~ 7 hours to complete at 330 KB/s. My pictures at 11 GB would take slightly less.

So I come to you, Ubuntu forums, please, tell me how I can get the most out of my Advanced Format WD hard drive. I find it so hard to believe a proper fix has not appeared for this, or at least an easy one and I really don't want to go through the trouble of returning the drive but 330 KB/s transfers are just shitty to deal with from disk to disk. 

Details: I'm running Ubuntu Lucid 64 bit. Parted is version 2.2. Gparted is the latest. fdisk is whatever comes with Lucid as default. The hard drive is here: [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5324&p_created=&p_cats=185&p_cv=1.185&p_pv=2.294&p_prods=227%2C294](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5324&p_created=&p_cats=185&p_cv=1.185&p_pv=2.294&p_prods=227%2C294)

The disk I'm transferring from is a non-advanced format 1 TB WD Black drive. I can write to it just fine from the 2 TB advanced format drive.

---

### Post by srs5694 on 2010-05-29
First, *do not* set the Windows XP compatibility jumper. It can simplify things in the short term if you've just got one big partition, but if you ever want to change that, it'll cause more problems and confusion.

Second, see [this article I wrote for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) on this topic. It includes explicit partitioning advice for several tools. IMHO, fdisk (for MBR disks) and gdisk (for GPT disks) work best, followed by the text-mode parted. I wouldn't recommend using GParted to partition such a disk at the moment. In all cases, use the newest version available and follow whatever directions are necessary to create properly aligned partitions.

If you're still having problems, post the output of "sudo fdisk -lu /dev/sdb" (substituting the correct device for "/dev/sdb"; and if you use GPT, make it "sudo gdisk -l /dev/sdb"). This command will show us how your disk is currently partitioned.

---

### Post by psych1610 on 2010-05-29
> **srs5694 said:**
> First, *do not* set the Windows XP compatibility jumper. It can simplify things in the short term if you've just got one big partition, but if you ever want to change that, it'll cause more problems and confusion.

Second, see [this article I wrote for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) on this topic. It includes explicit partitioning advice for several tools. IMHO, fdisk (for MBR disks) and gdisk (for GPT disks) work best, followed by the text-mode parted. I wouldn't recommend using GParted to partition such a disk at the moment. In all cases, use the newest version available and follow whatever directions are necessary to create properly aligned partitions.

If you're still having problems, post the output of "sudo fdisk -lu /dev/sdb" (substituting the correct device for "/dev/sdb"; and if you use GPT, make it "sudo gdisk -l /dev/sdb"). This command will show us how your disk is currently partitioned.

Hey, thanks for your response. I did not set the jumper. Your article for IBM Developer Works was actually another one I came across in my research and greatly assisted me to even get this far! Thanks for writing it. I've used parted successfully as indicated in the first post and after a reboot I'm getting 1 MB/s across disks, not nearly the 60 MB/s I get before it though. Still this is 3x faster than had I rebooted and not used parted at all. Based on that evidence I say there is still a problem somewhere. 

The following is the output from gdisk: 

```
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): A0AADDCE-F2A1-4B5D-AA8A-FAC1A75FF429
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 30 sectors (15.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              64      3907029134   1.8 TiB     0700  primary

```

---

### Post by srs5694 on 2010-05-30
Well, that disk's partition is properly aligned, assuming the jumper is not set -- the start sector number of 64 is divisible by 8.

Given that you're seeing different performance between boots, I can't help but wonder if you're seeing differences that are caused by caching. Linux caches its disk access to improve performance, so the better results may be caused by data already being in the cache. If so, the poor performance reflects the true hardware access speed. I'm not sure what might be causing these problems, but my guess is that it's not something related to the 4096-byte sector size. Perhaps there's a disk/controller interaction that's causing problems...?

Sorry I don't have any better ideas.

---

### Post by psych1610 on 2010-05-30
That's a bit disappointing, to be honest. At least if it were caused by the 4096 byte sector size there might be a go at solving it.

I don't think it's a cache releated issue because the better performance comes directly after I format the drive and sticks around until a reboot. Shouldn't the cache be clear then and therefore have slower speeds? Perhaps I'm not understanding this correctly.

When I get home from work tonight I'll attach the drive to another SATA port on the motherboard and see if maybe that's an issue.

---

### Post by srs5694 on 2010-05-30
The cache is clear when you first boot. After you create a filesystem, there may be some data in the cache relating to the filesystem creation operation; however, I'm not an expert on Linux's caching algorithms, so I don't know if this would have any real effect. It's the only thing that comes to mind, though, aside from incompatibilities with your disk controller hardware. Certainly if you've got multiple SATA controllers on your motherboard it's worth trying the drive with each of them.

---

### Post by psych1610 on 2010-05-30
In the interest of figuring out what the heck is going on with my drives I performed a few tests. Before I go further I should say (thought it should be obvious) these are not scientific, however, things did go as hypothesized. 

/dev/sda is a 80 GB Raptor drive from Western Digital
/dev/sda1 is System Reserved 100 MB
/dev/sda2 is NTFS partition Windows 7
/dev/sda3 is EXT4 partition / for Ubuntu

/dev/sdb is a 1 TB Western Digital Black Drive bought ~ 1 year ago. Normal 512 byte sectors.
/dev/sdb5 is EXT4 /home for Ubuntu
/dev/sb1 is NTFS used as a Storage drive for both systems

/dev/sdc1 is the drive in question. A 2 TB WD Green drive with 4096 byte sectors.

The testing included me formatting both drives with a variety of file systems and throwing things at them ranging from Ubuntu ISO's and Music/Movie files. All transfers were drive to drive to ensure I was "copying" and not just "moving". I got the speeds from the file transfer dialogue.

Results:

One 2 TB EXT4 partition on /dev/sdc1 was ~60 MB/s after formatting. Rebooting brought me down to ~330 KB/s.

One 2 TB EXT4 partition on /dev/sdc1 was ~60 MB/s after formatting using the parted method outlined in the opening post. Rebooting brought me down to ~ 1 MB/s

These results don't differ from the stuff I mentioned above.

New Stuff:

One 2 TB EXT3 partition on /dev/sdc1 was ~ 60 MB/s after formatting. Rebooting brought me down to ~ 330 KB/s. Same as before. 

One 2 TB EXT3 partition /dev/sdc1 was ~2 MB/s after formatting using the parted method detailed above. This is 2x faster than was seen during testing with EXT4.

The fun stuff! 

One 2 TB NTFS partition on /dev/sdc1 was 60 MB/s freshly formatted and after reboot. No optimizing operations were performed.

I made a small ext4 partition on /dev/sdb (/dev/sdb2) on the 1 TB WD Black drive with normal sectors to test if there was an issue with EXT4/3 on my system. Transferring to /dev/sdb2 both in NTFS and EXT4 revealed ~ 60 MB/s speeds before and after reboot.
[B]
Conclusion[/B]: There is still something going on with 4096 byte sectors in EXT4 and EXT3 that is not going on with the same drive formatted as NTFS (from gparted), regardless of the way one arranges the sectors. As was expected the 1 TB drive with 512 byte sectors was unaffected by either NTFS or EXT4. 

The file system of the drive "sending" the data did not seem to affect the rate at which the drive "receiving" the data was able to write it. Using the latest example /dev/sdb2 still received data at 60 MB/s regardless of whether the drive sending it /dev/sdc1 was in NTFS or EXT4. The same holds for all the other tests.

Unfortunately, NTFS, the non-native solution, is the best option for me to format my 2 TB WD drive with 4096 byte sectors to achieve maximum performance. EXT3 would be the second best assuming I were to use the parted method outline above. 

I hope this is able to help someone in the future, even though it was completely non-scientific in nature. I'll give NTFS a try for the next few days to see if my words above hold true and if necessary report back.

I would love to see a solution in which I can use a native file system on this drive and still get maximum performance from it. If anyone has suggestions or would like me to run some more tests I would love to hear from you.

srs5694, I guess this could still be a caching issue (since NTFS wouldn't be affected by the caching solutions of the kernel and the native file systems), but I'm too uneducated in the world of these things to venture a guess.

---

### Post by srs5694 on 2010-05-31
> **psych1610 said:**
> **Conclusion**: There is still something going on with 4096 byte sectors in EXT4 and EXT3 that is not going on with the same drive formatted as NTFS (from gparted), regardless of the way one arranges the sectors. As was expected the 1 TB drive with 512 byte sectors was unaffected by either NTFS or EXT4.

I have no new suggestions for what to try; however, I'd like to point out that you're focusing on the physical sector size as the cause without evidence. All you know is that the newer 1 TB drive is performing poorly compared to the older 1 TB drive. These two drives differ in many ways aside from their physical sector sizes, and the poor performance could be a result of any of these differences. Unfortunately, I can't give a lot of specifics about these differences or suggest methods to test them, since I don't know the details. They are (or could be) things like drive firmware, drive cache size, number of platters, interface circuitry details, etc. In fact, given that this particular problem is not being reported by everybody who buys one of these drives suggests that the true cause is not simply the sector size, but some interaction between an unknown factor (possibly the sector size, possibly something else) and something specific about your computer or configuration (SATA controller, driver options, etc.).

---

### Post by psych1610 on 2010-05-31
Excellent point! I never considered anything else for a second. Given that these drives were bought almost a year apart and are different not only in size but in cache as well (and who knows what else) I guess I should concede it's possible that just about any unknown or known variable could be causing me to have this issue.

Thanks for pointing that out. Given that NTFS handles so well on Ubuntu (in my experience, I should be thankful I have found a workaround to this.

---

### Post by SeePU on 2010-05-31
Any reason to have your drives set up that way?

I'd have Windows 7 on the 80GB drive - only.  

The WD Black for Ubuntu partitions and the 1GB WD Green for NTFS, one partition.  

I'm now a firm believer in having Windows and Linux on separate drives except when you need a Windows OS for updating/upgrading the BIOS of the mobo.  But, you could use XP for that.

However, with your situation, it sounds strange but I agree with the other poster.  Sounds like a SATA controller issue.  

The 'change in speed' when you reboot sounds peculiar.  I would google that 'change in speed after reboot' and the WD10EARS drive so like this:

'change in speed after reboot + WD10EARS' 

...just to see if anyone else has experienced a similar issue.

The 50 to 60MB transfer rate sounds typical for the Green drives and that's what you should get all the time if it's connected via SATA or eSATA.

---

### Post by psych1610 on 2010-05-31
> **SeePU said:**
> Any reason to have your drives set up that way?

I'd have Windows 7 on the 80GB drive - only.  

The WD Black for Ubuntu partitions and the 1GB WD Green for NTFS, one partition.  

I'm now a firm believer in having Windows and Linux on separate drives except when you need a Windows OS for updating/upgrading the BIOS of the mobo.  But, you could use XP for that.

However, with your situation, it sounds strange but I agree with the other poster.  Sounds like a SATA controller issue.  

The 'change in speed' when you reboot sounds peculiar.  I would google that 'change in speed after reboot' and the WD10EARS drive so like this:

'change in speed after reboot + WD10EARS' 

...just to see if anyone else has experienced a similar issue.

The 50 to 60MB transfer rate sounds typical for the Green drives and that's what you should get all the time if it's connected via SATA or eSATA.

No real reason why I partitioned that way, it just made sense to me. I rarely use Windows 7 and thought having / on a 10k RPM drive would give me some speed increases. Originally, the 1 TB drive was storage and was formatted in NTFS because thats just what I used in Windows.

The 2 TB drive is a new addition and I figured I would just use it for backups, torrenting, and any other uses I could think of. I could (and probably will) come up with a new partitioning scheme on my days off this week to take into account my new drive. 

*Edit* This may be hardly the place nor the time, but I'm wondering why you're such a firm believer in Windows and Linux on separate drives. I've not encountered any problems doing it like this, but perhaps you know something I just don't. If there is a good enough reason I could spend some time trying to rearrange everything this week.
Thanks for the tips

---

### Post by SeePU on 2010-06-01
> **psych1610 said:**
> No real reason why I partitioned that way, it just made sense to me. I rarely use Windows 7 and thought having / on a 10k RPM drive would give me some speed increases. Originally, the 1 TB drive was storage and was formatted in NTFS because thats just what I used in Windows.

The 2 TB drive is a new addition and I figured I would just use it for backups, torrenting, and any other uses I could think of. I could (and probably will) come up with a new partitioning scheme on my days off this week to take into account my new drive. 

*Edit* This may be hardly the place nor the time, but I'm wondering why you're such a firm believer in Windows and Linux on separate drives. I've not encountered any problems doing it like this, but perhaps you know something I just don't. If there is a good enough reason I could spend some time trying to rearrange everything this week.
Thanks for the tips
Well, my drives are set up similar to yours with Windows and Linux on the same drive.  But, I am going to re-do my partition scheme eventually.   I use XP but might be using Windows 7 later.   Right now, my Windows partition for XP is small, 30GB and I partitioned my 320GB drive into several Linux ones.  But, I want to use VirtualBox soon so I'll want a 100GB partition, for e.g..  I also have two 1TB drives for storage.  They both only have the one partition.  

The reason I suggest separate drives is that I think it will be easier to manage in the long run.   The problem is Grub and the fact you'll need 'different' info for handling how Windoze 'wants' to be the only OS/drive.  But, I read there are several 'how-to's' for handling that situation.  I think it would be easier to tackle issues related to either Linux or Windoze without worrying about effecting the boot up of the other.  When you want to re-do or re-install one of the operating systems, you don't have to worry about accidentally doing something to the other operating system.   I think it's an easier situation to deal with compared to Linux/Windows on the same drive, in the long run.  However, I have not tried this setup yet so take my recommendation with a grain of salt.  I will try it and then determine if my speculation holds water or not. :)

I would read a lot and have the 'solutions' and instructions printed out or on another nearby computer before pursuing the new setup, too.

---

### Post by psych1610 on 2010-06-01
I see what you're saying. It does make some sense that that method of doing things might work out easier. 

To ere on the safe side I'm not going to do anything right now since what I have works well and I'd hate to run the risk of breaking things. The next time I reinstall from scratch (10.10 anyone!) I'll probably revisit this.

Thanks!

---

### Post by uljanow on 2010-06-01
Lucid has the latest fdisk which aligns the first partition at a 1M boundary. That should work for 4k disks and SSDs.

---

### Post by Rizlaw on 2010-06-08
> **uljanow said:**
> Lucid has the latest fdisk which aligns the first partition at a 1M boundary. That should work for 4k disks and SSDs.

I have several Western Digital 2TB Green Advanced Format drives. Using Ubuntu 10.04 and "g parted" (0.5.1) I have successfully formatted these drives to a single ext4 partition by:

1. entering a "1" in "Free space preceding (MiB)" 

   [NOTE: entering "1" will result in a starting sector of 2048 which is, from what I have read, where Microsoft starts all Advanced Format drives formatted under Win 7).

2. removing the check in the box "Round to cylinders"

3. make sure the WD Advanced Format drive does NOT have any pins jumpered. Jumpering pins 7 - 8 is ONLY for a single partition WinXP setup.

After the format is finished you can check it with: ```
sudo fdisk -lu /dev/sd***x** * 
``` (replace "x" with your drive letter).

For a WD EARS 2TB Green HD, you should see something like this: 


```
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b17b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907024064  1953511008+  83  Linux
```

You can also read the 10.04 Release Notes which state:


> **Partition alignment changes may break some systems**

By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries. This ensures maximum performance on many modern disks, particularly solid state drives but also new "Advanced Format" disks with physical sectors larger than the traditional 512 bytes. Very few systems nowadays need the old alignment, used in the days of MS-DOS when it was useful for partitions to start at the beginning of a cylinder.

In some rare cases, optimal alignment may cause problems. Some BIOS implementations (those on Asus P5P800-MX and Asus P5GZ-MX motherboards) have been reported to hang after installation. It may be difficult to install Microsoft Windows XP and older after installing Ubuntu, although more recent versions of Windows should be compatible with optimal alignment and indeed may produce it themselves. If you find that you need to use the old cylinder alignment instead, then add the partman/alignment=cylinder boot parameter when starting the installer. (551965) 

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)


Hope this helps somebody.

---

### Post by psych1610 on 2010-06-08
Appreciate the tips. I may just try this out and see if I can get the disk to run efficiently.

---

### Post by hysterix` on 2010-06-22
> **Rizlaw said:**
> I have several Western Digital 2TB Green Advanced Format drives. Using Ubuntu 10.04 and &quot;g parted&quot; (0.5.1) I have successfully formatted these drives to a single ext4 partition by:

1. entering a &quot;1&quot; in &quot;Free space preceding (MiB)&quot; 

   [NOTE: entering &quot;1&quot; will result in a starting sector of 2048 which is, from what I have read, where Microsoft starts all Advanced Format drives formatted under Win 7).

2. removing the check in the box &quot;Round to cylinders&quot;

3. make sure the WD Advanced Format drive does NOT have any pins jumpered. Jumpering pins 7 - 8 is ONLY for a single partition WinXP setup.

After the format is finished you can check it with: ```
sudo fdisk -lu /dev/sd***x*** 
``` (replace &quot;x&quot; with your drive letter).

For a WD EARS 2TB Green HD, you should see something like this: 


```
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b17b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907024064  1953511008+  83  Linux
```You can also read the 10.04 Release Notes which state:




[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)


Hope this helps somebody.

 Hello Rizlaw.  Do you know of any way to switch the raid configuration for the western digital drives other than using the wd drive manager tool in windows?  Is it possible to get the status of both drives in linux if using a raid 1 configuration, or is windows the only option for checking the western digital raids.

---

### Post by rjwaldren on 2010-07-10
Please report these things to WD.  There is a suggestion in the WD idea forum to to release a non-emulated 4k firmware for the EARS drives.  It would be a great benefit to everyone except those still on XP.  The more noise that gets made the more like they are to appease us, so open bugs at WDC and annoy the crap out of them.

[http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347](http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347)

---

### Post by xscd on 2010-11-18
> **srs5694 said:**
> Well, that disk's partition is properly aligned, assuming the jumper is not set -- the start sector number of 64 is divisible by 8 ...

However, the end sector of his advanced format drive, 3907029134, is not divisible by 8. Might that be a problem?

3907029134 / 8 = 488378641.75

---

### Post by psusi on 2010-11-18
> **xscd said:**
> However, the end sector of his advanced format drive, 3907029134, is not divisible by 8. Might that be a problem?

3907029134 / 8 = 488378641.75

No.  The NUMBER of sectors is divisible by 8, but since the first sector is 0, the last will always be one less.

---

### Post by xscd on 2010-11-18
> **psusi said:**
> No.  The NUMBER of sectors is divisible by 8, but since the first sector is 0, the last will always be one less.

Ah, yes. :) Thank you. The number of blocks listed for the partition on his hard drive is indeed divisible by 8.

---

### Post by srs5694 on 2010-11-19
For that matter, the number of sectors in a partition is irrelevant, assuming the filesystem's data structures are laid out relative to the first sector of the partition rather than relative to the last sector of the partition. I'm not an expert on filesystem design, but my suspicion is that the authors of mkfs utilities would lay everything out relative to the first sector, and if they allocate in blocks of sectors, they'd just ignore any "extra" sectors in a partition -- that is, if they access data in 4 KiB (8-sector) blocks, and if the partition has, say, 80,002 sectors, they'd just ignore those last two sectors. Any other approach just seems like extra work (and greater opportunity for bugs to creep in) to me.

---

