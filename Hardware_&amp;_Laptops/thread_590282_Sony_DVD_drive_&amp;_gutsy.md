---
title: "Sony DVD drive &amp; gutsy"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by thewretched on 2007-10-24
Hello there!

I will preface my question by stating that I am quite new to the whole linux experience, but quite competent with computers in general. I ran Kubuntu on an old laptop for a while, and recently installed Gutsy on my desktop (so i'm brand new to GNOME.)

At any rate, I have 2 internal CD drives, a CDRW and a Sony DVD drive. Both are fully functional under windows. Both are mounting without issue, and show up as devices under  /etc/fstab. However, my DVD-ROM drive seems to be having issues. When I insert any DVD (and I have tried several), the drive mounts up and then proceeds to read the disk like its seeking but can't find any sectors. I can read the contents of disc (in most cases, the TS_AUDIO and VIDEO folders), and can watch individual .VOB files using MPlayer. However, I can't use the "play disc" option (I get a seek error).

Also, yesterday I started getting a "disk full" message. I poked around and found that my log files (syslog, kern.log, and messages) were up to 2.6 gigs each and were taking up my entire linux partition. The repeated error message was simply the drive seeking sectors and not finding them, and then a bunch of error messages about the tray being open after I eject the DVD.

So, I have no idea what the deal is. I would appreciate any input! :)

---

### Post by thewretched on 2007-10-24
Tried disabling DMA, as well as changing device options in MPlayer (it looks for /dev/dvd, but my drive was /dev/cdrom1) to no avail. Rechecked DVD drive in windows, and it works fine.

Anyone?

---

### Post by thewretched on 2007-10-24
My error, from syslog:


Oct 24 20:37:43 Stealth hald: mounted /dev/sda1 on behalf of uid 0
Oct 24 20:42:01 Stealth NetworkManager: <debug> [1193272921.826569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_PLAID_GREEDY_BABY'). 
Oct 24 20:42:02 Stealth kernel: [  373.872000] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 24 20:42:02 Stealth kernel: [  373.908000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'PLAID_GREEDY_BABY', timestamp 2006/04/28 11:31 (1f10)
Oct 24 20:42:13 Stealth kernel: [  384.964000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 24 20:42:13 Stealth kernel: [  384.964000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 24 20:42:13 Stealth kernel: [  384.964000] ide: failed opcode was: unknown
Oct 24 20:42:13 Stealth kernel: [  384.964000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Oct 24 20:42:13 Stealth kernel: [  384.964000] end_request: I/O error, dev hdc, sector 428692
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107173
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107174
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107175
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107176
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107177
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107178
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107179
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107180
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107181
Oct 24 20:42:13 Stealth kernel: [  384.964000] Buffer I/O error on device hdc, logical block 107182
Oct 24 20:42:13 Stealth kernel: [  385.416000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 24 20:42:13 Stealth kernel: [  385.416000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 24 20:42:13 Stealth kernel: [  385.416000] ide: failed opcode was: unknown
Oct 24 20:42:13 Stealth kernel: [  385.416000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Oct 24 20:42:13 Stealth kernel: [  385.416000] end_request: I/O error, dev hdc, sector 430244
Oct 24 20:42:13 Stealth kernel: [  385.448000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 24 20:42:13 Stealth kernel: [  385.448000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 24 20:42:13 Stealth kernel: [  385.448000] ide: failed opcode was: unknown
Oct 24 20:42:13 Stealth kernel: [  385.448000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Oct 24 20:42:13 Stealth kernel: [  385.448000] end_request: I/O error, dev hdc, sector 430244
Oct 24 20:42:13 Stealth kernel: [  385.480000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 24 20:42:13 Stealth kernel: [  385.480000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 24 20:42:13 Stealth kernel: [  385.480000] ide: failed opcode was: unknown

---

### Post by thewretched on 2007-10-24
Ah! Error fixed after installing libdvdcss2 and w32codecs packages!

Sorry to waste forum space :)

---

