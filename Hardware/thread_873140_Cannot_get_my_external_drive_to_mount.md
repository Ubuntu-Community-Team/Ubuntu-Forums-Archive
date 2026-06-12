---
title: "Cannot get my external drive to mount"
date: 2008-07-28
forum: Hardware
---

### Post by danniogier on 2008-07-28
Hi guys, I am hoping you can help as I have run out of ideas here!
I have an Advent laptop and have got windows vista and ubuntu 8.04 installed in a dual-boot setup. All of my music is on my external packard bell usb drive, and no matter what i do i CANNOT mount the thing!

It shows up in my places menu as DATA but when i click the mount button I get an error message saying " Invalid mount option when attempting to mount the volume 'DATA'"

I have tried to manually mount and force mount through terminal with no luck.

Fdisk -l gives me this:

danni@danni-laptop:~$ sudo fdisk -l
[sudo] password for danni: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a1076a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702        6143    43709961    7  HPFS/NTFS
/dev/sda3            6144        6205      498015   82  Linux swap / Solaris
/dev/sda4            6206       14593    67376610   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09def504

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

and dmesg, amongst a lot of other things, gives me this in relation to the drive i want to mount:

[  207.977444] usb-storage: device found at 3
[  207.977451] usb-storage: waiting for device to settle before scanning
[  208.585750] usb-storage: device scan complete
[  208.586377] scsi 7:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  208.606314] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  208.607298] sd 7:0:0:0: [sdb] Write Protect is off
[  208.607305] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  208.607310] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  208.608781] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  208.609306] sd 7:0:0:0: [sdb] Write Protect is off
[  208.609313] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  208.609317] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  208.609323]  sdb: sdb1
[  208.632934] sd 7:0:0:0: [sdb] Attached SCSI disk
[  208.633016] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  209.078214] UDF-fs: No VRS found
[  209.128559] ISOFS: Unable to identify CD-ROM format.
[  244.323655] FAT: invalid media value (0xb9)
[  244.323668] VFS: Can't find a valid FAT filesystem on dev sdb.
[  347.559101] CPU0 attaching NULL sched-domain.
[  347.559111] CPU1 attaching NULL sched-domain.
[  347.576862] CPU0 attaching sched-domain:
[  347.576870]  domain 0: span 03
[  347.576874]   groups: 01 02
[  347.576881] CPU1 attaching sched-domain:
[  347.576885]  domain 0: span 03
[  347.576888]   groups: 02 01
[  350.829075] usb 7-1: USB disconnect, address 3
 

Sorry this is a bit all over the place, I have tried so many different things my head is in knots!

Any help will be greatly appreciated!

I should also add that this drive works fine on vista, it was properly disconnected when it was last used, and i can mount other drives in ubuntu with no problems...

HELP!!!

---

### Post by sstvinc2 on 2008-07-31
When you try to manually mount it, are you including "-t vfat" in your command?

The simple (although probably more irritating) solution, in my opinion, would be to back up the data on your external drive and reformat it as NTFS.  Ubuntu has had no problems with NTFS for me, and I think Linux in general doesn't really like to deal with FAT disks.  Also, Vista will obviously have no problem with the NTFS drive.

You could reformat it as ext3 and use ext2ifs [http://www.fs-driver.org/]("http://www.fs-driver.org/") to mount it in windows (very easy, one-time shot), but you'd have to install ext2ifs on any windows machine that you wanted to use it on, so you probably should just stick with the NTFS route if you do decide to reformat.

---

### Post by jjwoznia on 2008-07-31
Just for starters, sstvinc2, Linux doesn't really have issues with FAT. DOS used FAT back in the day,and linux has been able to read/write FAT since around that time. Yes it has evolved over the years to accommodate for size, but FAT16 and FAT32 are very usable in linux. Good ntfs support is "brand new" in linux as of like 6-12 months ago acrossed all main distros. Every ntfs driver project before that failed miserably, they were always buggy and caused a bunch of read write errors. I am definitely not knocking your fix b/c I have a colleague that mentioned ntfs external storage seems to work fine and dandy.

As for the original issue, to prevent having to reformat the drive, danniogier, you should check out the post I made over on this other thread:

[http://ubuntuforums.org/showthread.php?t=420145&page=2](http://ubuntuforums.org/showthread.php?t=420145&page=2)

Drive mode for the lifedrive is basically a usb storage drive and a it also acts a card reader if there is a secure digital card in the slot. So if you adjust my fix a little bit, it should work the same way.

The real issue is something has been changed and now Ubuntu post 8.04 doesn't like usb storage devices. I also have just a conventional Sandisk usb card reader that doesn't work. Give my method from the other post a try. It is a permanent fix if you want it to be, but it is probably not the best fix. Let me know how it goes.

---

### Post by sstvinc2 on 2008-07-31
This has since been clarified for me by someone else.  I do remember not having NTFS support in Linux (which is why my inter-OS drives are always ext3, I suppose).  But FAT partitions have issues with Linux file permissions and ownership, so it's risky to use for any drive with OS- or application-critical files on it.  At least, that's my understanding.  So non-critical files (from the OS's standpoint: music, movies, documents, etc) are fine if you feel the need to use FAT.

---

