---
title: "cannot mount external USB harddisk"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by seboslaw on 2007-03-04
Hi,

I have a problem with my external USB-harddisk (IBM/Hitachi) under Ubuntu 6.10. With my old Debian installation the disk worked fine, also no problems under Win XP. Further, I have a second external USB HD, which works as it should (mountable and everything), running on the same USB-2.0 Controller as the HD that isn't working.
When I plug in the IBM HD, dmesg gives the following output:

[FONT="Lucida Console"][SIZE="1"][17256132.396000] Vendor: IBM-DTLA Model: -307075 Rev: TXAO
[17256132.396000] Type: Direct-Access ANSI SCSI revision: 00
[17256132.420000] SCSI device sdb: 150136561 512-byte hdwr sectors (76870 MB)
[17256132.420000] sdb: Write Protect is off
[17256132.420000] sdb: Mode Sense: 03 00 00 00
[17256132.420000] sdb: assuming drive cache: write through
[17256132.424000] SCSI device sdb: 150136561 512-byte hdwr sectors (76870 MB)
[17256132.424000] sdb: Write Protect is off
[17256132.424000] sdb: Mode Sense: 03 00 00 00
[17256132.424000] sdb: assuming drive cache: write through
[17256132.424000] sdb: sdb1
[17256132.456000] sd 6:0:0:0: Attached scsi disk sdb
[17256132.456000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[17256186.276000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive![/SIZE][/FONT]

So the disk seems to be attached to /dev/sdb....
fdisk -l gives the following, though:

[FONT="Lucida Console"][SIZE="1"]Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 3557 28571571 83 Linux
/dev/hda2 3558 3649 738990 5 Extended
/dev/hda5 3558 3649 738958+ 82 Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4864 39070048+ c W95 FAT32 (LBA)[/SIZE][/FONT]


/dev/sda1 is my other external HD. /dev/sdb1 isn't listed at all...... When I try now to mount the HD manually, I get the following output:

[FONT="Lucida Console"][SIZE="1"]# mount /dev/sdb1 /media/GROSS/
mount: special device /dev/sdb1 does not exist
[/SIZE][/FONT]
cat /proc/partitions gives:

[FONT="Lucida Console"][SIZE="1"]~# cat /proc/partitions
major minor #blocks name

3 0 29316672 hda
3 1 28571571 hda1
3 2 1 hda2
3 5 738958 hda5
8 0 39070080 sda
8 1 39070048 sda1
8 16 75068280 sdb
8 17 75063681 sdb1[/SIZE][/FONT]

So the disk is listed there, but not in fdisk.....
Anybody got any advice for me??? I've already tried replugging the HD and also reformated the drive under Windows......without success, though....


Regards,

Sebastian

---

### Post by seboslaw on 2007-03-04
anyone???

---

### Post by Tom Tiger on 2007-03-05
Is there a partition on the disk?

If not,  install qtparted (it's in the synaptic), and see if qtparted sees the drive.

if it does and it's empty, make new partition table, make a partition after its done you get an error, don't worry, that's just the automount. Close qparted, disconnect the usbdrive, connect it again (wait a minute to be sure) then hit disk under system (or just use qtparted again) format it and you're done, it will mount automaticly (also load diskapplet in you taskbar, really handy)

hope this helps, Tom

---

### Post by seboslaw on 2007-03-05
Hi Tom, 

thanks for your answer.

The drive is indeed partitioned (FAT 32) and I have no problem running it under Windows. I installed qtparted, which gave an error message "Failed to get list of devices" in the console while starting. It then didn't recognize the harddisk, but did recognize my two other drives (one regular, one USB).

Then I tried gparted, which said something like:

"call to stat for device /dev/sdb/ failed - No such file or directory"

when starting. It then opened and, just as qtparted, didn't recognize the harddisk /dev/sdb/ .
Do you have any other ideas on how to solve this???

Cheers,

Sebastian

---

### Post by seboslaw on 2007-03-05
Hi again,

after digging a little deeper, I found out that my usb hd was mounted as a scsi drive. It seems that the current edgy kernel has problems with a certain kind of usb casing (mine :-(

Under usbview it popped up as "prolific technology pl3507".
So I just ditched it and assembled the hd into my server. Problem solved :-)

---

