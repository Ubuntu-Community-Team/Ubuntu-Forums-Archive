---
title: "Failed Drive Recovery"
date: 2016-04-22
forum: Hardware
---

### Post by scambro on 2016-04-22
I believe I've had a drive failure, not the primary drive for my lubuntu system, but a secondary one.  It's failed "differently" than any other drive I've lost before, so I'm not sure what's happening.  It was totally operational, then I shut the server down to change some power plugs around.  The server seemed to freeze upon shut down, so after about 20 minutes, I manually powered it off.  When I boot up the system with the drive in question plugged in, I get the following messages in /var/log/syslog:

```

ata2: EH complete
ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata2.01: BMDMA stat 0x45
ata2.01: failed command: READ DMA
ata2.01: cmd c8/00:06:02:00:00/00:00:00:00:00/f0 tag 0 dma 3072 in
         res 51/04:06:02:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
ata2.01: status: { DRDY ERR }
ata2.01: error: { ABRT }
ata2.01: configured for UDMA/133 (device error ignored)
...
sd 1:0:1:0: [sdc]  
Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sd 1:0:1:0: [sdc]  
Sense Key : Aborted Command [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
        72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
        00 00 00 02 
sd 1:0:1:0: [sdc]  
Add. Sense: No additional sense information
sd 1:0:1:0: [sdc] CDB: 
Read(10): 28 00 00 00 00 02 00 00 06 00
end_request: I/O error, dev sdc, sector 2

```

When I do an fdisk -l, the drive doesn't show at all, and it makes my syslog file show a bunch of those same errors again.  When I look at /dev/sdc (since I see [sdc] in the log), it says it's a 4GB mount, which isn't true, the drive should be 1.5TB.  I can't seem to run any diagnostics on the drive because it isn't even showing to me... 

Any suggestions?  Is the drive just likely toasted?  Thanks!

---

### Post by weatherman2 on 2016-04-22
Obviously, check the power and data cables again.  If you have a monitor on this thing and can physically access it, consider disconnecting all other drives, connect this one to a known good cables, then boot a live USB of Linux.  Install GSmartControl or smartmontools to see if the drive's S.M.A.R.T. status can be obtained at all.  If you can't physically access the server (to boot up a live USB), you might try to remove the drive and plug it into another working computer.

But it sure sounds like a catastrophic hard drive failure, and you'd just be verifying that.  It happens!

---

### Post by scambro on 2016-04-22
Yeah - that's what I'm afraid of.  I swapped the SATA cable already, just tried a different power cable, but no change.  I ran smartctrl on it before and just get a SCSI read error message.  Oh well...  This was a drive with stuff on it that I deemed "losable."  I guess this is losing it!

---

