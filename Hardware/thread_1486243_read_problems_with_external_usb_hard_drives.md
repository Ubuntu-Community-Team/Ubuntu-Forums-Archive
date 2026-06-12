---
title: "read problems with external usb hard drives"
date: 2010-05-17
forum: Hardware
---

### Post by barna on 2010-05-17
Hi,
Recently I have problems with my external usb hard drives. Programs (for example gwenview) are terribly slow when reading pictures from this drive. From time to time pictures appear corrupted in the image viewer (and also in gimp, so that doesn't seem to be a problem in the viewer). 

I have set up an udev rule, following the suggestion here: [http://bugs.gentoo.org/show_bug.cgi?id=177266](http://bugs.gentoo.org/show_bug.cgi?id=177266) to set max_sectors to 128, but it did not change anything, corrupt pictures occured before and after as well.

The output of dmesg contains this for a session, when images were read in corrutply.

```

[ 5002.881037] usb 1-1: USB disconnect, address 5
[ 5006.973035] hub 1-0:1.0: over-current change on port 1
[ 5011.465062] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 5011.617957] usb 1-1: configuration #1 chosen from 1 choice
[ 5011.620321] scsi5 : SCSI emulation for USB Mass Storage devices
[ 5011.620870] usb-storage: device found at 6
[ 5011.620878] usb-storage: waiting for device to settle before scanning
[ 5016.616347] usb-storage: device scan complete
[ 5016.620682] scsi 5:0:0:0: Direct-Access     WDC WD32 00BEVT-22ZCT0         PQ: 0 ANSI: 2
[ 5016.623899] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 5016.641154] sd 5:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 5016.643552] sd 5:0:0:0: [sdb] Write Protect is off
[ 5016.643568] sd 5:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 5016.643578] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 5016.648929] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 5016.648952]  sdb: sdb1
[ 5016.690323] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 5016.690344] sd 5:0:0:0: [sdb] Attached SCSI disk

```

And most recently the plugged in disk appeared in my system, but when I tried to open it, it disappeared completely, and dmesg was populated with lots of these messages:

```

[ 5485.091747] sd 6:0:0:0: [sdb] Unhandled error code
[ 5485.091751] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 5485.091756] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 3f 00 00 08 00
[ 5485.091773] end_request: I/O error, dev sdb, sector 4159
[ 5485.106200] sd 6:0:0:0: [sdb] Unhandled error code
[ 5485.106210] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 5485.106218] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 5485.106236] end_request: I/O error, dev sdb, sector 0
[ 5485.110298] sd 6:0:0:0: [sdb] Unhandled error code
[ 5485.110305] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 5485.110313] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 5485.110332] end_request: I/O error, dev sdb, sector 0
[ 5485.110530] sd 6:0:0:0: [sdb] Unhandled error code
[ 5485.110534] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 5485.110540] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 5485.110556] end_request: I/O error, dev sdb, sector 0
[ 5485.305073] usb 2-2: new full speed USB device using ohci_hcd and address 4
[ 5485.485054] usb 2-2: device descriptor read/64, error -62
[ 5485.772082] usb 2-2: device descriptor read/64, error -62
[ 5486.048251] usb 2-2: new full speed USB device using ohci_hcd and address 5
[ 5486.228328] usb 2-2: device descriptor read/64, error -62
[ 5486.513054] usb 2-2: device descriptor read/64, error -62
[ 5486.793093] usb 2-2: new full speed USB device using ohci_hcd and address 6
[ 5487.201044] usb 2-2: device not accepting address 6, error -62
[ 5487.377058] usb 2-2: new full speed USB device using ohci_hcd and address 7
[ 5487.785145] usb 2-2: device not accepting address 7, error -62
[ 5487.785209] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 5487.785233] usb 1-2: USB disconnect, address 7

```

These problems started after upgrading to 10.04, but this may be also due to hardware problems. The USB HDD in questions works without any problem under Windows, however, my mobile phone [having a usb mass storage interface] also disappears from the system under linux and windows as well (this might be due to the phone, since it displayed 'Connected...' even hours after unplugging it from the computer, and I had to switch it off/on to be able to use it again...)

Can someone give any hint, how to judge whether this is a hardware issue (my notebook's USB ports, or the external devices), or a software issue? What else can I check?

Thanks

---

### Post by 666f6f on 2011-01-23
I am running Ubuntu 10.10 and I'm experiencing the same problem..

EDIT:  I *was* experiencing a *similar* problem..

---

### Post by barna on 2011-01-24
I strongly believe that in my case the reason was my dying PC. Soon after it was not able to boot from a CD anymore, had problems with USB devices also under Windows, etc. My new notebook has no problems.

---

### Post by 666f6f on 2011-01-24
Hey barna, thanks for posting back after so long.

I had a better look at the error message you posted and, on second thought, it didn't seem I experienced the same problem (for which I had made another post [here]("http://ubuntuforums.org/showthread.php?t=1673499")). 

I connect my USB hard disk via a USB cardbus adapter, which has two USB ports. If on the other USB port I connect a wireless adapter, my hard disk stops working randomly. So, the problem in my case turns out to be insufficient power supply to my cardbus USB adapter (it's true that my cardbus adapter can be power supplied but I have lost it's power supply).

Thrown the wireless adapter away, problem solved!

---

