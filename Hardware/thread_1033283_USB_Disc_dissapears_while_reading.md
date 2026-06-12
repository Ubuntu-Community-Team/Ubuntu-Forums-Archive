---
title: "USB Disc dissapears while reading"
date: 2009-01-07
forum: Hardware
---

### Post by cs6783 on 2009-01-07
Hi!

My 8.10 shows a really strange behavior: Today I wanted to read data from an USB device and connected it to the PC.. Everything seemed to work just fine. The device was detected and I could access it using Nautilus. Then I tried to copy some files.. The first file got copied correctly but then the device was unmounted and nothing worked (Input / Output Error)

My dmesg:

> [ 9006.400887] FAT: Directory bread(block 4881359) failed
[ 9006.400890] FAT: Directory bread(block 4881360) failed
[ 9006.400894] FAT: Directory bread(block 4881361) failed
[ 9006.400897] FAT: Directory bread(block 4881362) failed
[ 9006.400900] FAT: Directory bread(block 4881363) failed
[ 9006.400903] FAT: Directory bread(block 4881364) failed
[ 9006.400906] FAT: Directory bread(block 4881365) failed
[ 9006.400910] FAT: Directory bread(block 4881366) failed
[ 9006.400914] FAT: Directory bread(block 4881367) failed
[ 9006.400917] FAT: Directory bread(block 4881368) failed
[ 9006.400920] FAT: Directory bread(block 4881369) failed
[ 9006.400923] FAT: Directory bread(block 4881370) failed
[ 9006.400927] FAT: Directory bread(block 4881371) failed
[ 9021.427362] usb 5-1: device descriptor read/64, error -110
[ 9036.663273] usb 5-1: device descriptor read/64, error -110
[ 9036.883054] usb 5-1: new high speed USB device using ehci_hcd and address 9
[ 9052.019060] usb 5-1: device descriptor read/64, error -110
[ 9067.261126] usb 5-1: device descriptor read/64, error -110
[ 9067.474773] usb 5-1: new high speed USB device using ehci_hcd and address 10
[ 9077.903715] usb 5-1: device not accepting address 10, error -110
[ 9078.011622] usb 5-1: new high speed USB device using ehci_hcd and address 11
[ 9088.436597] usb 5-1: device not accepting address 11, error -110
[ 9174.042189] usb 5-1: new high speed USB device using ehci_hcd and address 12
[ 9189.174214] usb 5-1: device descriptor read/64, error -110
[ 9204.410140] usb 5-1: device descriptor read/64, error -110
[ 9204.625902] usb 5-1: new high speed USB device using ehci_hcd and address 13
[ 9219.753930] usb 5-1: device descriptor read/64, error -110
[ 9234.989848] usb 5-1: device descriptor read/64, error -110
[ 9235.213610] usb 5-1: new high speed USB device using ehci_hcd and address 14
[ 9245.636759] usb 5-1: device not accepting address 14, error -110
[ 9245.748416] usb 5-1: new high speed USB device using ehci_hcd and address 15
[ 9256.171264] usb 5-1: device not accepting address 15, error -110


Another thing: Several days ago while trying a similar thing I got this error message:

> 	DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

Has anyone got an idea how to fix this? 

Any help would really be appreciated!

---

### Post by tsoukase on 2009-06-21
I have the same problem but nobody even commented on a possible solution.

cs6783, your device probably is a mobile phone, as is mine (HTC), isn't it?

If the Linux Community had solved these trivial-in-Windows hardware problems, would it only achieve a decent market share.

Till then just copy your files one-by-one and whenever this happens just reinsert/remount the device.

---

