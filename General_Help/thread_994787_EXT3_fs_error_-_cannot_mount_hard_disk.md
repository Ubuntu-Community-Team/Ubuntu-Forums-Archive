---
title: "EXT3 fs error - cannot mount hard disk"
date: 2008-11-27
forum: General Help
---

### Post by Jezzaroo on 2008-11-27
I have a problem. Had Kubuntu 8.10 installed on a 200Gb SATA drive, and a 40Gb non-SATA drive with data on it as slave. Been working fine for weeks. Last night it all froze, and wouldn't reboot at all. I got error message:

> EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 256 not in group (block 4294967295)!

EXT3-fs: group descriptors corrupted! (Copied from syslog.)

I set the 40Gb as master, 200Gb as slave, reinstalled Ubuntu 8.04 on the 40Gb drive, as all the data I really need is on the 200Gb one. Tried to mount the 200Gb and got: 

> Cannot mount. Wrong fs type, bad option, bad superblock on /dev/sdb1. 

From a search on here I saw the magick code sudo fdisk -l, which gives me this:

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc79c9a18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee800574

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23946   192346213+  83  Linux
/dev/sdb2           23947       24321     3012187+   5  Extended
/dev/sdb5           23947       24321     3012156   82  Linux swap / Solaris



Any suggestions as to how I can remount that drive? Is there a repair option anywhere that could remove the bad sector or restore the block bitmap for group 256?

---

### Post by geirha on 2008-11-27
Try doing a filesystem check on it
```
sudo fsck /dev/sdb1
```

---

### Post by Jezzaroo on 2008-11-27
Doing that gives me this - although I've no idea how the smilies got in there:

> 

aero@aero-desktop:~$ sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;



When I try that, I get this:

> aero@aero-desktop:~$ e2fsck -b 8193 <device&gt;
bash: device: No such file or directory
[1] 8810
[1]+  Exit 1                  e2fsck -b 8193 < device
bash: gt: command not found
[1]+  Exit 1                  e2fsck -b 8193 < device
aero@aero-desktop:~$ 


Can you tell I'm a bit new to Linux? ;)

---

### Post by geirha on 2008-11-27
<device> should be replaced with the device node for the partition, /dev/sdb1 in this case. Not sure if that will work at all, but I guess it's worth a try.

Do you remember running any commands with sudo just before the computer froze? I believe the likely possibilities of this happening is either running some (possibly malicious) command that writes something directly to the partition (overwriting part of the filesystem) or that the part of the harddrive where the superblock is saved to happened to fail.

Install [apt://testdisk](apt://testdisk), a command-line utility that can be used to analyze and possibly recover partitions/filesystems. Run it with ```
sudo testdisk
``` and have it analyze your 200GB harddrive. Does it find your filesystem?

---

### Post by Jezzaroo on 2008-11-27
Damn - the SATA drive's disappeared. Hell's going on? 

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc79c9a18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
aero@aero-desktop:~$ 


I wasn't running any sudo commands when it failed - just browsing in Firefox. HDD light came on and everything froze. On reboot it told me that block 256 was missing or corrupted.  

I've checked all leads and jumpers and they all look OK. Tried testdisk but it only shows the 40Gb drive now. 

<scratches head>

---

### Post by geirha on 2008-11-27
Sounds like a classic case of harddrive failure, though open up the cabinet and make sure the cables are properly connected. Has the harddrive made any odd noices lately?

---

### Post by Jezzaroo on 2008-11-27
Just wanted to say that I've got the drive working again. I've got the data all backed up on DVD anyway, so I reinstalled Ubuntu onto the 200Gb, which worked fine, then set the 40Gb to be master. It's a bit messy but I can at least mount the 200Gb now. 

I've no idea what happened. Either way the drive seems physically OK and a fresh install has sorted it. Thanks for all your help.

---

