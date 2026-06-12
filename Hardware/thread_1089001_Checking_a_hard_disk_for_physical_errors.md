---
title: "Checking a hard disk for physical errors"
date: 2009-03-06
forum: Hardware
---

### Post by jlebar on 2009-03-06
Hi, all.

I'm having problems with an external drive which I think are either related to compatibility issues with the controller or the drive itself failing.  In particular, I'm able to format the external drive to ext3, but copies to the drive fail after about an hour, and dmesg reports I/O errors on a few sectors and an error loading the drive's journal when I try to re-mount.

I also had some issues when this drive was formatted as NTFS -- I was unable to access some files, even from Windows.  This may have been caused by physical failure of the drive, or by me messing up the partition by force mounting it from Linux.

I'm a bit skeptical that the problem is the drive: The drive isn't making any of the sounds normally associated with failure, it's less than a year old, and I had absolutely no problems with it before I force mounted it a few weeks ago.  But hey: Anything can happen, right?

Probably the easiest solution to this would be to find an enclosure which is known to work with Ubuntu and try my drive in there.  But I've been unable to locate such a controller.  In the absence of that hardware, I was hoping you guys could share some tips for checking whether the drive is failing, or otherwise diagnosing my problem.  Writing to the drive is definitely an option, as it doesn't have any useful data on it right now.  I'd really appreciate whatever help you all can give.

Thanks,
-Justin

Here's the relevant dmesg output:
```

[40119.976185] usb-storage: device found at 56
[40119.976194] usb-storage: waiting for device to settle before scanning
[40124.976428] usb-storage: device scan complete
[40124.985865] scsi 46:0:0:0: Direct-Access     SAMSUNG  HD753LJ               PQ: 0 ANSI: 2
[40124.989228] sd 46:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
[40124.992057] sd 46:0:0:0: [sdd] Write Protect is off
[40124.992066] sd 46:0:0:0: [sdd] Mode Sense: 38 00 00 00
[40124.992072] sd 46:0:0:0: [sdd] Assuming drive cache: write through
[40124.993760] sd 46:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
[40124.996388] sd 46:0:0:0: [sdd] Write Protect is off
[40124.996396] sd 46:0:0:0: [sdd] Mode Sense: 38 00 00 00
[40124.996400] sd 46:0:0:0: [sdd] Assuming drive cache: write through
[40124.996435]  sdd: sdd1
[40125.016848] sd 46:0:0:0: [sdd] Attached SCSI disk
[40125.017236] sd 46:0:0:0: Attached scsi generic sg3 type 0
[40125.676137] usb 5-8.3: reset high speed USB device using ehci_hcd and address 56
[40136.792755] sd 46:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[40136.792771] end_request: I/O error, dev sdd, sector 732356959
[40136.792833] JBD: Failed to read block at offset 23050
[40136.792865] JBD: recovery failed
[40136.792869] EXT3-fs: error loading journal.
[40136.794416] usb 5-8.3: USB disconnect, address 56

```

---

### Post by kidders on 2009-03-08
Hi there,

This problem could be caused by a lot of things. For example, your motherboard or the cable you're using may be unable to sustain an EHCI connection, or the driver may be having problems operating at high speed.

I suggest trying your disk out on a UHCI interface, to see if it behaves itself. That would eliminate a variety of potential issues ...[LIST]
[*]Run **rmmod ehci_hcd**.
[*]Plug in your device.
[*]Run **dmesg | tail -n20 ** to verify that it's using a UHCI interface.
[/LIST]You may find your disk will work fine at that speed ... at least for a while. If/when it stops working, the end of your dmesg log would be worth looking at. Other things that might be interesting include ...[LIST]
[*]Does your disk work any better on a different USB port? (Bear in mind that ports come in pairs.)
[*]Does changing the cable make any difference?
[*]How many hubs are there between your hard disk and your motherboard? (ie Are you plugging your disk into a port on your keyboard/etc?)
[*]Is the disk enclosure self-powering, or do you plug it into an A/C socket?
[*]What is the output of **cat /sys/block/sdd/device/max_sectors**?
[/LIST]

---

