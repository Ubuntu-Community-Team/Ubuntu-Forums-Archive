---
title: "Ubuntu 8.10 recognizes ext HD but won't mount"
date: 2009-04-01
forum: Hardware
---

### Post by Alitis on 2009-04-01
I have spent several hours, both today and yesterday, meticulously going through dozens if not hundreds of forum posts, forum searches, and google searches, and I just can't seem to find anyone else who has had the same problem.

I have a Western Digital 1TB External Hard Drive.  After driving back to college from visiting my parents over spring break my ext HD stopped reading in Vista.  I installed Ubuntu, first and foremost because linux is the ****, but also hoping to read, repair, or at least recover some of my data.

Here's the info:
- Ubuntu recognizes the drive as "USB Drive"
- When I try to open "USB Drive" I get "Unable to Mount Location: Can't Mount File"
- The HD is ntfs, and yes I have ntfs-3g and ntfs config installed.

Troubleshooting Thus Far:
"lsusb"
> Bus 006 Device 006: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 006 Device 005: ID 05e3:0607 Genesys Logic, Inc. 
Bus 006 Device 004: ID 05e3:0607 Genesys Logic, Inc. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


"mount"
> /dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/scott/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=scott)
/dev/sda1 on /media/tmpmnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


"sudo fdisk -l"
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b27dcca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       95493   767044600    7  HPFS/NTFS
/dev/sda2           95494      121601   209712510    5  Extended
/dev/sda5           95494      107942    99996561   83  Linux
/dev/sda6          120392      121601     9719293+  82  Linux swap / Solaris

*note that the Wester Digital HD does not show up here

"tail -F /var/log/messages"
> Apr  1 19:33:15 scott-desktop kernel: [  704.307738] sd 7:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Apr  1 19:33:15 scott-desktop kernel: [  704.308839] sd 7:0:0:0: [sdb] Write Protect is off
Apr  1 19:33:15 scott-desktop kernel: [  704.308851]  sdb:<3>end_request: I/O error, dev sdb, sector 0
Apr  1 19:33:15 scott-desktop kernel: [  704.309960] __ratelimit: 3 callbacks suppressed
Apr  1 19:33:15 scott-desktop kernel: [  704.317967] Dev sdb: unable to read RDB block 0
Apr  1 19:33:15 scott-desktop kernel: [  704.327469]  unable to read partition table
Apr  1 19:33:15 scott-desktop kernel: [  704.328639] sd 7:0:0:0: [sdb] Attached SCSI disk
Apr  1 19:33:15 scott-desktop kernel: [  704.331418] sd 7:0:0:0: Attached scsi generic sg2 type 0
Apr  1 19:49:45 scott-desktop kernel: [ 1694.873227] __ratelimit: 15 callbacks suppressed
Apr  1 20:01:47 scott-desktop -- MARK --


Addition Notes:
- I installed gparted, and it does not recognize the drive.
- I have successfully mounted other NTFS ext drives.
- Yes, it's possible the HD received damage in transit, but the HD does not make any of those awful "dieing" noises.
- In the NTFS-config options where it lists devices to mount, the HD does NOT show up.
- On vista, the HD spins and vista goes on about "installing usb mass storage device drivers...". Once it finishes nothing happens, and neither "My Computer" nor Disk Management recognize the HD, although a disk called "WD" shows up in device manager.

Seems to be that the computer knows that it's there, and knows it's a hard drive, but just can't seem to communicate with it.  Is there a way I can repair partition tables? or anything I can do?

---

### Post by Dark_Stang on 2009-04-02
Sounds like your hard drive is failing. I'd suggest hooking it up to a Windows machine and running a chkdsk on it to see if you can at least pull of your data before it totally loses it. If this doesn't work, and you really need your data, stop using the drive because you need data recovery. The more you try the worse (and more expensive) it will get.

---

### Post by Alitis on 2009-04-02
Okay.  When I plug it into Windows, it goes on about installing drivers but never actually shows up in my computer, or disk management.  How do I run chkdsk on it if it doesn't have a drive letter or a path?

---

### Post by coffeecat on 2009-04-02
There's another possibilty. Perhaps it's not the HD itself that's failing, but either the enclosure or the power supply.

Maybe the enclosure firmware has got itself borked, or perhaps during the drive back a cable inside has been loosened. Can you open up the enclosure? If so, check all cable mountings and see if that helps. If not, the HD inside will be a standard SATA. Take it out and try it in another enclosure (if you have one) or hot plug it into a SATA connector (if you have one). If you can do this you can reassure yourself the HD is still OK, or not as the case may be.

Or - power supply. This is where manufacturers skimp on quality. I'd lay even money that it's this that's failing. Perhaps enough power getting through for Vista to recognise something, but not enough for it to be mounted. If you're lucky, the DC voltage and connector will be the same as for other devices around the house. Can you try another power supply?

I'd have a go at the power supply before taking a screwdriver to the enclosure.

---

### Post by Alitis on 2009-04-03
Okay, so I took the enclosure apart and carefully took out the hd.  I checked all the parts to make sure they were all connect fine (hd, usb thing, power supply, etc) and tried it again - same result.  I then put the HD in my computer and hooked it up like a normal HD, bios booted and gave me some error and I couldn't get the OS to see anything.  Clearly, the HD has failed.  Fortunately, the HD was used mainly for media and backups, so I don't think I lost anything original and irreplaceable, but it still sucks.  Now I'm on to trying to solve other hardware issues. (last time I EVER build a computer from the cheapest stuff on pricewatch.com, **** that)

Thanks for all your help!!!

---

