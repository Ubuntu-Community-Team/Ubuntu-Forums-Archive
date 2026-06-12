---
title: "Ubuntu Not Recognizing Internal Hard Drive"
date: 2015-04-08
forum: Hardware
---

### Post by robert171 on 2015-04-08
Ok so I'm rather new to Ubuntu so sorry if I sound stupid.

In my computer I have 2 80GB SSD's (One with Windows and one with Ubuntu) and a 3 TB Hard drive. When I boot into windows I see the 3 TB hard drive and one of the 80GB ssd's which is fine. When I boot into Ubuntu I see both 80GB ssd's but not the 3TB hard drive. I went into the disks program but the drive isn't shown there either. Any help is greatly appreciate.

---

### Post by Bashing-om on 2015-04-08
robert171; Hi ! Welcome to the forum.

Maybe best to see what the system sees for installed hard drives. This is better done, I think, in terminal as terminal is the lower level interface.

What returns:
```

sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we can start 'looking' at how/where the drive is mounted.

[INDENT][INDENT][INDENT]it is a process
[/INDENT][/INDENT][/INDENT]

---

### Post by robert171 on 2015-04-08
Here is what the terminal returns: 

robert@Robert:~$ sudo parted -l
[sudo] password for robert: 
Model: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  67.2GB  67.2GB  primary   ext4            boot
 2      67.2GB  80.0GB  12.9GB  extended
 5      67.2GB  80.0GB  12.9GB  logical   linux-swap(v1)




Model: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  80.0GB  80.0GB  primary  ntfs




Model: Seagate Backup+ BK (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  


robert@Robert:~$ sudo blkid
/dev/sda1: UUID="9f756ba6-239b-43b3-a796-c739a5c6d014" TYPE="ext4" 
/dev/sda5: UUID="0fe098ad-0610-49cd-ba9d-7610045062eb" TYPE="swap" 
/dev/sr0: LABEL="UDF Volume" TYPE="udf" 
/dev/sdb1: UUID="9AD6E0F4D6E0D195" TYPE="ntfs" 
/dev/sdc1: LABEL="Seagate Backup Plus Drive" UUID="7292794492790DBB" TYPE="ntfs" 

The seagate one is a external hard drive.

---

### Post by weatherman2 on 2015-04-08
A 1TB partition is showing up on /dev/sdc1 .  This is really a 3TB drive?

If this is truly a 3TB drive, then understand there are limitations to the maximum partition size readable under the old "MSDOS" partition tables (used for 20+ years in the Windows world, supported by Linux).  You can't have a partition size larger than 2.1TB.  To do that, you either need to use a new partition structure called GPT...or you can use special software to trick Windows into using a larger partition.  Seagate provides Disk Wizard to do that.

Looks like your Seagate drive does use an MSDOS partition table.  If you used Disk Wizard to see the whole 3TB drive, it's likely Ubuntu can't see it it then.

[http://www.seagate.com/support/downloads/beyond-2tb/](http://www.seagate.com/support/downloads/beyond-2tb/)

If this were a brand new 3TB drive, the easy solution would be to re-initialize it as a GPT partition table - unless you are using say Windows XP, which can't support GPT.  If you are using Windows 7 or 8, then you could do that and then Ubuntu would be able to see it too.  Of course, your Seagate drive probably has lots of data on it...

---

### Post by gordintoronto on 2015-04-09
Weatherman: as the OP said, the 1 TB Seagate is an external drive. There is no sign of the 3 TB drive.

Robert: how is the 3 TB drive formatted? How much data is on it? What version of Ubuntu are you using?

---

### Post by robert171 on 2015-04-09
Ok guys, I booted up windows and took some screenshots of what it says about the hard drive.

[http://gyazo.com/399d6bd9ce1d6c1eb34a2b52ed1361df](http://gyazo.com/399d6bd9ce1d6c1eb34a2b52ed1361df)
[http://gyazo.com/c4834cf3a10f2e95db18115a8eb700eb](http://gyazo.com/c4834cf3a10f2e95db18115a8eb700eb)
[http://gyazo.com/507233c4c2128f42ce1acd2d1057a396](http://gyazo.com/507233c4c2128f42ce1acd2d1057a396)

Turns out it's only a 2TB hard drive. (Oops)

Gordintoronto: I'm running the latest LTS version of Ubuntu so 14.04.2.

---

### Post by weatherman2 on 2015-04-09
How about a screenshot from Disk Management in Windows, showing partition types?

---

### Post by robert171 on 2015-04-09
Here you go: [http://gyazo.com/ceb21a1b72f0d06e232fe33b05ce1206](http://gyazo.com/ceb21a1b72f0d06e232fe33b05ce1206)

---

### Post by Mark Phelps on 2015-04-10
You formatted your 3TB drive as MBR -- and have lost an entire 1TB in the process!  For any drive larger than 2TB, you need to format it as GPT.

---

### Post by robert171 on 2015-04-10
I haven't done anything to it, I haven't ever formatted it, I just installed Ubuntu on an SSD and the hard drive wouldn't show up. Also it's a 2TB hard drive, I made a mistake saying that it was 3. So how can I fix it? (I'm new to Ubuntu so I don't know much about this sort of stuff)

---

### Post by Bashing-om on 2015-04-10
robert171; Yikes ;

well;
> 
I haven't done anything to it, I haven't ever formatted it, I just installed Ubuntu on an SSD and the hard drive wouldn't show up.

If there is nothing to be seen, there is nothing - we need to put a file system on that drive so it is seen.

What file system do you want ?
If only ubuntu is to be installed to that box, ext4 is a good choice
For sharing the drive between ubuntu and Windows, NTFS is a good choice.
bk
one can have multiple partitions in various file systems on a single hard drive.
While GParted is versatile and will handle the job ->
Windows' tools for Windows systems
ubuntu tools for ubuntu systems .
-----------------set up partitions and format them in the file system of choice.

[INDENT]betcha then
[INDENT][INDENT][INDENT][INDENT]we can see something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by user_of_gnomes on 2015-04-11
You should probably **NOT** follow bashin-om's advice unless you're looking to lose all that data I can see in the screenshot ... 

When you type "disks" and click on the 1TB partition, can you show me what the partition lay-out looks like?

---

### Post by robert171 on 2015-04-11
Is this what you're looking for? [http://gyazo.com/ceb21a1b72f0d06e232fe33b05ce1206](http://gyazo.com/ceb21a1b72f0d06e232fe33b05ce1206)

When I look for disks in Ubuntu the hard drive doesn't even show up (Unless it's this selected thing): [http://gyazo.com/33d638cb40b8e7d6cff794c6183a1971](http://gyazo.com/33d638cb40b8e7d6cff794c6183a1971) 

If you are confused by the 1TB Seagate drive in the terminal text that was an external hard drive I had accidently plugged in.

---

### Post by user_of_gnomes on 2015-04-12
It's disk 1 under Windows that we're talking about, right? Is it a USB-drive?

And no, it doesn't even show up indeed. What is selected in Disks is most likely your card reader.

---

### Post by robert171 on 2015-04-13
Yes, disk 1 is the one that's not working in Ubuntu. It is an internal hard drive. The Seagate one that's in the terminal text is an external USB drive that's working fine.

---

### Post by user_of_gnomes on 2015-04-13
Okay, that was confusing. What kind of controller is it connected to? Do any of the other devices connected to the same controller show up in Linux?

---

