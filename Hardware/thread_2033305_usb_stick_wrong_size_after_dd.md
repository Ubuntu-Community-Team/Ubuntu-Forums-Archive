---
title: "usb stick wrong size after dd"
date: 2012-07-25
forum: Hardware
---

### Post by 1clue on 2012-07-25
Hi guys,

I had a brain freeze while trying to make a usb stick bootable.

I used dd to write an iso to my 32g usb stick and now it reports the maximum size as the size of an ubuntu cd image.  732.1m.  No disk utilities will write to it because it's not a format they know anymore.

This was a previously working 32g stick I've had around for almost a year, now it shows as nothing any computer can mount, except that the hardware size has changed and nothing seems able to fix it.

I've tried fdisk, disk utility and disk utility on the mac.

I can't be the only moron on the forum.  Does somebody know how to undo this?

Thanks.

---

### Post by Scott Goodgame on 2012-07-25
You might want to try gparted and delete the partition, create a new onw and write a partition table, then format it.

---

### Post by oldfred on 2012-07-26
What does testdisk say about the flash drive?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by 1clue on 2012-07-26
Unable to open file or device.

Thanks for the reading material, will get right on that.


testdisk /dev/sde
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Unable to open file or device /dev/sde

Usage: testdisk [/log] [/debug] [file.dd|file.e01|device]
       testdisk /list  [/log]   [file.dd|file.e01|device]
       testdisk /version

/log          : create a testdisk.log file
/debug        : add debug information
/list         : display current partitions

TestDisk checks and recovers lost partitions
It works with :
- BeFS (BeOS)                           - BSD disklabel (Free/Open/Net BSD)
- CramFS, Compressed File System        - DOS/Windows FAT12, FAT16 and FAT32
- HFS, HFS+, Hierarchical File System   - JFS, IBM's Journaled File System
- Linux Ext2 and Ext3                   - Linux Raid
- Linux Swap                            - LVM, LVM2, Logical Volume Manager
- Netware NSS                           - NTFS (Windows NT/2K/XP/2003)
- ReiserFS 3.5, 3.6 and 4               - Sun Solaris i386 disklabel
- UFS and UFS2 (Sun/BSD/...)            - XFS, SGI's Journaled File System

If you have problems with TestDisk or bug reports, please contact me.

---

### Post by 1clue on 2012-07-26
Tried as root.  I'm inside now doing scans.

---

### Post by 1clue on 2012-07-26
gparted doesn't recognize the partition table but shows the device to be 4.00 gb.  The size has somehow changed since I started this debacle.  I tried writing a partition table to it, but it won't stay.

testdisk tried writing a partition  table too, but failed.

This is an a-data n005 usb3 device, 32gb size.

I wonder if I could get someone who has a similar device to dd the partition table and post it somewhere so I could re-dd it with good data?

---

### Post by 1clue on 2012-07-26
Or maybe as an alternative maybe I could get an idea of reasonable values for cylinders/heads/sectors/sector size?  Not sure if I can write anything but it might help.

It would really bug me if this device is fried.  It's pretty quick by thumb drive standards, and has been reliable until now.

---

### Post by prshah on 2012-07-26
> **1clue said:**
> It would really bug me if this device is fried.  It's pretty quick by thumb drive standards, and has been reliable until now.

I don't think you can "fry" a USB stick in the manner stated using dd, so I don't believe that your stick is damaged in any manner.

I suspect that you are simply using /dev/sdX1 rather than sdX; sdX1 refers to the partition, and sdX refers to the device.

Even if it is one of those "knock-off / fake" chinese pen drives, I don't see how the capacity reset has occured using dd.

As a last resort, you can wipe out the existing partition structure completely by using```
sudo dd of=/dev/sdX if=/dev/zero bs=512 count=1
``` Please replace sdX with the device for your (plugged in, unmounted) USB drive.

This will zero everything within the first 512 bytes, which includes the MBR and Partition Table. You can then use palimpsest or gparted. Of course, you "lose" all data on the device; use testdisk (or photorec, included in testdisk suite) to recover if required, but difficult / involved.

AT YOUR OWN RISK, please.

---

### Post by 1clue on 2012-07-26
The device is /dev/sde, not /dev/sde1.  It's not a fake drive, been using this thing for almost a year to full 32g capacity.  It's had dozens of erase/write/format cycles, depending on whether I'm going to/from a mac, windows or linux.

I tried the dd if=/dev/zero and it still shows as 4g, still unrecognized partition table and still won't write a new one using gparted as root.

Using testdisk I tried changing disk geometry to be the same as my 64-g stick only half the cylinders, but it won't take.  I wish I could what testdisk would put in into a file, then dd it back out onto my flash drive.

---

### Post by viperdvman on 2012-07-26
did you DD a whole ISO to your 32GB flash drive? If so, it's going to overwrite that 32GB partition you had and write the ISO as its own partition, leaving the rest of the drive unformatted.

A possible reason you're having problems is that it writes the entire contents of the ISO, MBR and partition table included, on the flash drive, and thus makes it act like a CD/DVD. So the drive will only recognize that particular partition. And trying to remove that partition and reformat the entire USB drive does get to be a real PITA. I've done it before in Ubuntu's Disk Utility, but it's been a while and don't remember all the details involved. Just make sure that you **unmount the drive** before attempting to remove the partition, whether in gparted or Disk Utility.

For now, I would try creating another FAT partition after the one DD created in gparted... use up that remaining amount of space. If that doesn't work, it's because DD copied over the ISO's partition table, which is much like a CD's/DVD's table rather than an HDD/SSD's MBR or GPT tables. This partition can be deleted in Ubuntu's Disk Utility if all else fails. And you'll have all 32GB of your flash drive back once you reformat it.

Also, if creating that second partition alongside the one DD created fails, then I would recommend getting a smaller 8GB USB drive for the purpose of DDing 4GB+ ISOs to.

---

### Post by prshah on 2012-07-26
> **1clue said:**
> The device is /dev/sde, not /dev/sde1.  It's not a fake drive, 

I tried the dd if=/dev/zero and it still shows as 4g, still unrecognized partition table and still won't write a new one using gparted as root.


If you used dd correctly, it should not show you any partitions at all. I assume you used sudo. It should also trigger a kernel refresh to re-read the partitions; assuming it didn't, try this command to refresh the kernel's knowledge of the partitions:```
sudo partprobe /dev/sdX #sde
```

Then, please check the "disklabel". you can do this in GParted: for your usb "drive": Click Device-Set Disklabel and set it to msdos. Then click "Create". You can then try to partition as normal.

Before starting any of the above, please issue the below command in ANOTHER terminal```
tail -f /var/log/syslog
``` Then plug in the usb drive and perform the above operations. I assume your data is long gone and you are only interested in bringing the pendrive back to life.

If you find the problem is still not solved, please post back the log output from the above command.

---

### Post by 1clue on 2012-07-26
Yes, I copied the iso over with dd to the raw device.  I have been unable to make a partition after the 4g one because all the disk utilities think there's no drive out there.

I did all this stuff as root.  There is no partition, just a blank 4g space.  I can't create a partition at all because there is no partition table.  The various utilities fail in different ways when I try to write a partition table.  testdisk lets me 'create' one and even change the disk geometry so it looks like 32g again, but when I power the device down and remove/reinstall it, nothing was written at all.

The data on the drive was never an issue.  It's long gone or useless by now.  The drive on the other hand is usb3 64g and it cost a significant amount of money.

---

### Post by oldfred on 2012-07-26
If you just want to erase MBR, which will zero out partition table. Normally you only use dd on first 446 as that is the boot code & the rest is the partition table.
dd has the nickname Data Destroyer for a reason.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


Erase Partition- Make double sure you have correct drive & partition example is sda1
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
example is sda be sure to change:
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Then you may be able to build a new partition table.

---

### Post by 1clue on 2012-07-26
Dude,

I'm one of the guys who's been calling it data destroyer.  I don't even know what the original name means.  I have to fire up the man page every time I use it, because I'm terrified of it.

The whole point of this project was to fool the system that my usb was a true iso cd.  That didn't work, but what I forgot to do is grab the boot block(s) before I trashed it.

If I DD the first few blocks from a 64g stick over the top of this 32g one, will it hurt anything?

I don't have another 32g, nor do I have another usb3 stick.  I do however have a couple 64g usb2 ones.

---

### Post by oldfred on 2012-07-26
I have seen testdisk & some Windows tools create partition tables with the wrong size that we then had to repair. 

You may be able to write the output from sfdisk, edit end value and import into defective one? See man sfdisk.


Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Restore from PT.txt, adjust examples with sda or sdc to your drives
sudo sfdisk --no-reread -f /dev/sdc -O PT.save < PT.txt
sudo sfdisk --no-reread -f /dev/sdc -O PTsda.save < PTsda.txt
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.


Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by R33D3M33R on 2012-07-27
> **oldfred said:**
> If you just want to erase MBR, which will zero out partition table. Normally you only use dd on first 446 as that is the boot code & the rest is the partition table.
dd has the nickname Data Destroyer for a reason.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


Erase Partition- Make double sure you have correct drive & partition example is sda1
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
example is sda be sure to change:
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Then you may be able to build a new partition table.

I did the exact same thing as OP with a 4 GB USB drive. I dd-ed an Linux DVD iso to it. I was really surprised when it didn't allow me to delete the files in Linux. So I booted to windows and I was even more surprised that there seem to be no way to delete the partition table. The only thing I was able to do is to allocate ~230 MB through Windows 7.

So I gave this instructions above a try. I used 
```

sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
dd if=/dev/zero of=/dev/sdb bs=512 count=1
sudo fdisk -l /dev/sdb //some progress was shown here
sudo fdisk /dev/sdb //this is how i entered the partition editing
```In fdisk I pressed n for new partition table, p for primary and w to write it. Then I executed:

```
sudo mkfs.vfat -F 32 /dev/sdb1
```And I recovered the full disk size. I didn't try to write such amount of data on it, but it seem to have worked.

---

