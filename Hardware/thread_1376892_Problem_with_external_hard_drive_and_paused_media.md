---
title: "Problem with external hard drive and paused media"
date: 2010-01-09
forum: Hardware
---

### Post by spearofsolomon on 2010-01-09
I'm using Ubuntu 9.10 but I'm not sure this problem has as much to do with Ubuntu as it does with the hard drive.  I'm using an Iomega 1.5 TB external hard drive over USB 2.0.  When I plug the drive in for the first time it works fine.  I have backed up several hundred GB onto it and retrieved a lot of data without issue.

My problem started when I began listening to music or watching movies on the drive.  As long as I keep listening or watching, I don't have issues, but if I pause the media player for long enough, when I try to resume the player will try for a few seconds, then the drive will make a clicking sound and disconnect.  I can't do anything with it, and if I leave it plugged in it can even prevent my computer from shutting down all the way.  Turning it off and on again doesn't help reconnect it - I usually have to reboot the computer for it to connect again after this issue.

One day I was looking through dmesg for help on another issue and I spotted something that seemed like info about this issue.  I didn't have time to collect the data until today, so here it is:

[ 7637.190093] usb 2-1: new high speed USB device using ehci_hcd and address 7
[ 7637.343371] usb 2-1: configuration #1 chosen from 1 choice
[ 7637.344053] scsi6 : SCSI emulation for USB Mass Storage devices
[ 7637.344310] usb-storage: device found at 7
[ 7637.344315] usb-storage: waiting for device to settle before scanning
[ 7642.342925] usb-storage: device scan complete
[ 7642.343573] scsi 6:0:0:0: Direct-Access     ST315003 41AS                  PQ: 0 ANSI: 2 CCS
[ 7642.344515] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 7642.345526] sd 6:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[ 7642.346651] sd 6:0:0:0: [sdc] Write Protect is off
[ 7642.346660] sd 6:0:0:0: [sdc] Mode Sense: 34 00 00 00
[ 7642.346667] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 7642.349345] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 7642.349358]  sdc: sdc1
[ 7653.802794] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 7653.802806] sd 6:0:0:0: [sdc] Attached SCSI disk
[13157.132891] usb 2-1: reset high speed USB device using ehci_hcd and address 7
[13159.308314] usb 2-1: USB disconnect, address 7
[13159.308483] sd 6:0:0:0: Device offlined - not ready after error recovery
[13159.308508] sd 6:0:0:0: [sdc] Unhandled error code
[13159.308513] sd 6:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[13159.308522] end_request: I/O error, dev sdc, sector 971557735
[13159.308534] Buffer I/O error on device sdc1, logical block 121444709
[13159.308549] Buffer I/O error on device sdc1, logical block 121444710
[13159.308557] Buffer I/O error on device sdc1, logical block 121444711
[13159.308565] Buffer I/O error on device sdc1, logical block 121444712
[13159.308572] Buffer I/O error on device sdc1, logical block 121444713
[13159.308580] Buffer I/O error on device sdc1, logical block 121444714
[13159.308587] Buffer I/O error on device sdc1, logical block 121444715
[13159.308594] Buffer I/O error on device sdc1, logical block 121444716
[13159.308601] Buffer I/O error on device sdc1, logical block 121444717
[13159.308655] sd 6:0:0:0: rejecting I/O to offline device
[13159.308672] sd 6:0:0:0: rejecting I/O to offline device
[13159.308730] sd 6:0:0:0: rejecting I/O to offline device
[13159.308755] sd 6:0:0:0: [sdc] Unhandled error code
[13159.308760] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13159.308768] end_request: I/O error, dev sdc, sector 971557975
[13159.602545] usb 2-1: new high speed USB device using ehci_hcd and address 8
[13159.769655] usb 2-1: configuration #1 chosen from 1 choice
[13159.781523] scsi7 : SCSI emulation for USB Mass Storage devices
[13159.781652] usb-storage: device found at 8
[13159.781654] usb-storage: waiting for device to settle before scanning
[13164.781092] usb-storage: device scan complete
[13164.902614] usb 2-1: reset high speed USB device using ehci_hcd and address 8
[13165.063680] usb 2-1: device firmware changed
[13165.064508] usb 2-1: USB disconnect, address 8
[13165.219908] usb 2-1: new high speed USB device using ehci_hcd and address 9
[13165.374673] usb 2-1: configuration #1 chosen from 1 choice
[13165.391450] scsi8 : SCSI emulation for USB Mass Storage devices
[13165.396359] usb-storage: device found at 9
[13165.396362] usb-storage: waiting for device to settle before scanning
[13170.400378] usb-storage: device scan complete
[13170.401045] scsi 8:0:0:0: Direct-Access     ST315003 41AS                  PQ: 0 ANSI: 2 CCS
[13170.402238] sd 8:0:0:0: Attached scsi generic sg3 type 0
[13170.580093] usb 2-1: reset high speed USB device using ehci_hcd and address 9
[13170.731479] usb 2-1: device firmware changed
[13170.731611] usb 2-1: USB disconnect, address 9
[13170.732032] sd 8:0:0:0: [sdd] READ CAPACITY failed
[13170.732040] sd 8:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[13170.732050] sd 8:0:0:0: [sdd] Sense not available.
[13170.732184] sd 8:0:0:0: [sdd] Write Protect is off
[13170.732191] sd 8:0:0:0: [sdd] Mode Sense: 00 00 00 00
[13170.732197] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[13170.740581] sd 8:0:0:0: [sdd] READ CAPACITY failed
[13170.740589] sd 8:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13170.740599] sd 8:0:0:0: [sdd] Sense not available.
[13170.740632] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[13170.740641] sd 8:0:0:0: [sdd] Attached SCSI disk

I waited to plug the drive in until after the bootup was complete, and then I started a movie and paused it.  Later I clicked play again and caused the issue, and so you can see

[ 7653.802806] sd 6:0:0:0: [sdc] Attached SCSI disk
[13157.132891] usb 2-1: reset high speed USB device using ehci_hcd and address 7
[13159.308314] usb 2-1: USB disconnect, address 7

where it finishes attaching at 7653 and at 13157 it starts to error.

I can reproduce the problem with multiple media players using multiple types of media.  I can successfully pause and resume media but only if the delay is short, although I haven't found a reproducible number.  Sometimes it can be as low as a minute, other times half an hour.

Thanks for any ideas in debugging this problem.

---

