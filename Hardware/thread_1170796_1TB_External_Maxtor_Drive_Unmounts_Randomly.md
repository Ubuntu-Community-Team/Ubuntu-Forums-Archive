---
title: "1TB External Maxtor Drive Unmounts Randomly"
date: 2009-05-26
forum: Hardware
---

### Post by dblencowe on 2009-05-26
Hey there,

Recently I converted my Desktop over to the latest release of Ubuntu (Jaunty) and found that I am thoroughly enjoying the experience bar one small problem.
At random intervals, whether the device is in use or not the Kernel will dismount my External USB Hard Drive.

Below I have included clippings of my log files which show the error occuring and the results of it:

**A lot of this, recurring:**
> May 26 22:23:37 david-desktop ntfs-3g[3463]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
May 26 22:23:37 david-desktop ntfs-3g[3463]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error

**Then the drive is dismounted**
> May 26 22:23:37 david-desktop kernel: [ 7959.238389] usb 2-4: new high speed USB device using ehci_hcd and address 5
May 26 22:23:37 david-desktop hald: unmounted /dev/sdf1 from '/media/disk' on behalf of uid 0

**A couple more errors amongst other things**
> May 26 22:23:52 david-desktop kernel: [ 7974.353847] usb 2-4: device descriptor read/64, error -110
May 26 22:24:07 david-desktop kernel: [ 7989.569821] usb 2-4: device descriptor read/64, error -110
May 26 22:24:07 david-desktop kernel: [ 7989.785849] usb 2-4: new high speed USB device using ehci_hcd and address 6
May 26 22:24:23 david-desktop kernel: [ 8004.901825] usb 2-4: device descriptor read/64, error -110
May 26 22:24:31 david-desktop kernel: [ 8013.134050] hub 2-0:1.0: unable to enumerate USB device on port 4
May 26 22:24:54 david-desktop kernel: [ 8036.158526] usb 2-4: new high speed USB device using ehci_hcd and address 7
May 26 22:24:54 david-desktop kernel: [ 8036.290257] usb 2-4: configuration #1 chosen from 1 choice
May 26 22:24:54 david-desktop kernel: [ 8036.294417] scsi6 : SCSI emulation for USB Mass Storage devices
May 26 22:24:54 david-desktop kernel: [ 8036.295000] usb-storage: device found at 7
May 26 22:24:54 david-desktop kernel: [ 8036.295003] usb-storage: waiting for device to settle before scanning
May 26 22:24:59 david-desktop kernel: [ 8041.295895] usb-storage: device scan complete
May 26 22:24:59 david-desktop kernel: [ 8041.295895] scsi 6:0:0:0: Direct-Access     Maxtor   Basics Desktop   0122 PQ: 0 ANSI: 4
May 26 22:24:59 david-desktop kernel: [ 8041.298576] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
May 26 22:24:59 david-desktop kernel: [ 8041.305803] sd 6:0:0:0: [sdg] Write Protect is off
May 26 22:24:59 david-desktop kernel: [ 8041.305803] sd 6:0:0:0: [sdg] Mode Sense: 2d 08 00 00
May 26 22:24:59 david-desktop kernel: [ 8041.305803] sd 6:0:0:0: [sdg] Assuming drive cache: write through
May 26 22:24:59 david-desktop kernel: [ 8041.314457] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
May 26 22:24:59 david-desktop kernel: [ 8041.314457] sd 6:0:0:0: [sdg] Write Protect is off
May 26 22:24:59 david-desktop kernel: [ 8041.314457] sd 6:0:0:0: [sdg] Mode Sense: 2d 08 00 00
May 26 22:24:59 david-desktop kernel: [ 8041.314457] sd 6:0:0:0: [sdg] Assuming drive cache: write through
May 26 22:24:59 david-desktop kernel: [ 8041.314457]  sdg: sdg1
May 26 22:24:59 david-desktop kernel: [ 8041.347297] sd 6:0:0:0: [sdg] Attached SCSI disk
May 26 22:24:59 david-desktop kernel: [ 8041.347297] sd 6:0:0:0: Attached scsi generic sg6 type 0

Then nothing, I have tried remounting both manually and automatically, cutting power to the drive for a bit and then restoring and then finally rebooting which solves the problem for a while.

If there is anything you can do to help me solve this I would be grateful as it has left me quite stumped!

Thanks for your time,
David Blencowe

---

### Post by HavocXphere on 2009-05-26
> Failed to read of MFT
That does not sound good.:( IO errors on the MFT should not happen.

Sounds like either the filesystem or the physical drive is damaged.

Chances are that windows will just ignore this and move on. Ubuntu unmounts it. Either way something is wrong.

I'd suggest making backups of important data. Then run a windows disk check. Then run a test to check the physical disk itself. (like spinrite or something)

---

### Post by cmcanulty on 2009-10-09
My Maxtor and Western Digital ext drives both unmount randomly it is driving me crazy I can't do backups and no solutions on forums so far.They both work fine with windows. I also get input output errors every time the disk unmounts.

---

### Post by saschi on 2009-11-21
I have the sama problem since upgrading to Jaunty. This happens to both, my 1TB Maxtor external HDD AND my 500GB Toshiba drive which I bought only 2 days ago.
Both disks also pass the filesystem check provided with the new drive management tool.

I have no idea what to do about this...:sad:

---

### Post by sethg on 2009-12-14
I have the exact problem with my 500 gb external. Windows disk check says there's nothing wrong with it. It's pretty annoying really. It unmounts and I have to reboot to get it to show up, because nothing plugged in is mountable paste login.

I wish I'd never upgraded to Karmic sometimes. A few things work better, but most works much worse.

---

