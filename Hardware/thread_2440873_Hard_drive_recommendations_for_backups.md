---
title: "Hard drive recommendations for backups ?"
date: 2020-04-16
forum: Hardware
---

### Post by oygle on 2020-04-16
Needing a 2TB external hard drive for backups. I have been informed by Seagate that their external hard drives are only compatible with Windows or Mac. Does anyone have any recommendations for hard drives to backup Linux/Kubuntu data please ?

Some info - [Linux OS Support for Disk Drives Beyond 2.2 TeraBytes (TB)]("https://www.seagate.com/au/en/support/kb/linux-os-support-for-disk-drives-beyond-22-terabytes-tb-218575en/") and [(SOLVED) Buying a new external hard drive]("https://forums.linuxmint.com/viewtopic.php?t=294892")

---

### Post by CatKiller on 2020-04-16
Drives are drives. There's no specific OS compatibility.

All drive manufacturers have bad spells. Pick any manufacturer you like and you'll be able to find horror stories about one model or another that "ate all my data."

Multiple redundant versioned backups are the way to go: automatic backups one place, manual backups another place, offsite backups somewhere else. The failure rate of any part of that doesn't really matter then, because they're redundant. It's never been easier or cheaper to do it that way.

---

### Post by ajgreeny on 2020-04-16
Seagate obviously don't know enough about Linux to tell you anything useful; I am using a 2TB external USB3 disk for my backups with no problems at all.

They might not actively support its use with Linux but I suspect also that they do not actually say that it won't work, and you therefore use it at your own risk.

The disk I have is brilliant, fast and compact, a **Seagate Expansion Portable** drive, now formatted to ext4.  No doubt it came with NTFS but that is hopeless as I don't have Windows to repair any filesystem problems that might arise, and NTFS is hopeless dealing with Linux permissions.

The first of your links points to an old discussion; note the kernel versions mentioned; 2.6.35, which I think was in the first versions of Ubuntu, 16 years ago, so forget about that.  The second link to the Linuc Mint discussion is much more as I have now suggested; just forget about any of the software which might come on the disk and completely reformat it as you want.

---

### Post by SeijiSensei on 2020-04-16
I've been writing backups to this device every night for a couple of years now.

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817?Item=N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817?Item=N82E16822178817)

Never had a hiccup.

---

### Post by oygle on 2020-04-16
> **CatKiller said:**
> Drives are drives. There's no specific OS compatibility.

Yes, I have only just realised the external drive i have been using for about 10 years (500 Gb and starting to fail) is a Seagate...lol  :)

> **CatKiller said:**
> Multiple redundant versioned backups are the way to go: automatic backups one place, manual backups another place, offsite backups somewhere else. The failure rate of any part of that doesn't really matter then, because they're redundant. It's never been easier or cheaper to do it that way.

Yes, agreed, redundancy is the way to go. For now, I just use Beyond Compare, easy to use and the 'synchronise' function is very quick. But there is no redundancy there, it is simply updating on a mirror basis.

> **ajgreeny said:**
> Seagate obviously don't know enough about Linux to tell you anything useful; I am using a 2TB external USB3 disk for my backups with no problems at all.

Thanks, good to know that others are using Seagate successfully.

> **ajgreeny said:**
> They might not actively support its use with Linux but I suspect also that they do not actually say that it won't work, and you therefore use it at your own risk.

Yes, good point, they don't actually say it doesn't work.

> **ajgreeny said:**
> The disk I have is brilliant, fast and compact, a **Seagate Expansion Portable** drive, now formatted to ext4. 

When I get it, I'll just use Partition Manager to format to EXT4. I don't use Windows, other than an old laptop running inverter monitoring software. It's easier to just backup that up onto a USB stick as it's only a few Mb.

> **ajgreeny said:**
> The first of your links points to an old discussion; note the kernel versions mentioned; 2.6.35, which I think was in the first versions of Ubuntu, 16 years ago, so forget about that.  The second link to the Linuc Mint discussion is much more as I have now suggested; just forget about any of the software which might come on the disk and completely reformat it as you want.

I didn't realise the first link was so old. Yep, format is the way to go.

> **SeijiSensei said:**
> I've been writing backups to this device every night for a couple of years now.

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817?Item=N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817?Item=N82E16822178817)

Never had a hiccup.

Thanks, I may need one very similar, as photos and videos from mobile phones take up a fair bit. The Kubuntu is only about 240 Gb, and takes about 4 to 5 hours to the current (failing) external. It is only USB 2 , so very slow.

---

### Post by MartyBuntu on 2020-04-17
> **ajgreeny said:**
> Seagate obviously don't know enough about Linux to tell you anything useful; 

Seagate knows enough not to cross their corporate partners at Microsoft and Apple...and give customers a reliable open-source alternative.

---

### Post by TheFu on 2020-04-17
5-10 years ago, a few USB external disks didn't implement the full USB-storage protocol and there were some that didn't work with Linux.  People had to really watch the USB interfaces used.  That's mostly been handled today with workarounds in software on the Linux side.  I have some HW from 2010 that still doesn't handle USB3 speeds well, but my research about it is that the motherboard from that time just didn't have sufficient bandwidth for anything except the x16 GPU.

So ... my only real recommendations for 2TB external disks are this:
[LIST]
[*]Don't get Seagate for this size. Check out the BackBlaze reliability reports for why.
[*]Avoid the 2.5inch size, get the 3.5inch disks, which are faster and often we can "shuck" the enclosure to find a quality RED HDD inside which is worth 50% more than the price paid for the disk+enclosure.  WD does this fairly often.
[*]Get an enclosure with external power so the full available speed can be used.
[*]Don't worry about USB3 or USB 3.1 ... no spinning HDDs can come close to either.
[/LIST]

So, I have a 2TB WD external WDC WD20EARX-00PASB0 that has been going strong for more years than I remember - ok 55576 hrs (6.3 yrs) according to SMART today.  Still looks good, SMART-wise.  But nobody here has statistical samples counts.  The 2 Seagate 2TB disks that I had, which failed just after 1 yr don't prove anything - except that I was really happy my credit card doubled the warranty so I could get better replacement HDDs.

---

### Post by SeijiSensei on 2020-04-19
> **TheFu said:**
> So, I have a 2TB WD external WDC WD20EARX-00PASB0 that has been going strong for more years than I remember - ok 55576 hrs (6.3 yrs) according to SMART today.
Hmm. Mine's just a young pup then at 31,558 hours or about 3.6 years.

---

### Post by kurt18947 on 2020-04-19
I just purchased a SATA disk enclosure, I think the brand is Orico. I have a 500 GB. 3.5" spinning hard drive in it. Easy to swap out drives as desired. That always made more sense to me than a purpose-built backup device. I guess some backup devices come with backup software but I'm pretty sure those only work with Windows & maybe Mac. There are GUIs for Rsync  and backup software for Linux so I don't see that having included backup software is that big a deal.

---

### Post by oygle on 2020-04-23
Ended up purchasing a Seagate 4TB backup plus.Difficult to tell if it is 3.5 " disk. Have backed up what was on the HDD, as some of it was warranty information. Now I presume I can simply format the drive to EXT4, is that correct ?

I did a test with a small directory and it took 10 minutes to backup 4 Gb. Much SLOWER than the old hard drive (Seagate) using usb 2.  But need to test after reformatting (it is NTFS now), as there were a number of errors because of long filenames.

---

### Post by Dennis N on 2020-04-24
> Now I presume I can simply format the drive to EXT4, is that correct ?
You format partitions, not drives. Before you format, you need to make a new partition table on the drive. The best type is a GPT partition table (rather than MS-DOS). Then, create at least one partition - when you do this, you normally have the option to format the new partition at the same time. It's here where you choose ext4 as the format for the partition's file system.

---

### Post by oygle on 2020-04-24
> **Dennis N said:**
> Before you format, you need to make a new partition table on the drive. The best type is a GPT partition table (rather than MS-DOS). Then, create at least one partition - when you do this, you normally have the option to format the new partition at the same time. It's here where you choose ext4 as the format for the partition's file system.

Okay thanks. After the (EXT4) format, copied that 4 Gb path to the external and it only took half the time compared to copying to an NTFS partition. Five minutes for 4 Gb. It still seems a bit slow compared to the (very old) external drive connected, which could only use usb 2.  Could there be a usb driver issue ?

---

### Post by Dennis N on 2020-04-24
> Five minutes for 4 Gb. It still seems a bit slow...

When you are backing up (using rsync for example), you would only be copying modified source files and adding new files to the backup disk. So your wouldn't be transferring 4 GB each time. It is what it is.

---

### Post by SeijiSensei on 2020-04-24
I'll ask the obvious question.  Are you sure you're connected to a USB 3.0 port?

I just ran a test on my Seagate.  I copied a 4.1 GB ISO file from the computer's hard drive to the external . It completed in 37 seconds.  The source file resides on a software RAID1 array.  That improves read performance since blocks can be read from both drives simultaneously, but it would hardly matter enough to explain the difference between 37 seconds and five minutes.

My Seagate drive has one partition using GPT and ext4 formatting.

```

$ time sudo cp CentOS-7-x86_64-DVD-1503-01.iso /media/external

real    0m37.597s
user    0m0.215s
sys     0m4.275s

```

**Update:** I wanted to eliminate the RAID issue, so I copied the file to my primary SATA drive.  (That took 57 seconds!)  Copying the file from that drive to the Seagate took 37 seconds like before.

This is on a system running CentOS 6.1 so I doubt my drivers are more up-to-date than those that come with current Ubuntu distributions.

---

### Post by rbmorse on 2020-04-24
Your Seagate 4TB Backup Plus portable hard drive uses a 2.5 inch disk drive.

---

### Post by oygle on 2020-04-24
> **SeijiSensei said:**
> I'll ask the obvious question.  Are you sure you're connected to a USB 3.0 port?

I did check with **lsusb** and then passed the port ID and it said USB 3.0 . Also checked the user manual as there are 2 USB ports, and the one I'm using is definitely USB 3.0

> **SeijiSensei said:**
> I just ran a test on my Seagate.  I copied a 4.1 GB ISO file from the computer's hard drive to the external . It completed in 37 seconds.  The source file resides on a software RAID1 array.  That improves read performance since blocks can be read from both drives simultaneously, but it would hardly matter enough to explain the difference between 37 seconds and five minutes.

That's a huge difference. This morning there was some improvement. I deleted the partitions that were there, including the SeaGate one. Then used KDE Partition Manager to format the only partition of about 3.6 TB . Then copied a 20 Gb path to the external and it only took 8 minutes. So, thinking it was now working, tried some other big paths, but it just gets stuck on even copying a few hundred Mb.  Should I use GPT instead of KDE Partition Manager ?  Plus is there a max size of partitions (EXT4) with Ubuntu , like a 2 TB limit or similar ?

I tried using smartmontools but it ...

```
sudo smartctl -i /dev/sdb
```

> smartctl 7.0 2018-12-30 r4883 [x86_64-linux-5.3.0-46-generic] (local build)
Copyright (C) 2002-18, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Read Device Identity failed: scsi error unsupported field in scsi command

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

> **SeijiSensei said:**
> My Seagate drive has one partition using GPT and ext4 formatting.

```

$ time sudo cp CentOS-7-x86_64-DVD-1503-01.iso /media/external

real    0m37.597s
user    0m0.215s
sys     0m4.275s

```

**Update:** I wanted to eliminate the RAID issue, so I copied the file to my primary SATA drive.  (That took 57 seconds!)  Copying the file from that drive to the Seagate took 37 seconds like before.

This is on a system running CentOS 6.1 so I doubt my drivers are more up-to-date than those that come with current Ubuntu distributions.

I can't understand why this new drive is so slow ? Even started to look at Dell BIOS updates, and to check on drivers for USB. But nothing really. Possibly there is a log file to check, in the system somewhere.  There is also, what seems to be a video problem ?? Try viewing paths in Dolphin on the external and it takes a long time to open the paths. I'm not using the NVIDIA drivers, just the standard ones that come with Kubuntu 19.10 . When I notice the video slowness, thinking it may be overall resources, a quick look at 'System Activity' ensures there is no high CPU usage. Thanks for your help

> **rbmorse said:**
> Your Seagate 4TB Backup Plus portable hard drive uses a 2.5 inch disk drive.

Thanks , yes I only realised that today.

---

### Post by oygle on 2020-04-24
Have just run the following on the laptop HDD, not the external ..

```
sudo gdisk -l /dev/sda
```

> GPT fdisk (gdisk) version 1.0.4

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Warning: Invalid CRC on main header data; loaded backup partition table.
Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!
Main header: ERROR
Backup header: OK
Main partition table: ERROR
Backup partition table: OK

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Model: ST1000LM024 HN-M
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 27C37952-7E2D-4D49-A4D7-179A06BD2895
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5487 sectors (2.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        34762749   16.6 GiB    8300  Linux filesystem
   5        34762752        44527615   4.7 GiB     8200  Linux swap
   6        44529664      1953523711   910.3 GiB   8300  Linux filesystem


---

### Post by oygle on 2020-04-25
> **SeijiSensei said:**
> 

```

$ time sudo cp CentOS-7-x86_64-DVD-1503-01.iso /media/external

real    0m37.597s
user    0m0.215s
sys     0m4.275s

```

Thanks for the tip on the **time** command. I tried it with a 2.1 Gb .iso

```
time  cp  kubuntu-19.10-desktop-amd64.iso     /media/oygle/Backups/1/home/oygle
```

> real    0m14.269s
user    0m0.039s
sys     0m3.469s


Hmm, so a **cp** is very fast, but copying in Dolphin or Beyond Compare takes a very long time, or often freezes on displaying directories ??

---

### Post by Dennis N on 2020-04-25
> Have just run the following on the laptop HDD, not the external ..

Comments: 

**gdisk** is intended only for GPT disks. That's probably causing the warnings. Use **fdisk** instead with MS-DOS disks like the internal drive. Newer versions of fdisk now work on both MS-DOS and GPT disks.

If the new external drive is 2.5", it may run at 5400 rpm, which would account for at least some of the increase in times you notice. 3.5" disks run at 7200 rpm.

---

### Post by oygle on 2020-04-25
> **Dennis N said:**
> **gdisk** is intended only for GPT disks. That's probably causing the warnings. Use **fdisk** instead with MS-DOS disks like the internal drive. Newer versions of fdisk now work on both MS-DOS and GPT disks.

If the new external drive is 2.5", it may run at 5400 rpm, which would account for at least some of the increase in times you notice. 3.5" disks run at 7200 rpm.

Okay thanks about the need to use **fdisk**. Yes, there could be a speed difference. I can't run **smartctl** on the new external drive for some reason. Just copied 174.3 Gb (10,003 files, 939 sub-folders) in 49 minutes.

```
~/Downloads$ time  cp -R  *    /media/oygle/Backups/1/home/oygle/Downloads/
```

> real    48m53.391s
user    0m5.785s
sys     7m40.478s

Not sure why any GUI file copy is taking such a long time, with freezing, etc ???  The following is from 5 years ago, but the command file copy is much faster than Dolphin - [https://forum.kde.org/viewtopic.php?f=223&t=124677](https://forum.kde.org/viewtopic.php?f=223&t=124677)

---

### Post by oygle on 2020-04-26
Has anyone had experience with using [restic]("https://restic.net/") on Ubuntu ?

---

### Post by TheFu on 2020-04-26
Beware that time output is for the cp side of the command. If you have lots of RAM, RAM will be used to buffer as the writes continue to the slow 2.5inch disk.  Hopefully, you have it using an external power adapter, not just USB power.  

Could have sworn that I warned against using 2.5inch disks AND suggested using an external power adapter.  Horse --> water.

GUIs are slow. I wouldn't use cp for a backup tool either.  If you just want to sneak-net files around, that's fine, great, good.  Versioned backups aren't hard to create and pretty easy to work with. They also need to capture not just the data, but the permission changes over time.  Different versions of software packages change the owner, group and file permissions. Capturing those changes over time is critical to having solid backups.  rsync with hard-linking doesn't accomplish that.

If you want backups, there are many better choices that are like rsync the first time, then faster than rsync for each version after that.  The most recent "backup" looks like any rsync mirror, but older versions can also be retrieved using a fairly simple command - 1 file, 57 files, entire directory structures, or an entire backup set restored with 1 command. You pick the date/revision to be restored.  Latest, 31 days ago, 69 days ago, whatever.  If you can run 

```
sudo rsync -avz source target
```
then you can run 
```
sudo rdiff-backup --exclude-special-files source target
```
To restore, **rsync** can be used or ```
sudo rdiff-backup -r target source
```
This isn't complicated until you want to be even more efficient and only backup specific areas, lists of manually installed packages, and capture some system settings like drive layouts so restoring to 100% new hardware isn't too hard.

---

### Post by oygle on 2020-09-12
> **TheFu said:**
> So ... my only real recommendations for 2TB external disks are this:
[LIST]
[*]Don't get Seagate for this size. Check out the BackBlaze reliability reports for why.
[*]Avoid the 2.5inch size, get the 3.5inch disks, which are faster and often we can "shuck" the enclosure to find a quality RED HDD inside which is worth 50% more than the price paid for the disk+enclosure.  WD does this fairly often.
[*]Get an enclosure with external power so the full available speed can be used.
[*]Don't worry about USB3 or USB 3.1 ... no spinning HDDs can come close to either.
[/LIST].

Thanks for your recommendations. Unfortunately, for some reason, I didn't get notifications and therefore missed seeing your post. Definitely the 3.5 inch disks are faster and as you say, external power is preferred. Oh well,, next time I buy one.  :)

Thanks for your tips/advice re rsync,cp, GUI's, etc.

---

