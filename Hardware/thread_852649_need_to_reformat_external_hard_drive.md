---
title: "need to reformat external hard drive"
date: 2008-07-07
forum: Hardware
---

### Post by brettzwo on 2008-07-07
I'm running Ubuntu 8.04.  I'm trying to reformat a My Book external hard drive that went bad.  I tried zeroing it out on my iMac and that seemed to work, but when I tried formating it on the iMac it just spun and spun for hours not doing anthing.  It won't mount on the iMac or my Ubuntu system.  I can however see it in iMac disk utility as was the case in the above description.

I also tried downloading and using GParted and it seemed to recognize it; however, there was no way to reformat or partition the drive that I could see.

Any help would be greatly appreciated.

Thank you,

-Brett

---

### Post by stinger30au on 2008-07-07
> **brettzwo said:**
> 

I also tried downloading and using GParted and it seemed to recognize it; however, there was no way to reformat or partition the drive that I could see.

Any help would be greatly appreciated.

Thank you,

-Brett



right click on the partition with gparted and you can delete the partion and reformat it in there.

make sure you start gparted from a shell by this

gksu gparted

then all will be ok

---

### Post by brettzwo on 2008-07-07
I know I'm going to sound like an idiot, but really I'm tired and I've been messing with this thing for days and have become a bit delirious.  Unfortunately, it was an oversight on my part but Ubuntu does NOT recognize the external USB drive.  I was looking at an internal hard drive partition...ooops!

Any other ideas?

I did take the drive back down to my iMac and it CAN recognize it in Disk Utility although it won't mount.  When I try to partition it in iMac Disk Utility I just get spin, spin, spin and nothing happens for hours.

Any help would be GREATLY appreciated.

Thank you,

-Brett

---

### Post by mtbsoft on 2008-07-07
Sorry to be the bearer of bad news but I'm not sure that Hardy will recognise the MyBook at the moment. I've seen this problem reported elsewhere and experienced it myself - my own 2Tb MyBook is ignored by Hardy on all my machines.

---

### Post by Odrodzona-Sarmacja on 2008-07-09
If you run "sudo blkid" and your hard drive doesn't shows up there, then you must look for and install a driver for it. See the manufacturer home page for Linux drives for their hard drive. They may have a forum on their pages for users of their hardware, a good place to start talking about the Linux driver issue too. Good luck!

---

### Post by mtbsoft on 2008-07-17
Ok, this is interesting.  I finally got the opportunity to try some more testing and it appears that I can now see the drive, it (now) simply doesn't automount.  Maybe this is the result of a recent update or maybe I just wasn't looking hard enough because I expected it to appear as a USB device..

GParted recognises it now, I've tried the sudo blkid command which gave the following...

```
< snip >
/dev/sdb1: UUID="FC1C445E1C4415D4" LABEL="My Book 1" TYPE="ntfs" 
```

 ...and the following appeared in the messages log...

```
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.330344] usb 5-4: new high speed USB device using ehci_hcd and address 6
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.470750] usb 5-4: configuration #1 chosen from 1 choice
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.829968] usbcore: registered new interface driver libusual
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.897392] usbcore: registered new interface driver hiddev
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.901848] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.1/input/input10
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.930879] input,hidraw0: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-4
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.930900] usbcore: registered new interface driver usbhid
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.930904] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.963474] Initializing USB Mass Storage driver...
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.998228] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.999465] usbcore: registered new interface driver usb-storage
Jul 17 20:54:36 ubuntu-9400 kernel: [ 5531.999470] USB Mass Storage support registered.
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.002598] scsi 2:0:0:0: Enclosure         WD       My Book Device   104a PQ: 0 ANSI: 4
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.007927] scsi 2:0:0:1: Direct-Access     WD       My Book          104a PQ: 0 ANSI: 4
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.008969] scsi 2:0:0:0: Attached scsi generic sg2 type 13
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.020673] sd 2:0:0:1: [sdb] 3907026944 512-byte hardware sectors (2000398 MB)
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.021879] sd 2:0:0:1: [sdb] Write Protect is off
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.024052] sd 2:0:0:1: [sdb] 3907026944 512-byte hardware sectors (2000398 MB)
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.025310] sd 2:0:0:1: [sdb] Write Protect is off
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.025322]  sdb: sdb1
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.033514] sd 2:0:0:1: [sdb] Attached SCSI disk
Jul 17 20:54:42 ubuntu-9400 kernel: [ 5537.033561] sd 2:0:0:1: Attached scsi generic sg3 type 0
```

...so it just seems like I have to mount and unmount it manually each time I want to use it. So I'm happy now - hope this helps.

---

