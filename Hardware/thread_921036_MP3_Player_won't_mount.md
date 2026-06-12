---
title: "MP3 Player won't mount"
date: 2008-09-15
forum: Hardware
---

### Post by zeroroom on 2008-09-15
I plugged up my [_Samsung YP-Z5AS 4GB_]("http://www.amazon.com/Samsung-YP-Z5AS-Digital-Player-Silver/dp/B000EPHHUM") MP3 player up to my system and it doesn't seem to be mounting.

I checked to see if it showed up in /media and it isn't there. Normally when I plug in a USB device it automagicaly mounts and shows up on the desktop. Is there something I am missing?

I am *very* new to Ubuntu so please assume I have overlooked the obvious.

Thanks in advance for any assistance provided.

---

### Post by arch0njw on 2008-09-16
Does this post help you out at all?
[http://ubuntuforums.org/showthread.php?t=351878](http://ubuntuforums.org/showthread.php?t=351878)

If one person had success, there has to be a way to get it to work :)

---

### Post by zeroroom on 2008-09-16
> **arch0njw said:**
> Does this post help you out at all?
[http://ubuntuforums.org/showthread.php?t=351878](http://ubuntuforums.org/showthread.php?t=351878)

If one person had success, there has to be a way to get it to work :)

I appreciate the reply but, my player isn't even mounting. I am so new to Ubuntu that I am not sure what troubleshooting steps to take. Thanks again.

I am going to try to install WMP 10, which I think we can all agree, is garbage. I am hoping that it may see the player anyway. If anyone else has any ideas, I'm all ears.

Thanks.

---

### Post by arch0njw on 2008-09-17
Try connecting the drive and running this command:  *sudo fdisk -l*.  Please post the results.

BTW, that is "dash ell" not "dash one".

---

### Post by zeroroom on 2008-09-17
> **arch0njw said:**
> Try connecting the drive and running this command:  *sudo fdisk -l*.  Please post the results.

BTW, that is "dash ell" not "dash one".

When I get home tonight I will try that. I have been talking to someone else about this issue and I wanted to update you on what we have found. Maybe it will shed some light on the issue.

I ran lsusb from a terminal and recived this:
> 
dwhite@zeroroom:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 004: ID 04e8:503c Samsung Electronics Co., Ltd
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 001: ID 0000:0000 


Then per some other instructions I received I unpluged the device then ran dmesg > /tmp/1 then pluged the device back in and ran dmesg > /tmp/2 then diff /tmp/1 /tmp/2. This was the output:
> 
dwhite@zeroroom:~$ dmesg > /tmp/1
dwhite@zeroroom:~$ dmesg > /tmp/2
dwhite@zeroroom:~$ diff /tmp/1 /tmp/2
788a789,806
> [ 6221.500416] usb 6-2: new high speed USB device using ehci_hcd and address 5
> [ 6221.781148] usb 6-2: configuration #1 chosen from 1 choice
> [ 6221.812794] scsi8 : SCSI emulation for USB Mass Storage devices
> [ 6221.813435] usb-storage: device found at 5
> [ 6221.813437] usb-storage: waiting for device to settle before scanning
> [ 6226.833707] usb-storage: device scan complete
> [ 6227.079758] scsi 8:0:0:0: Direct-Access Samsung YP-Z5 (MSC) PQ: 0 ANSI: 2
> [ 6227.083475] sd 8:0:0:0: [sdc] 8094720 512-byte hardware sectors (4144 MB)
> [ 6227.084977] sd 8:0:0:0: [sdc] Write Protect is off
> [ 6227.084982] sd 8:0:0:0: [sdc] Mode Sense: 07 00 00 00
> [ 6227.084985] sd 8:0:0:0: [sdc] Assuming drive cache: write through
> [ 6227.090215] sd 8:0:0:0: [sdc] 8094720 512-byte hardware sectors (4144 MB)
> [ 6227.091964] sd 8:0:0:0: [sdc] Write Protect is off
> [ 6227.091969] sd 8:0:0:0: [sdc] Mode Sense: 07 00 00 00
> [ 6227.091971] sd 8:0:0:0: [sdc] Assuming drive cache: write through
> [ 6227.091974] sdc: sdc1
> [ 6227.097679] sd 8:0:0:0: [sdc] Attached SCSI removable disk
> [ 6227.097723] sd 8:0:0:0: Attached scsi generic sg4 type 0


And even though Linux sees the player when I open up computer this is what I see:
[IMG]http://lh4.ggpht.com/donavanwhite/SNB_GLDHaWI/AAAAAAAAAGI/OtCKjippQTk/s800/Computer.jpg[/IMG]
(*Please let me know if you can't view the image.*)

I then ran groups and this was the output:
> 
dwhite@zeroroom:~$ groups
dwhite adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin


Like I said, I will try what you have suggested and see if that will help. Unless someone thinks, in light of this new information, that would make things worse.

Thanks again for the help arch0njw!

---

### Post by arch0njw on 2008-09-17
I think me and the other fellow are onto the same path.  "fdisk" is a partition table manipulator; the "-l" switch is the "list" switch.  I am attempting to see if the OS is aware of that device's existence as a drive, but just isn't mounting it.

The "lsusb" command is effectively a "list USB" command -- it shows what USB devices are attached.  It is a good thing that it is showing up under that.  The OS is aware that it is connected as a device.  The next question (answered by "fdisk -l") is if it is aware that it is a drive.

Does "filesystem" appear after your connect your MP3 player?  That might be what we're looking for.

---

### Post by zeroroom on 2008-09-17
> **arch0njw said:**
> Does "filesystem" appear after your connect your MP3 player?  That might be what we're looking for.

Filesystem appears all the time. For lack of a better term, it the is main drive, the drive Ubuntu is installed on.

---

### Post by Casper Hansen on 2008-09-17
Try installing Gnomad2.

---

### Post by zeroroom on 2008-09-17
> **Casper Hansen said:**
> Try installing Gnomad2.

I installed it, but I still have the issue where the player won't mount.

---

### Post by zeroroom on 2008-09-17
> **arch0njw said:**
> Try connecting the drive and running this command:  *sudo fdisk -l*.  Please post the results.

BTW, that is "dash ell" not "dash one".


Here is the result of running sudo fdisk -l:

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea58cbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    b  W95 FAT32

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea58cbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23569   189317961   83  Linux
/dev/sdb2           23570       24321     6040440    5  Extended
/dev/sdb5           23570       24321     6040408+  82  Linux swap / Solaris
dwhite@zeroroom:~$ 


I don't see the MP3 player in here, do you? Is it wierd that it shows up under lsusb but not fdisk?

---

### Post by arch0njw on 2008-09-17
Okay.  Now that is a bit strange.  The OS sees it as a device, but it is not seeing it as a drive.  I think that gives us a starting place.  I will need to dig into this more.

---

### Post by zeroroom on 2008-09-17
I went to submit a bug and found this: [_Samsung YP-Z5 flash based MP3 player fails to mount_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42959")

Maybe it will help.

Thanks for your help arch0njw!

---

### Post by arch0njw on 2008-09-18
Sometimes blowing on the embers of an old bug is necessary.  Here's hoping it works again!

---

