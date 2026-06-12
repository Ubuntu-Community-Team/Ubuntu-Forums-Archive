---
title: "External USB Hard Drive - resets / errors"
date: 2011-01-26
forum: Hardware
---

### Post by LeoCurrie on 2011-01-26
Hi -

I have a USB hard disc that seems to work pretty normally most of the time.
It is a 1TB hitachi drive, badged by Lacie, formatted for ext3

The problem is happens when I start browsing through photos.
I will be browsing through a folder, and randomly I will be given an error like 
'Error stating file '/media/a6a6662d-6345-4f1f-91cc-b844ce573f35_/Photos/things/CIMG0254.JPG': No such file or directory'

Looking in the messages I can see the following, starting at 00:40 when I plug the drive in:
```
Jan 27 00:40:44 binnie kernel: [145752.590720] scsi 16:0:0:0: Direct-Access     Hitachi  HDT721010SLA360       PQ: 0 ANSI: 2 CCS
Jan 27 00:40:44 binnie kernel: [145752.592004] sd 16:0:0:0: Attached scsi generic sg4 type 0
Jan 27 00:40:44 binnie kernel: [145752.594723] sd 16:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jan 27 00:40:44 binnie kernel: [145752.595437] sd 16:0:0:0: [sdd] Write Protect is off
Jan 27 00:40:44 binnie kernel: [145752.596621]  sdd: sdd1
Jan 27 00:40:44 binnie kernel: [145752.616403] sd 16:0:0:0: [sdd] Attached SCSI disk
Jan 27 00:40:45 binnie kernel: [145754.314192] kjournald starting.  Commit interval 5 seconds
Jan 27 00:40:45 binnie kernel: [145754.315498] EXT3 FS on sdd1, internal journal
Jan 27 00:40:45 binnie kernel: [145754.315506] EXT3-fs: mounted filesystem with ordered data mode.
Jan 27 00:46:40 binnie kernel: [146108.274391] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:46:51 binnie kernel: [146118.491728] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:46:56 binnie kernel: [146123.722807] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:47:11 binnie kernel: [146139.325389] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:47:32 binnie kernel: [146159.816567] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:47:42 binnie kernel: [146170.308619] usb 1-1: reset high speed USB device using ehci_hcd and address 14
Jan 27 00:47:48 binnie kernel: [146175.703311] sd 16:0:0:0: Device offlined - not ready after error recovery
Jan 27 00:47:48 binnie kernel: [146175.703323] sd 16:0:0:0: [sdd] Unhandled error code
Jan 27 00:47:48 binnie kernel: [146175.703325] sd 16:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 27 00:47:48 binnie kernel: [146175.703328] sd 16:0:0:0: [sdd] CDB: Read(10): 28 00 0d 3d 46 a7 00 00 f0 00
Jan 27 00:47:48 binnie kernel: [146175.703359] usb 1-1: USB disconnect, address 14
Jan 27 00:47:48 binnie kernel: [146175.703373] sd 16:0:0:0: [sdd] Unhandled error code
Jan 27 00:47:48 binnie kernel: [146175.703374] sd 16:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 27 00:47:48 binnie kernel: [146175.703376] sd 16:0:0:0: [sdd] CDB: Read(10): 28 00 0d 3d 47 97 00 00 10 00
Jan 27 00:47:48 binnie kernel: [146175.850736] usb 1-1: new high speed USB device using ehci_hcd and address 15
Jan 27 00:48:09 binnie kernel: [146196.436808] usb 1-1: new high speed USB device using ehci_hcd and address 16
Jan 27 00:48:24 binnie kernel: [146212.035946] usb 1-1: new high speed USB device using ehci_hcd and address 17
Jan 27 00:48:35 binnie kernel: [146222.528545] usb 1-1: new high speed USB device using ehci_hcd and address 18
Jan 27 00:48:40 binnie kernel: [146228.193780] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jan 27 00:48:41 binnie kernel: [146228.752365] usb 3-1: new full speed USB device using uhci_hcd and address 3
Jan 27 00:48:42 binnie kernel: [146229.311546] usb 3-1: new full speed USB device using uhci_hcd and address 4
Jan 27 00:48:42 binnie kernel: [146229.830191] usb 3-1: new full speed USB device using uhci_hcd and address 5

```As you can see, there was some kind of problem at 00:46.
The drive vanished from the desktop, and the little blue light is flashing constantly.

What does this mean? Is this a disc read error, or a problem with the USB hub?

I don't think it's a disc read error because I can disconnect the drive, reconnect it and successfully load the image that apparently failed.
Where do I go from here?

Thanks -

Leo

---

