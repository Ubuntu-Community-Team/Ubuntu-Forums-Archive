---
title: "Slow File Transfer between USB HD &amp; Computer?"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2008-04-06
I've got an 80GB hard drive in a portable USB case which I use to store a lot of my media files on. I have noticed lately that the file transfer speeds are really slow, ever since I reinstalled 7.04; for example, I was just quoted over seven minutes to transfer ~500MB of files. Earlier today, it took like two hours to transfer about 2GB. I don't recall it being quite this slow before. I also noticed that I was having trouble getting the USB hard drive to mount; I would hear it rev up, then stop, rev up, stop, rev up, stop, but never mount. I think that might have been a balancing issue; I had a rubber band under part of it, which I removed, and now it seems better.

Anyway, what exactly might be my file transfer problem? I'm not really running anything heavy right now: Firefox, an idle session of K3b, that's it. I'm hoping my drive isn't dying...:(

-Dan

---

### Post by rogblake on 2008-04-06
> **dbsoundman said:**
> 
Anyway, what exactly might be my file transfer problem? I'm not really running anything heavy right now: Firefox, an idle session of K3b, that's it. I'm hoping my drive isn't dying...:(

-Dan

You should check your system log file (/var/log/messages) for entries related to the drive. If you see "bad sector" type errors the drive is probably dying. If you see "USB disconnect/USB reset" type messages you may have a compatibility problem.

---

### Post by dbsoundman on 2008-04-09
I deleted my Feisty install and didn't check the log file first, but I just had the spin up/down problem in Hardy, here's my log output:
[CODEApr  9 16:10:48 blackdiamond kernel: [  533.370575] usb 4-2: new high speed USB device using ehci_hcd and address 2
Apr  9 16:10:48 blackdiamond kernel: [  533.498718] usb 4-2: configuration #1 chosen from 1 choice
Apr  9 16:10:48 blackdiamond kernel: [  533.638130] usbcore: registered new interface driver libusual
Apr  9 16:10:48 blackdiamond kernel: [  533.711228] Initializing USB Mass Storage driver...
Apr  9 16:10:48 blackdiamond kernel: [  533.717275] scsi0 : SCSI emulation for USB Mass Storage devices
Apr  9 16:10:48 blackdiamond kernel: [  533.723320] usbcore: registered new interface driver usb-storage
Apr  9 16:10:48 blackdiamond kernel: [  533.723335] USB Mass Storage support registered.
Apr  9 16:10:59 blackdiamond kernel: [  544.327649] usb 4-2: USB disconnect, address 2
Apr  9 16:10:59 blackdiamond kernel: [  544.328564] scsi 0:0:0:0: Device offlined - not ready after error recovery
Apr  9 16:12:29 blackdiamond kernel: [  634.692935] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr  9 16:12:30 blackdiamond kernel: [  634.820611] usb 1-2: not running at top speed; connect to a high speed hub
Apr  9 16:12:30 blackdiamond kernel: [  634.852749] usb 1-2: configuration #1 chosen from 1 choice
Apr  9 16:12:30 blackdiamond kernel: [  634.864817] scsi1 : SCSI emulation for USB Mass Storage devices
Apr  9 16:12:35 blackdiamond kernel: [  639.878597] scsi 1:0:0:0: Direct-Access     WDC WD80 0BB-00JKC0       0811 PQ: 0 ANSI: 0
Apr  9 16:12:35 blackdiamond kernel: [  639.910232] Driver 'sd' needs updating - please use bus_type methods
Apr  9 16:12:35 blackdiamond kernel: [  639.915563] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  9 16:12:35 blackdiamond kernel: [  639.922515] sd 1:0:0:0: [sda] Test WP failed, assume Write Enabled
Apr  9 16:12:35 blackdiamond kernel: [  639.927500] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  9 16:12:35 blackdiamond kernel: [  639.934504] sd 1:0:0:0: [sda] Test WP failed, assume Write Enabled
Apr  9 16:12:35 blackdiamond kernel: [  639.934527]  sda: sda1
Apr  9 16:12:35 blackdiamond kernel: [  639.942697] sd 1:0:0:0: [sda] Attached SCSI disk
Apr  9 16:12:35 blackdiamond kernel: [  639.959035] sd 1:0:0:0: Attached scsi generic sg0 type 0
Apr  9 16:13:40 blackdiamond kernel: [  704.878236] usb 1-2: reset full speed USB device using uhci_hcd and address 2
Apr  9 16:14:18 blackdiamond kernel: [  743.353583] usb 1-2: reset full speed USB device using uhci_hcd and address 2
Apr  9 16:14:48 blackdiamond kernel: [  773.593705] usb 1-2: reset full speed USB device using uhci_hcd and address 2
Apr  9 16:14:50 blackdiamond kernel: [  774.819809] sd 1:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Apr  9 16:14:50 blackdiamond kernel: [  774.819825] end_request: I/O error, dev sda, sector 96
Apr  9 16:15:20 blackdiamond kernel: [  804.920702] usb 1-2: reset full speed USB device using uhci_hcd and address 2
Apr  9 16:15:20 blackdiamond kernel: [  805.054345] sd 1:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Apr  9 16:15:20 blackdiamond kernel: [  805.054362] end_request: I/O error, dev sda, sector 224
Apr  9 16:15:50 blackdiamond kernel: [  835.154061] usb 1-2: reset full speed USB device using uhci_hcd and address 2[/CODE]

Nothing about bad sectors, but I noticed it did repeat the same process a couple times at the beginning. At that point, I was hearing the drive spin up, stop, spin up, stop. Any clues as to what's up?

-Dan

---

### Post by mark541 on 2008-04-16
I noticed this line in your log;

Apr 9 16:12:30 blackdiamond kernel: [ 634.820611] usb 1-2: not running at top speed; connect to a high speed hub

Do you have the hard drive connected directly to your PC, or is it connected to a hub? I've had similar problems with some usb hubs. Some will work just fine, others will identify as USB2, but will only run as USB1.1.

So, if you don't have the drive connected directly to the PC, try that and see what happens. I've had no problems when connecting to USB2 connectors directly on the motherboard, or plugged into PCI USB2 controllers.

Let us know it that works.

---

### Post by dbsoundman on 2008-04-16
Unfortunately, it's connected directly to the PC, so the speed problem is not due to a hub.

I'm wondering if it's mainly just my processor speed. I've only got an Athlon XP 2200+, which hasn't ever exactly impressed me speed-wise...

-Dan

---

### Post by bobbob1016 on 2008-04-17
What file system are you using?  FAT32 or NTFS could be fragmented, that could be the issue.  Not sure if there is a Windows-free way of doing a defrag.  An ext2 or ext3, or basically any Unix partition shouldn't get fragmented to the best of my knowledge.  It is highly highly highly unlikely that it is your CPU speed, more so because if I read correctly, it worked fine before you reinstalled.

---

### Post by timcredible on 2008-04-17
i would check 3 things:

1 - is your usb port on your pc usb2.0?
2 - does your external drive require more power?  some drives need 2 usb ports or 1 usb port plus a/c power to power it properly.
3 - do a fsck on the drive, maybe it's got some back spots preventing it from working correctly.

---

