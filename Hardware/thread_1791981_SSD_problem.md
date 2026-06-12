---
title: "SSD problem"
date: 2011-06-27
forum: Hardware
---

### Post by martinyt on 2011-06-27
I have a 60GB Corsair SSD (CSSD-F60GB2-BRKT-A) which I now have mounted to my computer. I get an error at bios saying something like "There were somthing wrong with on of your discs. Hit f1 to proceed". When it boots I get:
sudo fdisk -l

Disk /dev/sdd: 0 MB, 32768 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Telling me that it only have a 32kB disk. Obviously I have some problems. I have looked around, but not found anything that might resolve my problem. If you have any suggestion, please let me know. Thanks

---

### Post by dabl on 2011-06-27
> **martinyt said:**
> 

Disk /dev/sdd doesn't contain a valid partition table



That is the problem.  You can use GParted, "Device > New Partition Table" and choose "MS-DOS" for the partition table type, then make your partition(s) and filesystems, and you should be able to proceed with installation.

There is a lot more that you can learn about using an SSD.  This thread has information and links to some of it:

[http://kubuntuforums.net/forums/index.php?topic=3117423.0](http://kubuntuforums.net/forums/index.php?topic=3117423.0)

---

### Post by martinyt on 2011-06-27
Thanks. I tried the gparted suggestion and I got and error message saying something like: "something went wrong". The good news is that I do not get an bios-error, but the bad news is that the disk dosen show up at all any more :-(

---

### Post by oldfred on 2011-06-27
Someone recently had the some issue with a new 4k drive.

Sector size (logical/physical): 512 bytes / 4096 bytes

But I do not think I saw the solution.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

Are you also installing windows or just Linux? If just Linux then gpt is recommended for SSD.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by martinyt on 2011-06-28
So, after a shutdown, the disc appears again. Tried the GPT:

gdisk /dev/sdd
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): n
No free sectors available

Command (? for help): 



I will only run linux/ubuntu on the disc.

---

### Post by dabl on 2011-06-28
There is such a thing as failure of the SSD ...   :(

However, before giving up on it, I would use "dd" to wipe out the MBR area, and then try again with GParted to make a new MBR.

Be very careful -- you do NOT want to make a mistake with your dd command, as it will destroy all data on the target device with no warning or confirmation:

dd if=/dev/zero of=/dev/sd*x* bs=512 count=1

where "x**" is the correct designation of your SDD.  First use fdisk -l to make sure you have the right device, then use the dd command to nuke everything in the first 512 bytes.  Then start GParted, browse to the device, and try making a new partition table.

Good luck!

---

### Post by martinyt on 2011-06-28
Now, playing around with gdisk - I got this:

gdisk /dev/sdd
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): 

But I still can't create a new partion.

---

### Post by oldfred on 2011-06-28
I would download the newest copy of gdisk. The copy in Ubuntu is old. And detailed instructions on on rodbooks site.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Be sure to create a bios_grub partition.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.

---

### Post by martinyt on 2011-06-28
dabl -gparted just crashed -

Oldfred - I will try it.

---

### Post by martinyt on 2011-06-28
Still reading about GPT and MBR. Just thought I should mention that I tried to install ubuntu on this ssd when it was connected to a laptop (trough the DVD-pata port). I had some boot problems and that is way it's now in my stationary computer.

---

### Post by srs5694 on 2011-06-28
> **dabl said:**
> There is such a thing as failure of the SSD ...   :(

This is probably the case, as revealed by....

[quote=martinyt]```
Disk /dev/sdd: 0 MB, 32768 bytes
```[/quote]

This says that fdisk is finding the disk to be a mere 32,768 bytes (note: *bytes*, not some larger multiple of that, like gibibytes) in size. For comparison, a 128-entry GPT consumes a total of 34,304 bytes (including both primary and backup data structures), so this disk, as seen by fdisk, isn't even large enough to partition with a standard-sized GPT.

FWIW, gdisk produces similar output (it reports the disk's size in both sectors and MiB, GiB, TiB, or other multiple-of-bytes value), but dabl's gdisk examples have all been edited to omit this information, so it's impossible to see how gdisk is seeing the disk. gdisk, and probably fdisk, determines the disk size without referring to the MBR data, so erasing the MBR data will do nothing to change this if it's being misdetected. It's conceivable, though, that the drive is OK and it's a driver issue, kernel bug, or a bug in partitioning software. Testing in another (non-Linux) OS, such as Windows or FreeBSD, would reveal if this was the case.

---

### Post by martinyt on 2011-06-28
ok. So, I got gdisk 0.7.2, but I still can't create any partions. Here is a print of the MBR partition

Expert command (? for help): o

Disk size is 64 sectors (32.0 KiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1           63   primary     0xEE

---

### Post by dabl on 2011-06-28
> **martinyt said:**
> dabl -gparted just crashed -



Ummmmmm -- that's not a good thing.

FWIW, I personally made a Parted Magic Live USB stick long time ago -- in addition to Parted it has some other excellent diagnostics and utilities for working with drives and partitions.  So if you boot it, then browse to your device, you should be able to launch GParted and make the new partition table.

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

---

### Post by martinyt on 2011-06-28
dabl - I managed to start gparted again, but the same thing happened - I tries to set a new partion table, but returnes an error and "lose" the disc - It wont show up in fdisk either. I complet shutdown does make it appear again.

I'll try your suggestion - since don't have any other platforms to try the disc on - but maybe srs5694 - if I get desperate enough I will try it on a different platform.

---

### Post by martinyt on 2011-06-28
dabl - It did not work. Same problem.

---

### Post by srs5694 on 2011-06-28
Martinyt,

Please re-read my previous post. *Your disk is not being detected correctly by any Linux disk partitioning tool*. This means it will be *impossible* to partition it correctly unless and until you track down the source of the problem. Chances are dabl was correct in suggesting you've got defective hardware. The simplest way to test that hypothesis is to test the disk under another OS and/or on another computer. Doing anything else at this point is a waste of time.

(As a side note, there are precisely three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. You've tested with members of all three families, so trying more partitioning programs will almost certainly be fruitless.)

---

### Post by martinyt on 2011-06-29
srs5694 - ok. my next step is try it on a nother platform. I guess conecting it through usb would work? This step might take I while, but I'll post as soon as I am getting something. Thanks!

---

### Post by martinyt on 2011-09-15
[COLOR=black][FONT=Verdana]Ok. So I have tried it in windows. The disc is recognised and it says that there no problem with the disk. -However - I can't access it and it is not given a name (E: or something)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When I start the "computer management" in windows a popup tells me it would like to initialize and convert the disk.  It says it is unknown and not initialize. After completing the initializing it says it is online. However, I am still not able to access the disc and the same message pops up when I reconnect the disc.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Is it broken? More tests?[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by srs5694 on 2011-09-15
It sounds like it's broken to me. Contact the manufacturer to see if you can get an in-warranty replacement.

---

