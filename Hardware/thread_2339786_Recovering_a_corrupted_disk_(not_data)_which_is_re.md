---
title: "Recovering a corrupted disk (not data) which is resisting being wiped"
date: 2016-10-12
forum: Hardware
---

### Post by tdeith on 2016-10-12
I have an SSD whose partition table was corrupted while I was trying to move a dual-booted Windows into an EFI boot - I'm not positive on the how or why of the corruption. I am now booted into a live USB trying to recover the disk, which I have connected as an external via USB. My goal is ultimately to wipe the disk, including the partition table, and start this disk from scratch. I no longer care about partitions or their data. 

However, I can't get anything to wipe more than 8GB of the 512GB on the disk, and there are a variety of oddities with this disk which I can't make heads or tails from, and must be related. My best guess at an overall theme to the oddities is that there is a corruption in the disk causing two specific partition headers (is that a thing?) to be read back-to-back in a loop, such that those two partitions will freeze anything trying to read the SSD's partition data. 

Some interesting symptoms:

- *fdisk -l*, *blkid*, and *df -h* don't necessarily reach a consensus on what they're seeing regarding the drive. At the moment (now that I've ejected/inserted the drive a couple of times), *blkid* thinks the device is in /dev/sdd, *df -h* thinks the drive is in /dev/sdc, and *fdisk* doesn't see it. *df -h* is certainly right.

- None of my computers have successfully booted into BIOS (neither booting past BIOS nor  entering the BIOS settings) with this drive attached. The BIOS's  universally freeze while detecting hardware. This makes boot-based recovery tools (eg,  DBAN) difficult so far. It is also not fixed by resets-via-CMOS-battery-ejecting.

- Once booted into Ubuntu, when the disk is inserted by USB, Nautilus sees the drive, can mount the original partitions on the drive, and can successfully read their contents. However, each partition is listed about a hundred times, each entry with a different UUID attached to the partition. (This makes sense to me if the partition table is gone and partitions are being repeated.)

- Using *dd** if=/dev/zero of=/dev/sdX bs=1M* to try and overwrite the entire device resulted in only 8GB of 512GB being written before 'No space left on device' is returned. **These 8GB correspond to the 8GB occupied by one of the two repeating partitions, no more, no less. **I wish I could personally make inferences on this detail.

- GParted does not see the device, with the exception of one time: at that time, it saw 8GB of empty space, possibly written by *dd* above, and nothing else. Re-writing the partition table at that time had no effect.

- *testdisk* only sees 8GB of device, and doesn't find any partitions in scanning. (The cylindar/sector counts seem off too, but frankly I don't know enough to navigate *testdisk* confidently.)

I'm at a loss as to how else I can try to scrub whatever's corrupting this disk. My uneducated speculation is that there's some corruption in the disk causing seeking to go from the end to the start of the disk when looking for partitions, or something to that effect. 

*fdisk -l* output:
```

[... /dev/ramX ...]

Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.9 GiB, 16018046976 bytes, 31285248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0e0e8e70

Device     Boot   Start     End Sectors  Size Id Type
/dev/sda1  *          0 2902111 2902112  1.4G  0 Empty
/dev/sda2       2888004 2892739    4736  2.3M ef EFI (FAT-12/16/32)

```

*df -h* output - note that /dev/sdc3 - /dev/sdc255 are repeats of the same two partitions.
```

Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G  7.8G     0 100% /dev
tmpfs           1.6G   23M  1.6G   2% /run
/dev/sdb        1.4G  1.4G     0 100% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow            7.8G  262M  7.6G   4% /
tmpfs           7.8G  200K  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  192K  7.8G   1% /tmp
tmpfs           1.6G  108K  1.6G   1% /run/user/999
/dev/sdc12      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a91
/dev/sdc16      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a92
/dev/sdc10      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a9
/dev/sdc22      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a93
/dev/sdc24      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a94
/dev/sdc26      7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a95
/dev/sdc6       7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a96
/dev/sdc13      257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e731
/dev/sdc11      257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e73
/dev/sdc15      257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e732
/dev/sdc21      257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e733
/dev/sdc8       7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a97

... etc etc for many repetitions ...

/dev/sdc192     7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a996
/dev/sdc198     7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a995
/dev/sdc200     7.6G  3.3G  3.9G  46% /media/ubuntu/29ca7c9f-c33a-4360-8ed6-54befae126a997
/dev/sdc197     257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e7395
/dev/sdc195     257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e7397
/dev/sdc199     257G  236G  8.2G  97% /media/ubuntu/7778b2a1-9bf2-4648-9fa6-6f2643d83e7396

```

*blkid* output - note that the device is actually at /dev/sdc, and is reported as being in /dev/sdd here. I have no idea why this would be the case. Also note that everything from /dev/sdd3 - /dev/sdd255 are repeats:
```

/dev/loop0: TYPE="squashfs"
/dev/sdd1: UUID="4598-B2D3" TYPE="vfat"
/dev/sdd2: LABEL="Lovelybunchadata" UUID="64B21538B2151062" TYPE="ntfs"
/dev/sdd5: UUID="7778b2a1-9bf2-4648-9fa6-6f2643d83e73" TYPE="ext4" PTTYPE="dos"
/dev/sdd6: UUID="29ca7c9f-c33a-4360-8ed6-54befae126a9" TYPE="ext4"
/dev/sdd7: UUID="7778b2a1-9bf2-4648-9fa6-6f2643d83e73" TYPE="ext4" PTTYPE="dos"
/dev/sdd8: UUID="29ca7c9f-c33a-4360-8ed6-54befae126a9" TYPE="ext4"
/dev/sdd9: UUID="7778b2a1-9bf2-4648-9fa6-6f2643d83e73" TYPE="ext4" PTTYPE="dos"

... UUIDs change, but nothing else...

/dev/sdd254: UUID="29ca7c9f-c33a-4360-8ed6-54befae126a9" TYPE="ext4"
/dev/sdd255: UUID="7778b2a1-9bf2-4648-9fa6-6f2643d83e73" TYPE="ext4" PTTYPE="dos"
/dev/sda1: LABEL="ESD-USB" UUID="12C5-D03F" TYPE="vfat"

```


Thank you to anyone who might be able to help.

---

### Post by oldfred on 2016-10-12
Lets try gdisk. If drive is sdd.
sudo gdisk -l /dev/sdd

Did you by any chance use drive as installer and use dd to copy ISO to that drive?

With logical partitions in MBR(msdos), it is a linked list from one partition to the next & last partition has no link. If links get messed up, then you get repeating loop of partitions.
 sda60 error:Linked logical partition error
[http://ubuntuforums.org/showthread.php?t=1880513](http://ubuntuforums.org/showthread.php?t=1880513)
[http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions](http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions)

---

### Post by tdeith on 2016-10-12
*gdisk -l /dev/sdX *output: (drive is now sdb - kernel panic caused reboot.)

```

ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdb: 16313328 sectors, 7.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A1975D9B-7C21-4757-B170-548F69E0BF0C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 16313294
Partitions will be aligned on 2048-sector boundaries
Total free space is 16313261 sectors (7.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

The drive has never been used as an installation drive, and it has also never had an install media *dd*'d into it.

The partition linking makes some sense. I'm investigating the links you provided. Thanks for the help so far!

---

### Post by tdeith on 2016-10-12
Another interesting tidbit is that *sudo fdisk /dev/sdb *does give access to the drive (note - a reboot means the drive has moved from */dev/sdc* to *sdb*). The information it presents seems expected for the issue: 

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0xd28a030e.

Command (m for help): p
Disk /dev/sdb: 7.8 GiB, 8352423936 bytes, 16313328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd28a030e

Command (m for help): 

```

---

### Post by tdeith on 2016-10-12
Update:

Neither [http://ubuntuforums.org/showthread.php?t=1880513](http://ubuntuforums.org/showthread.php?t=1880513)
Nor [https://ubuntuforums.org/showthread.php?t=1849060](https://ubuntuforums.org/showthread.php?t=1849060) 

are not quite the same issue as I'm having. The closest was ghost partitions showing up from bad MBR chaining, but in either thread, the OP had the drive show up in its entirety for *fdisk*, and looks as though *dd *could read/write from the disk in its entirety. The best I can get is a single partition's worth of drive space (not the partition itself, though) to show up in *fdisk*, or be read/writable by *dd. *Why it is that only one partition's worth of disk is showing in *fdisk*, but other partitions on the same disk appear under the device (using *blkid* or *df*), is still beyond me.

---

### Post by oldfred on 2016-10-12
You  are looping with two UUIDs.

Go into fdisk's advanced mode and see if just a write fixes it.

 You can possibly repair a MBR partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

---

### Post by tdeith on 2016-10-12
No cigar:

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x28806548.

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

Expert command (m for help): r

Command (m for help): p
Disk /dev/sdb: 7.8 GiB, 8352423936 bytes, 16313328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x28806548


Command (m for help): v
Remaining 16313327 unallocated 512-byte sectors.

```

edit: Incidentally, after writing from *fdisk*, things are unchanged:

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sdb: 7.8 GiB, 8352423936 bytes, 16313328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab54d47e

Command (m for help): 


```

---

### Post by oldfred on 2016-10-13
It looks like you ran fdisk on sdb, but your issue was on sdc? Or did drive order change.
 > /dev/sdc3 - /dev/sdc255 are repeats 

---

### Post by tdeith on 2016-10-13
The Drive order changed, yes. (Reboot due to kernel panic as I tried running Ubuntu's "disks" program to explore the drive.)

Sorry for that confusion.

---

### Post by oldfred on 2016-10-13
Did you do a w from fdisk to force it to update partition tables?

---

### Post by tdeith on 2016-10-13
I did write with *w*, yes.

Full *fdisk* process which a smart man would have posted originally:

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

Expert command (m for help): r

Command (m for help): p
Disk /dev/sdb: 7.8 GiB, 8352423936 bytes, 16313328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab54d47e

Command (m for help): v
Remaining 16313327 unallocated 512-byte sectors.

Command (m for help): w

The partition table has been altered.
Syncing disks.

ubuntu@ubuntu:~$

```

---

### Post by tdeith on 2016-10-13
I may as well also post this in case it's useful:

The way the partitions were set up before these issues was approximately:

1) - 150MG of FAT for UEFI
2) ~60GB empty/unjournalled - was being turned into NTFS while the boot table was originally killed
3) ~80GB NTFS
(Below are in a logical partition)
4) 8GB EXT3
5) 8GB EXT3
6) 280GB EXT3
7) 16GB Swap

I'm nearly certain that the 8GB seen by *fdisk*, *gdisk*, etc, correspond to one of the 8GB EXT3 partitions.

---

### Post by oldfred on 2016-10-13
You do not normally use an ESP - efi system partition with MBR partitioning. UEFI expects gpt partitioning.
Windows only boots in BIOS mode from MBR and only in UEFI from gpt. Ubuntu can boot in either UEFI or BIOS from gpt, but generally should be in same boot mode as Windows.


First post showed this:
```
Disk /dev/sda: 14.9 GiB, [COLOR=#ff0000]16018046976 bytes[/COLOR], 31285248 sectors
Units: sectors of 1 * 512 = 512 bytes
```

Which seems to show the error, but none of your newer posts show that.
I think GiB and sectors match, but bytes does not.

Does BIOS/UEFI show drive at correct size?

---

### Post by tdeith on 2016-10-13
> **oldfred said:**
> You do not normally use an ESP - efi system partition with MBR partitioning. UEFI expects gpt partitioning.
Windows only boots in BIOS mode from MBR and only in UEFI from gpt. Ubuntu can boot in either UEFI or BIOS from gpt, but generally should be in same boot mode as Windows.

Yes - I was making the transition from MBR/BIOS to GPT/UEFI while I was hitting this issue. I did things in a wonky order (from not really knowing what I was doing, and being bold with the "I can just wipe the disk and start over if it messes up" assumption).

> **oldfred said:**
> 
First post showed this:
```
Disk /dev/sda: 14.9 GiB, [COLOR=#ff0000]16018046976 bytes[/COLOR], 31285248 sectors
Units: sectors of 1 * 512 = 512 bytes
```

Which seems to show the error, but none of your newer posts show that.
I think GiB and sectors match, but bytes does not.


*/dev/sda* is the Ubuntu live USB, and 16GB (14.9GiB) is the right size for that drive.

> **oldfred said:**
> 
Does BIOS/UEFI show drive at correct size?


I've tried to confirm this, but it's been tricky:

> **tdeith said:**
>  
- None of my computers have successfully booted into BIOS (neither  booting past BIOS nor  entering the BIOS settings) with this drive  attached. The BIOS's  universally freeze while detecting hardware. This  makes boot-based recovery tools (eg,  DBAN) difficult so far. It is also  not fixed by resets-via-CMOS-battery-ejecting.


I'll be trying to get a BIOS to show the disk (and size) for now, though.

---

### Post by oldfred on 2016-10-13
It is essential that UEFI/BIOS sees drive correctly. It writes data to hard drive for operating systems to use.

---

### Post by tdeith on 2016-10-13
I think it's fair to say that none of my UEFIs/BIOS's are seeing the drive correctly. I have two computers giving me errors while the BIOS/UEFI is looking for disks, and one computer which is capable of grabbing the harddisk's name. (Screenshot attached.)

Does this sound like it's a damaged drive, then? Any damage would have needed to occur somewhere in the process of:

 - Have a MBR drive holding UEFI-booting grub and various Ubuntu distros, and a legacy-BIOS-booting Windows 7 (because transition from legacy to UEFI)
 - Start installing Windows 7 OS from a GPT-tabled, UEFI-booting, USB
 - Tell Windows installer to format a new NTFS partition, and watch as entire installer freezes before any indication of partitioning progress appears
 - Power down machine after 5 minutes of waiting for Installer to progress

I can imagine unexpected power down to corrupt the partition table, but I am surprised it would damage the drive past being readable by a BIOS. (Except that it really seems that damaged...)

---

### Post by tdeith on 2016-10-13
So this issue appears to have fixed itself - which is to say I'm not sure if I had a hand in it or not. I'll be posting a longer write-up later on detailing what I was doing when the disk decided to appear under *fdisk* as its full-sized self.

Until that write-up, though, thank you so much for your help oldfred! (Even if you just walked me through debugging steps, and gave relevant background information.)

---

### Post by oldfred on 2016-10-14
Sometimes the fix is just sprinkling the magic pixie dust over the problem. (or we never really know what solved it.) :)

---

### Post by tdeith on 2016-10-14
So, I now have a fully functional drive; I even have some fresh OS's sprinkled around. Here's what happened between #17 and now:

 - Given that there was the one laptop which could boot into/past bios with the drive attached (attached via SATA), I tried to run DBAN against the disk. Setting up the DBAN boot medium, and running it against the disk, all went as it normally should. Unfortunately, DBAN only saw the 8GB of drive that I'd been seeing via *fdisk *etc, and probably didn't wipe anything which hadn't already been zeroed. Maybe it helped, though.
 - I then tried booting back into the Ubuntu live USB, primarily to see if it would still panic* during boot. It panicked, drive was removed from SATA, rebooted into live USB, drive was reinserted via USB.
 - I started trying to target specific partitions in the drive for wiping with *dd*, since for some reason I hadn't graduated from trying targeting */dev/sdX* to targeting */dev/sdX*#. Eventually I had overwritten every partition available in /dev/sdX. Somewhere in this process, *fdisk *etcstarted seeing the drive as being 4KB (I think because a single 4K record got copied into some specific partition via *dd*?)instead of 8GB. 
 - Since *something* had changed, I was curious to see if there would still be kernel panic if the drive was already attached while Ubuntu booted. So, reboot into live USB again, this time not removing the drive from the other USB port. And tada, not only was there no kernel panic, but the drive made its full 500GB available via *fdisk*.I immediately wiped the entire disk via *dd*, in case I had just gotten lucky and didn't fully nuke the corrupt stuff. I've since had no problems.

***The kernel panic manifested itself as a 
'Out of memory: Kill process [worryingly small PID] ([something important like upstart]) score 100 or sacrifice child' 
error while Ubuntu was booting. These OOM messages happened to be the first sign that something had gone wrong when I had originally killed the drive. My speculation would have to be that somewhere in the kernel's init, it was hitting the MBR-partition-loop and dying.

---

### Post by oldfred on 2016-10-14
I changed to gpt partitioning back with 10.10. My XP drive was still MBR, but then all new or totally formatted drives are gpt. Even my larger flash drives are gpt.
Only if dual booting with Windows on an older BIOS only system may you need MBR.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

