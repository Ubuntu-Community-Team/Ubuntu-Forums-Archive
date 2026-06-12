---
title: "usb hard drive not recognized while usb stick is"
date: 2009-12-18
forum: Hardware
---

### Post by yawnmoth on 2009-12-18
I plug a USB hard drive into my machine while Windows Vista is running and am able to access it just fine.  I insert an Ubuntu LiveCD, reboot, and find myself unable to access it at all.

Here's what dmesg says when I start Ubuntu up with the drive already plugged in:

```
[   75.064017] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   78.032014] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   81.000013] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   83.968013] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
```

If I unplug the drive and plug it back in I get this:

```
[  683.808016] usb 1-6: new high speed USB device using ehci_hcd and address 8
[  683.864041] hub 1-0:1.0: unable to enumerate USB device on port 6
...
[  759.268020] usb 1-5: new high speed USB device using ehci_hcd and address 9
[  759.324059] hub 1-0:1.0: unable to enumerate USB device on port 5
```
(i tried to plug it into two ports to no avail)

Of course, the fact that this all works in Windows makes what Ubuntu is saying highly suspect.

Here's what happens if I plug in a USB stick:

```
[  907.620016] usb 1-5: new high speed USB device using ehci_hcd and address 10
[  907.780306] usb 1-5: configuration #1 chosen from 1 choice
[  909.957084] Initializing USB Mass Storage driver...
[  909.957536] scsi6 : SCSI emulation for USB Mass Storage devices
[  909.957659] usbcore: registered new interface driver usb-storage
[  909.957663] USB Mass Storage support registered.
[  909.989770] usb-storage: device found at 10
[  909.989774] usb-storage: waiting for device to settle before scanning
[  914.988198] usb-storage: device scan complete
[  914.988920] scsi 6:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
[  915.034314] sd 6:0:0:0: [sdc] 2056192 512-byte hardware sectors: (1.05 GB/1004 MiB)
[  915.034931] sd 6:0:0:0: [sdc] Write Protect is off
[  915.034936] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  915.034939] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  915.037919] sd 6:0:0:0: [sdc] 2056192 512-byte hardware sectors: (1.05 GB/1004 MiB)
[  915.038405] sd 6:0:0:0: [sdc] Write Protect is off
[  915.038410] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  915.038413] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  915.038422]  sdc:
[  915.189064] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  915.189175] sd 6:0:0:0: Attached scsi generic sg3 type 0
```
So that works.  It's just USB hard drives that don't.  And it's not a problem with the hard drive, either, since it works just fine in Windows Vista.

Any ideas?

---

### Post by unmole on 2009-12-18
Is your USB HD formatted as NTFS ? Because I believe that is the issue and it can be fixed.

---

### Post by yawnmoth on 2009-12-18
It is but I'm not sure what I can do about that from Ubuntu.  GParted doesn't recognize it at all (even though Windows does).

---

### Post by unmole on 2009-12-18
Try this:
1. Install ntfs-3g
2. Add yourself to the "fuse" group.  Open Administration >Users& Groups, and add yourself to fuse.
3. Make a new mount point for your NTFS-formatted USB drive, like /media/NTFS_USB
4. Finally do a 
```
sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB
```

---

### Post by yawnmoth on 2009-12-19
According to [this post](http://ubuntuforums.org/showpost.php?p=7263604&postcount=2022), installing ntfs-3g is not necessary in (as of that post) the latest version of Ubuntu.  Since Ubuntu 9.10 was released at the end of October and that post was made in May, even Ubuntu 9.04, it seems, should work, yet it doesn't.

To top it off, the fact that [these instructions](http://ubuntuforums.org/showthread.php?t=217009) are out of date (the three code names they mention are Dapper [6.06], Edgy [6.10], and Feisty [7.04]) re-enforce the notion that installing ntfs-3g is unnecessary.

If I do, in fact, need to install it, (1) where might I find newer instructions and (2) why would people be saying it's installed when it isn't?

(I'm running 9.04)

---

### Post by yawnmoth on 2009-12-20
I just upgraded to Ubuntu 9.10 and I'm still having these same problems.

And, intuitively, it seems like I should atleast be able to see the drive even if I'm not able to mount it.  Or more to the point, it seems silly to think that I'd have to install support for NTFS just to reformat it to ext3 or whatever.  That's not what I'm trying to do but given that I *can't* even do something that simple I might as well be trying it.

Any ideas?

---

### Post by yawnmoth on 2009-12-20
Further testament to ntfs-3g's being installed...  if I type in "gksu ntfs-config" in the Terminal I get this:

ubuntu@ubuntu:~$ gksu ntfs-config
ubuntu@ubuntu:~$

ie. it looks as though it's running to completion without producing any errors.

---

