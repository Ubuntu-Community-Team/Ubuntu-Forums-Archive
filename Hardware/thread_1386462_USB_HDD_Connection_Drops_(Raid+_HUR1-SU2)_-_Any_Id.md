---
title: "USB HDD Connection Drops (Raid+ HUR1-SU2) - Any Ideas?"
date: 2010-01-20
forum: Hardware
---

### Post by M1GEO on 2010-01-20
I have a problem with my [RAID+ HUR1-SU2 Dual 3.5" HDD Raid Enclosure]("http://mediasonicinc.com/store/product_info.php?cPath=26_34&products_id=71").  The enclosure has two 1TB Hitachi drives.

Upon connecting to my Ubuntu 9.10 box via USB, the system recognises the drive and all is well.  This continues to be the case while the drive is kept busy.  If I read/write data from/to the drive, then all is well.  I am also able to stop for a short duration.

My intention was to use the drive to back stuff up to, using a cron based script.  However, if the drive is left for some time (typically 15-20 minutes), then the connection to the computer is lost - if left for a long period of time it usually comes back again.  After I return from uni there are often several Nautilus windows open in /media where the drive *was* mounted, and then the connection died, and then it came back (ubuntu opens a nautilus window displaying the drive when it is mounted).

Below is a quote from the syslog regarding the connection of the drive
> 
Jan 20 23:11:00 transistor kernel: [119183.154269] usb 1-3: new high speed USB device using ehci_hcd and address 38
Jan 20 23:11:00 transistor kernel: [119183.325395] usb 1-3: configuration #1 chosen from 1 choice
Jan 20 23:11:00 transistor kernel: [119183.327119] scsi14 : SCSI emulation for USB Mass Storage devices
Jan 20 23:11:00 transistor kernel: [119183.327225] usb-storage: device found at 38
Jan 20 23:11:00 transistor kernel: [119183.327227] usb-storage: waiting for device to settle before scanning
Jan 20 23:11:05 transistor kernel: [119188.338768] usb-storage: device scan complete
Jan 20 23:11:05 transistor kernel: [119188.361309] scsi 14:0:0:0: Direct-Access     Hitachi  HDT721010SLA360  ST6O PQ: 0 ANSI: 4
Jan 20 23:11:05 transistor kernel: [119188.361685] sd 14:0:0:0: Attached scsi generic sg4 type 0
Jan 20 23:11:05 transistor kernel: [119188.366638] sd 14:0:0:0: [sdd] 3907049984 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jan 20 23:11:05 transistor kernel: [119188.392552] sd 14:0:0:0: [sdd] Write Protect is off
Jan 20 23:11:05 transistor kernel: [119188.392556] sd 14:0:0:0: [sdd] Mode Sense: 10 00 00 00
Jan 20 23:11:05 transistor kernel: [119188.392558] sd 14:0:0:0: [sdd] Assuming drive cache: write through
Jan 20 23:11:05 transistor kernel: [119188.471292] sd 14:0:0:0: [sdd] Assuming drive cache: write through
Jan 20 23:11:05 transistor kernel: [119188.471299]  sdd: sdd1
Jan 20 23:11:05 transistor kernel: [119188.571287] sd 14:0:0:0: [sdd] Assuming drive cache: write through
Jan 20 23:11:05 transistor kernel: [119188.571294] sd 14:0:0:0: [sdd] Attached SCSI disk
Jan 20 23:11:07 transistor kernel: [119190.502206] EXT4-fs (sdd1): barriers enabled
Jan 20 23:11:07 transistor kernel: [119190.611310] kjournald2 starting: pid 11944, dev sdd1:8, commit interval 5 seconds
Jan 20 23:11:07 transistor kernel: [119190.612036] EXT4-fs (sdd1): internal journal on sdd1:8
Jan 20 23:11:07 transistor kernel: [119190.612044] EXT4-fs (sdd1): delayed allocation enabled
Jan 20 23:11:07 transistor kernel: [119190.612047] EXT4-fs: file extents enabled
Jan 20 23:11:08 transistor kernel: [119190.741101] EXT4-fs: mballoc enabled
Jan 20 23:11:08 transistor kernel: [119190.741120] EXT4-fs (sdd1): recovery complete
Jan 20 23:11:08 transistor kernel: [119190.741870] EXT4-fs (sdd1): mounted filesystem with ordered data mode


It is possible to observe the kernel complaining about the device
> 
Jan 20 23:35:20 transistor kernel: [120643.091452] usb 1-3: reset high speed USB device using ehci_hcd and address 38
Jan 20 23:35:35 transistor kernel: [120658.222625] usb 1-3: device descriptor read/64, error -110
Jan 20 23:35:50 transistor kernel: [120673.482939] usb 1-3: device descriptor read/64, error -110
Jan 20 23:35:51 transistor kernel: [120673.721357] usb 1-3: reset high speed USB device using ehci_hcd and address 38
Jan 20 23:36:06 transistor kernel: [120688.862523] usb 1-3: device descriptor read/64, error -110
Jan 20 23:36:21 transistor kernel: [120704.112552] usb 1-3: device descriptor read/64, error -110
Jan 20 23:36:21 transistor kernel: [120704.371351] usb 1-3: reset high speed USB device using ehci_hcd and address 38
Jan 20 23:36:26 transistor kernel: [120709.424390] usb 1-3: device descriptor read/8, error -110
Jan 20 23:36:31 transistor kernel: [120714.582530] usb 1-3: device descriptor read/8, error -110
Jan 20 23:36:32 transistor kernel: [120714.842538] usb 1-3: reset high speed USB device using ehci_hcd and address 38
Jan 20 23:36:37 transistor kernel: [120719.892294] usb 1-3: device descriptor read/8, error -110
Jan 20 23:36:42 transistor kernel: [120725.032529] usb 1-3: device descriptor read/8, error -110
Jan 20 23:36:42 transistor kernel: [120725.142717] sd 14:0:0:0: Device offlined - not ready after error recovery
Jan 20 23:36:42 transistor kernel: [120725.142771] usb 1-3: USB disconnect, address 38
Jan 20 23:36:42 transistor kernel: [120725.149859] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
Jan 20 23:36:42 transistor kernel: [120725.149865] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
Jan 20 23:36:42 transistor kernel: [120725.149867] EXT4-fs: mballoc: 0 generated and it took 0
Jan 20 23:36:42 transistor kernel: [120725.149868] EXT4-fs: mballoc: 0 preallocated, 0 discarded
Jan 20 23:36:42 transistor kernel: [120725.150142] JBD2: I/O error detected when updating journal superblock for sdd1:8.
Jan 20 23:36:42 transistor kernel: [120725.150168] EXT4-fs (sdd1): previous I/O error to superblock detected
Jan 20 23:36:42 transistor kernel: [120725.272086] usb 1-3: new high speed USB device using ehci_hcd and address 39
Jan 20 23:36:57 transistor kernel: [120740.411326] usb 1-3: device descriptor read/64, error -110


The kernel continues to complain for a while, and then 

> 
Jan 20 23:38:04 transistor kernel: [120807.221368] hub 1-0:1.0: unable to enumerate USB device on port 3
Jan 20 23:38:04 transistor kernel: [120807.541381] usb 5-1: new full speed USB device using uhci_hcd and address 25
Jan 20 23:38:05 transistor kernel: [120807.724271] usb 5-1: not running at top speed; connect to a high speed hub *(it is!)*
*<< S...N...I...P --- Generic USB Device attachment>>*
Jan 20 23:38:16 transistor kernel: [120818.943808] EXT4-fs: file extents enabled
Jan 20 23:38:16 transistor kernel: [120819.065565] EXT4-fs: mballoc enabled
Jan 20 23:38:16 transistor kernel: [120819.065591] EXT4-fs (sdd1): recovery complete
Jan 20 23:38:16 transistor kernel: [120819.093794] EXT4-fs (sdd1): mounted filesystem with ordered data mode


This repeats a few times, and then the computer, i assume, gives up.  I have tried with ext4 and ext3.

Here is the drive's *lsusb* entry
> Bus 001 Device 038: ID 0928:0002 Oxford Semiconductor, Ltd

I have tried to poke around in /sys/bus/usb/devices/<deviceid>, and when the device is working everything is as expected.  This remains the case right up until it all goes wrong.

Any advice or help would be greatly appreciated.
Kind Regards, and Thanks in Advance;

---

### Post by M1GEO on 2010-02-01
I assume this has something to do with the disk array or a element in the raid going to sleep.  If i keep the discs busy, the problem doesn't arise.

In order to do this, I have simply made a script to write random data to a file (512K every 10 minutes) to the hard discs using dd and cron.

Since then, I have not had any trouble, *fingers crossed*

Any ideas as to a better (proper) solution are welcome, however.

---

