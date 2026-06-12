---
title: "case sensitive hfs+ usb drive"
date: 2005-11-10
forum: General Help
---

### Post by ttrygve on 2005-11-10
I have a USB2/Firewire drive that I created from OS X Tiger.  It's a complete image of my OS X install, created with a OS X program called Carbon Copy Cloner.  I did this because I had to give up my mac recently, so I have a complete backup of it here which I can boot other macs from or use Carbon Copy Cloner to clone back to my next mac if I get one anytime soon, but I can't seem to get to my files on it from my ubuntu desktop.  When I plug it in, it automatically detects and mounts /dev/sda2, which is a whopping 8mb partition called "Boot OS X" containing a couple files to boot OS X from (bootromfirmware, BootX, com.apple.Boot.plist, vers.txt, & "Volume Name Icon").

Any idea how/if I can make it detect and at least get read access to the main partition with all of my data on it?  It was formatted as journaled case sensitive hfs+.

These lines appear in /var/log/messages when I plug it in:

Nov 10 17:29:40 localhost kernel: [4450415.925000] usb 3-6: USB disconnect, address 7
Nov 10 17:30:02 localhost kernel: [4450438.341000] usb 3-6: new high speed USB device using ehci_hcd and address 8
Nov 10 17:30:02 localhost kernel: [4450438.550000] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 10 17:30:02 localhost usb.agent[17067]:      usb-storage: already loaded
Nov 10 17:30:07 localhost kernel: [4450443.551000]   Vendor: SAMSUNG   Model: MP0804H           Rev: UE10
Nov 10 17:30:07 localhost kernel: [4450443.551000]   Type:   Direct-Access                 ANSI SCSI revision: 00
Nov 10 17:30:07 localhost kernel: [4450443.555000] SCSI device sda: 156368015 512-byte hdwr sectors (80060 MB)
Nov 10 17:30:07 localhost kernel: [4450443.558000] SCSI device sda: 156368015 512-byte hdwr sectors (80060 MB)
Nov 10 17:30:08 localhost kernel: [4450443.558000]  /dev/scsi/host5/bus0/target0/lun0: [mac] p1 p2 p3 p4
Nov 10 17:30:08 localhost kernel: [4450443.986000] Attached scsi disk sda at scsi5, channel 0, id 0, lun 0
Nov 10 17:30:08 localhost scsi.agent[17123]:      sd_mod: loaded sucessfully (for disk)
Nov 10 17:30:08 localhost kernel: [4450444.549000] HFS+-fs: unable to find HFS+ superblock

---

### Post by Lambert on 2005-11-10
You may want to try  and unmount the device and then remount it using this command from terminal.

to unmount type

```
umount /<path>/<name>
``` 
to mount

```
mount -t hfsplus /dev/sda2 /mnt/<name>
``` 

You may need to use sudo in front of each command to run as superuser.
You can search using [COLOR=Sienna]"mount -t hfsplus"[/COLOR] as a keyword for more information and make sure I'm not missing something.

---

### Post by ttrygve on 2005-11-10
```
mount -t hfsplus /dev/sda2 /mnt/<name>
``` 

Actually, it was already detecting and mounting as hfsplus (from "mount"):

/dev/sda2 on /media/Boot OSX type hfsplus (rw)
# mount | grep media
/dev/sda2 on /media/Boot OSX type hfsplus (rw)

# df -h /media/Boot\ OSX/
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             8.5M  1.4M  7.2M  16% /media/Boot OSX

But I did try that and it still showed up as the same 8.5M partition.  I also tried sda1, 3 & 4, but only got "wrong fs type" errors:

mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm kind of wondering if my problem is that it's not a normal hfsplus partition, but a journaled & case sensitive one.

Thanks, though.

---

### Post by RAOF on 2005-11-10
What does 
```
sudo fdisk -l /dev/sda
```
say?  That should list all your partitions on there, and what file system type it thinks they are.

---

### Post by ttrygve on 2005-11-10
```

Disk /dev/sda: 80.0 GB, 80060423680 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

```

Which is odd, of course, since it autodetects and mounts sda2.

---

### Post by Lambert on 2005-11-10
There's an app in the repositories you may want to look at.
name is [COLOR=Sienna]hfsplus[/COLOR]

> tools to access HFS+ formatted volumes
HFS+ is a modernized version of Apple Computer's HFS Filesystem.
Nowadays, it is widely used with more recent versions of MacOS.
hfsplus consists of a library and set of tools that allow access to
HFS+ volumes.

This package contains the tools themselves.

Did you check or test the drive with the mac before you gave it up to make sure the clone was ok?

---

### Post by ttrygve on 2005-11-10
[QUOTE=Lambert]There's an app in the repositories you may want to look at.
name is [COLOR=Sienna]hfsplus[/COLOR][/QUOTE]

Yeah, I tried installing both hfsplus and hfsutils, but they didn't appear to make any difference.  I've since learned while googling that "case sensitive hfs+" is technically called hfsx, but there does not appear to be a fstype option for mount called hfsx.

> Did you check or test the drive with the mac before you gave it up to make sure the clone was ok?

Oh of course, I wasn't about to give up my powerbook without testing that first.  =)  I've even booted someone else's iBook off this drive just recently, and it ran just fine.

---

### Post by ttrygve on 2005-11-11
More info:

```
# parted /dev/sda
GNU Parted 1.6.21 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/sda
(parted) print
Error: The partition's data region doesn't occupy the entire partition.
Ignore/Cancel? i
Disk geometry for /dev/sda: 0.000-76351.569 megabytes
Disk label type: mac
Minor    Start       End     Filesystem  Name                  Flags
1          0.000      0.031              Apple
2          0.031    128.031  hfs+        eXternal booter
3        128.031  76351.562              Apple_HFSX_Untitled_1

```

---

