---
title: "[SOLVED] USB HDD terribly slow with ehci_hcd"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by pieroxy on 2007-01-20
Hi there,

I have a USB enclosure for a SATA drive that gives ms some issues on Edgy. The thing works almost as expected but for the terribly slow speed. I noticed that when I am copying from the USB hdd, (I have a led on the enclosure) the drive transmits data for a few seconds and then stops all activity for 25-30 seconds. By looking in dmesg, for every 'activity halt' I can see the line:

[17217739.600000] usb 3-4.4.1: reset high speed USB device using ehci_hcd and address 15
and sometimes :
[17222735.940000] usb 3-5: device descriptor read/64, error -71

When the drive 'works' (in between the resets) the speed is normal. But for 5 seconds of reading, there's 30 seconds of resetting !!! Of course, plugging the disk in a Windows box works just fine.

I tried a bunch of stuff:

1. Setting 8 or 16 in /sys/block/sdc/device/max_sectors. This somewhat reduces by 2x to 3x the speed (when actually transferring) but it also does reduce the amount of resetting so that it is about the same as the default - 240.
2. Plugging my HDD on another USB plug. It was originally directly connected to my box and I tried connecting it to various USB2 hubs. Results are worse (more resetting and more serious errors in dmesg)
3. Unloading the module ehci_hcd. The drive is then recognized as ohci_hcd (I suppose that's USB 1.1) and everything goes well (at least for the time I tried - I didn't try for hours) but things are naturally very slow as well.

So I didn't find a solution yet. Anyone has any ideas?

--pieroxy

Note: Here are the dmesg entries when I plug the drive:
[17218098.220000] usb 3-5: new high speed USB device using ehci_hcd and address 18
[17218098.352000] usb 3-5: configuration #1 chosen from 1 choice
[17218098.352000] scsi7 : SCSI emulation for USB Mass Storage devices
[17218098.352000] usb-storage: device found at 18
[17218098.352000] usb-storage: waiting for device to settle before scanning
[17218103.352000] usb-storage: device scan complete
[17218103.352000]   Vendor: Initio    Model: ST3400620AS       Rev: 1.14
[17218103.352000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17218103.356000] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[17218103.356000] sdc: Write Protect is off
[17218103.356000] sdc: Mode Sense: 00 00 00 00
[17218103.356000] sdc: assuming drive cache: write through
[17218103.356000] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[17218103.356000] sdc: Write Protect is off
[17218103.356000] sdc: Mode Sense: 00 00 00 00
[17218103.356000] sdc: assuming drive cache: write through
[17218103.356000]  sdc: sdc1
[17218103.364000] sd 7:0:0:0: Attached scsi disk sdc
[17218103.364000] sd 7:0:0:0: Attached scsi generic sg2 type 0

---

### Post by pieroxy on 2007-01-21
As it just turned out, the device will work well on some files, not well on others, and it will even disconnect when used too intensively.

From what I could tell, the device(sdc)  failed and got re-dected as sdd later on (at about 17228110.696000) and things didn't quite go very well from that point...

 Here is the latest-greatest dmesg:

[17228079.540000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17228079.540000] end_request: I/O error, dev sdc, sector 184072599
[17228109.652000] usb 3-5: reset high speed USB device using ehci_hcd and address 9
[17228109.896000] usb 3-5: reset high speed USB device using ehci_hcd and address 9
[17228110.008000] usb 3-5: device descriptor read/64, error -71
[17228110.224000] usb 3-5: device descriptor read/64, error -71
[17228110.440000] usb 3-5: reset high speed USB device using ehci_hcd and address 9
[17228110.572000] usb 3-5: device firmware changed
[17228110.572000] usb 3-5: USB disconnect, address 9
[17228110.572000] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
[17228110.572000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17228110.572000] end_request: I/O error, dev sdc, sector 184072607
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17228110.572000] end_request: I/O error, dev sdc, sector 184072679
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.572000] sd 2:0:0:0: rejecting I/O to offline device
[17228110.584000] sd 2:0:0:0: rejecting I/O to device being removed
[17228110.584000] journal_bmap: journal block not found at offset 24526 on sdc1
[17228110.584000] Aborting journal on device sdc1.
[17228110.584000] sd 2:0:0:0: rejecting I/O to device being removed
[17228110.584000] Buffer I/O error on device sdc1, logical block 1569
[17228110.584000] lost page write due to I/O error on sdc1
[17228110.584000] journal commit I/O error
[17228110.584000] sd 2:0:0:0: rejecting I/O to device being removed
[17228110.584000] Buffer I/O error on device sdc1, logical block 18415642
[17228110.584000] lost page write due to I/O error on sdc1
[17228110.696000] usb 3-5: new high speed USB device using ehci_hcd and address 10
[17228110.828000] usb 3-5: configuration #1 chosen from 1 choice
[17228110.828000] scsi3 : SCSI emulation for USB Mass Storage devices
[17228110.828000] usb-storage: device found at 10
[17228110.828000] usb-storage: waiting for device to settle before scanning
[17228112.500000] SMB connection re-established (-5)
[17228112.540000] SMB connection re-established (-5)
[17228112.564000] SMB connection re-established (-5)
[17228113.024000]  2:0:0:0: rejecting I/O to dead device
[17228113.024000] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[17228113.040000]  2:0:0:0: rejecting I/O to dead device
[17228113.040000] Buffer I/O error on device sdc1, logical block 0
[17228113.040000] lost page write due to I/O error on sdc1
[17228115.828000] usb-storage: device scan complete
[17228115.828000]   Vendor:           Model:                   Rev:     
[17228115.828000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17228115.832000] SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
[17228115.832000] sdd: Write Protect is off
[17228115.832000] sdd: Mode Sense: 00 00 00 00
[17228115.832000] sdd: assuming drive cache: write through
[17228115.832000] SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
[17228115.832000] sdd: Write Protect is off
[17228115.832000] sdd: Mode Sense: 00 00 00 00
[17228115.832000] sdd: assuming drive cache: write through
[17228115.832000]  sdd:<6>sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228115.852000] end_request: I/O error, dev sdd, sector 0
[17228115.852000] Buffer I/O error on device sdd, logical block 0
[17228115.856000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228115.856000] end_request: I/O error, dev sdd, sector 0
[17228115.856000] Buffer I/O error on device sdd, logical block 0
[17228115.856000]  unable to read partition table
[17228115.856000] sd 3:0:0:0: Attached scsi disk sdd
[17228115.856000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[17228116.188000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.188000] end_request: I/O error, dev sdd, sector 781422592
[17228116.188000] Buffer I/O error on device sdd, logical block 97677824
[17228116.192000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.192000] end_request: I/O error, dev sdd, sector 781422592
[17228116.192000] Buffer I/O error on device sdd, logical block 97677824
[17228116.196000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.196000] end_request: I/O error, dev sdd, sector 781422760
[17228116.196000] Buffer I/O error on device sdd, logical block 97677845
[17228116.200000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.200000] end_request: I/O error, dev sdd, sector 781422760
[17228116.200000] Buffer I/O error on device sdd, logical block 97677845
[17228116.204000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.204000] end_request: I/O error, dev sdd, sector 781422760
[17228116.204000] Buffer I/O error on device sdd, logical block 97677845
[17228116.212000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.212000] end_request: I/O error, dev sdd, sector 781422760
[17228116.212000] Buffer I/O error on device sdd, logical block 97677845
[17228116.232000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.232000] end_request: I/O error, dev sdd, sector 781422760
[17228116.236000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.236000] end_request: I/O error, dev sdd, sector 781422760
[17228116.240000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.240000] end_request: I/O error, dev sdd, sector 781422704
[17228116.244000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.244000] end_request: I/O error, dev sdd, sector 781422704
[17228116.248000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.248000] end_request: I/O error, dev sdd, sector 781422752
[17228116.252000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.252000] end_request: I/O error, dev sdd, sector 781422752
[17228116.264000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.264000] end_request: I/O error, dev sdd, sector 781422760
[17228116.280000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.280000] end_request: I/O error, dev sdd, sector 781422760
[17228116.344000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.344000] end_request: I/O error, dev sdd, sector 0
[17228116.388000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.388000] end_request: I/O error, dev sdd, sector 0
[17228116.396000] sd 3:0:0:0: SCSI error: return code = 0x10070000
[17228116.396000] end_request: I/O error, dev sdd, sector 0

---

### Post by allwin on 2007-01-21
I've been struggling with similar issues for some time now.  However, I discovered that sometimes the manufacturer of your enclosure will have firmware updates out on the web someplace.  This improved things for me a tad.  Also I find that if I plug in a known good USB device, and let it get recognized, and then put the HD in the same slot later, things work different...sometimes it will finally recognize the device or stop erroring out.  Also you can try booting with the thing plugged in.

Frankly, I think there be troubles in the USB department in Ubuntu.  Most of my posts on this subject went without answer for weeks on end now.  1394 devices also act flakey in similar ways, though I was at last able to get one HD to work at max speed by plugging in my DVD writer first, then reusing that socket with the HD enclosure (after updating the firmware in the enclosure).  Like you, with 3 different windows boxes, they all worked (for years incidentally) full speed and just fine.

---

### Post by pieroxy on 2007-01-22
Ok, now I am really annoyed. It is not - as I thought - a matter of my HDD enclosure. My USB card reader was working fine a month ago and is now showing the exact same symptoms, a bit worse actually. 

My USB 2 devices have become - for all intents and purposes - useless. I will look back at which package I installed in the last three weeks and will try to roll them back. Will keep you posted

---

### Post by pieroxy on 2007-01-24
I got that fixed by shutting down my computer and unplugging it (as well as all the USB devices) for a few minutes. That's what I call a HARD-HARD reset and has saved me in other situations. I didn't think it could be the problem...

So it was a hardware issue, not a software one.

---

