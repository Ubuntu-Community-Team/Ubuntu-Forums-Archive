---
title: "Genesys Logic, Inc. GL3310 SATA 3Gb/s Bridge Controller (05e3:0731) no USB 3.0"
date: 2018-11-13
forum: Hardware
---

### Post by elmarciano18 on 2018-11-13
Hello!

My notebook is running Xubuntu 18.04.
I got this USB3.0-SATA Adapter: Genesys Logic, Inc. GL3310 SATA 3Gb/s Bridge Controller 05e3:0731
**When I plug it into an USB 2.0 port** on my Notebook (hp 8770w with Mobile Intel QM77 Express chipset)
dmesg is showing:
> [409287.955795] usb 1-1.6: new high-speed USB device number 4 using ehci-pci
[409288.158518] usb 1-1.6: New USB device found, idVendor=05e3, idProduct=0731
[409288.158521] usb 1-1.6: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[409288.158522] usb 1-1.6: Product: USB to S-ATA
[409288.158524] usb 1-1.6: Manufacturer: Genesyslogic
[409288.158525] usb 1-1.6: SerialNumber: 0000000000026120
[409288.159187] usb-storage 1-1.6:1.0: USB Mass Storage device detected
[409288.159379] scsi host7: usb-storage 1-1.6:1.0
[409289.161056] scsi 7:0:0:0: Direct-Access     TS32GSSD 25S-M            1203 PQ: 0 ANSI: 0
[409289.161412] sd 7:0:0:0: Attached scsi generic sg2 type 0
[409289.162661] sd 7:0:0:0: [sdb] 62533292 512-byte logical blocks: (32.0 GB/29.8 GiB)
[409289.163636] sd 7:0:0:0: [sdb] Write Protect is off
[409289.163637] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[409289.164637] sd 7:0:0:0: [sdb] No Caching mode page found
[409289.164640] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[409289.169070]  sdb: sdb1 sdb2 sdb3
[409289.1**In general the USB3.0 port is working with other USB3.0 devices (at superspeed).**72293] sd 7:0:0:0: [sdb] Attached SCSI disk
[409294.930987] EXT4-fs (sdb1): mounting ext2 file system using the ext4 subsystem
[409294.934627] EXT4-fs (sdb1): warning: mounting unchecked fs, running e2fsck is recommended
[409294.936864] EXT4-fs (sdb1): mounted filesystem without journal. Opts: (null)
[409304.933080] EXT4-fs (sdb3): warning: mounting unchecked fs, running e2fsck is recommended
[409304.937101] EXT4-fs (sdb3): mounted filesystem without journal. Opts: (null)

and **everything is working fine.**

But **when I plug it into an USB3.0 port it does not work**. dmesg says:
> [409249.874168] usb 4-4: new SuperSpeed USB device number 5 using xhci_hcd
[409249.894074] usb 4-4: New USB device found, idVendor=05e3, idProduct=0731
[409249.894078] usb 4-4: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[409249.894082] usb 4-4: Product: USB to S-ATA
[409249.894084] usb 4-4: Manufacturer: Genesyslogic
[409249.894087] usb 4-4: SerialNumber: 0000000000026120
[409249.895288] usb-storage 4-4:1.0: USB Mass Storage device detected
[409249.895425] scsi host7: usb-storage 4-4:1.0
..
and nothing more.
In general the USB3.0 port is working with other USB3.0 devices (at superspeed).
**It does not detect the SATA drive connected to the adapter and there's no corresponding device in /dev**
[B]In general the USB3.0 port is working with other USB3.0 devices (at superspeed).
When I then unplug the Adapter from the USB3.0 port dmesg says:
[/B]> [409285.119902] xhci_hcd 0000:00:14.0: Cannot set link state.
[409285.119908] usb usb4-port4: cannot disable (err = -32)
**This error does not come up after disconnecting the adapter from an USB2.0 port! So I think it is related to the problem.**


I found that I probably need to activate a quirk related to this controller and I found on there:
[https://github.com/torvalds/linux/blob/master/drivers/usb/storage/unusual_devs.h](https://github.com/torvalds/linux/blob/master/drivers/usb/storage/unusual_devs.h)
But how do I load the "usb_storage" module with this quirk (USB - SATA):
> [TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]/* Reported by Ben Efros <ben@pc-doctor.com> */[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]UNUSUAL_DEV(  0x05e3, 0x0723, 0x9451, 0x9451,[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]        "Genesys Logic",[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]        "USB to SATA",[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]        USB_SC_DEVICE, USB_PR_DEVICE, NULL,[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
        US_FL_SANE_SENSE ),

My device is usually shown as product it: 0731

Thank you for help!

---

### Post by elmarciano18 on 2018-11-13
OK; I could make it work manually by unloading the usb-storage driver and loading it like this:
> modprobe -v usb-storage "quirks=0x05e3:0x0731:u"


But how do I make it work automatically, everytime I reboot or replug the adapter?
I already tried creating the file /etc/modprobe.d/usb-storage.conf with the content:
> options usb-storage "quirks=0x05e3:0x0731:u"
but this does not work :(

---

