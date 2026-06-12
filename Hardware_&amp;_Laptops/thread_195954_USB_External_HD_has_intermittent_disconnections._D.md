---
title: "USB External HD has intermittent disconnections. Dapper involved ?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by TomG on 2006-06-13
Hi,

I have a 300gb sata Maxtor disk in a USB box from a few months and recently I have intermittent USB disconnections. :( 
I thought first that it could be due to overheat but after putting powerful fan on it I still get problem...
As I recently upgraded to Dapper I wonder if it could be linked ? :confused: 
I dont remember having such problem before with this disk...
Below the /var/log/messages on last occurence. 
Note that I have also 2 USB key without same problem...

Please advise me. Tx,
TomG

```


Jun 13 20:23:30 localhost kernel: [4303697.460000] sd 4:0:0:0: SCSI error: return code = 0x70000
Jun 13 20:23:30 localhost kernel: [4303697.460000] end_request: I/O error, dev sdb, sector 502372596
Jun 13 20:23:30 localhost kernel: [4303697.460000] lost page write due to I/O error on sdb2
Jun 13 20:23:30 localhost kernel: [4303697.460000] usb 2-4.4: USB disconnect, address 5
Jun 13 20:23:30 localhost kernel: [4303697.461000] sd 4:0:0:0: SCSI error: return code = 0x10000
Jun 13 20:23:30 localhost kernel: [4303697.461000] end_request: I/O error, dev sdb, sector 502372604
Jun 13 20:23:30 localhost kernel: [4303697.461000] lost page write due to I/O error on sdb2
Jun 13 20:23:30 localhost last message repeated 8 times
Jun 13 20:23:30 localhost kernel: [4303697.461000] sd 4:0:0:0: SCSI error: return code = 0x10000
Jun 13 20:23:30 localhost kernel: [4303697.461000] end_request: I/O error, dev sdb, sector 502372836
Jun 13 20:23:30 localhost kernel: [4303697.690000] usb 2-4.4: new high speed USB device using ehci_hcd and address 8
Jun 13 20:23:30 localhost kernel: [4303697.783000] scsi6 : SCSI emulation for USB Mass Storage devices
Jun 13 20:23:35 localhost kernel: [4303702.788000]   Vendor: Maxtor 6  Model: V300F0            Rev:
Jun 13 20:23:35 localhost kernel: [4303702.788000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jun 13 20:23:35 localhost kernel: [4303702.791000] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
Jun 13 20:23:35 localhost kernel: [4303702.792000] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
Jun 13 20:23:35 localhost kernel: [4303702.793000]  sdc: sdc1 sdc2
Jun 13 20:23:35 localhost kernel: [4303702.812000] sd 6:0:0:0: Attached scsi disk sdc
Jun 13 20:23:35 localhost kernel: [4303702.812000] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jun 13 20:23:36 localhost kernel: [4303703.557000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
Jun 13 20:23:36 localhost kernel: [4303703.557000] kjournald starting.  Commit interval 5 seconds
Jun 13 20:23:36 localhost kernel: [4303703.559000] EXT3 FS on sdc2, internal journal
Jun 13 20:23:36 localhost kernel: [4303703.559000] EXT3-fs: recovery complete.
```

---

### Post by rplantz on 2006-07-19
I am having a similar problem. It occurs when trying to use rsync to backup. Here is part of my /var/log/messages file:
```

Jul 18 21:07:19 localhost kernel: [ 2295.296377] usb 3-1: reset high speed USB device using ehci_hcd and address 6
Jul 18 21:07:20 localhost kernel: [ 2295.704111] usb 3-1: USB disconnect, address 6
Jul 18 21:07:20 localhost kernel: [ 2295.705710] sd 5:0:0:0: SCSI error: return code = 0x10000
Jul 18 21:07:20 localhost kernel: [ 2295.705715] end_request: I/O error, dev sdb, sector 84479336
Jul 18 21:07:20 localhost kernel: [ 2295.705723] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705740] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705745] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705751] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705756] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705761] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705765] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705770] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705774] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705779] lost page write due to I/O error on sdb5
Jul 18 21:07:20 localhost kernel: [ 2295.705810] sd 5:0:0:0: SCSI error: return code = 0x10000
Jul 18 21:07:20 localhost kernel: [ 2295.705812] end_request: I/O error, dev sdb, sector 84479576
Jul 18 21:07:20 localhost kernel: [ 2295.879284] __journal_remove_journal_head: freeing b_committed_data

```

I never had any problems doing this with Breezy. (Yes, it's been a while since I did a backup. Busted!)

---

### Post by TomG on 2006-07-19
Thx for your post. 
I did further tests from this :
 o I connected my (SATA) disk directly on motherboard -> no problem
 o I tested my USB box on WinXP SP2 (different PC) also -> problem reproduced !
So I wonder if in my case it is not more a hardware problem (USB Box)... May be the upgrade to Dapper is a coincidence...

---

### Post by rplantz on 2006-07-19
I think it was also a hardware problem for me -- the usb connector on my computer. I accidentally kicked a usb cable that was plugged into the front connector a while back. I have plugged my disk into a connector on the rear, and it is still mounted after an hour or so.

---

### Post by YorYor on 2006-07-29
Intermittent errors usually mean it's a hardware fault. Especially when it's via a USB cable. Make sure you plug it to a USB header that is directly plugged to the motherboard (safest bet is one of those located on the backplate).

If your USB cable has 2 headers for additional power, then use it! Don't go through a USB hub because the total current supplied to the hub from the motherboard is still only 500mA (if you have 2 devices plugged to the USB hub, then the combined current supplied to both will never exceed 500mA).

I've recently had a change in my portable harddisk, from a Toshiba to a Hitachi. The Toshiba worked fine with just one power connector (my external USB box had 2, one for power and data transfer, and another one for additional power), whereas the Hitachi needed both connectors to be plugged in before it would work stably.

Another incident is my desktop. I have 2 optical drives, 2 PATA harddrives and 1 SATA. There was a period when somehow the power distributed by my power supply seems to be insufficient, and I'd get the device disconnected error. Previously though it could be my drive failing, but everything would run stably once I disconnect one of the drives.

So I'm pretty sure it's a power issue if you are sure your drive is not starting to show symptoms of "harddrive cancer" known as bad sectors.

---

