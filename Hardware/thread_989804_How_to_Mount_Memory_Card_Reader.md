---
title: "How to Mount Memory Card Reader?"
date: 2008-11-22
forum: Hardware
---

### Post by flem on 2008-11-22
I'm trying to switch an old desktop to Ubuntu from XP so that I can learn how to use Linux.  However, I have an xD card reader which will not mount and I need help mounting it.  Based on what I could find on the forums, here is some information that might be helpful:

I am running a fresh install of Ubuntu 8.10.

I have tried plugging it in to all of my USB ports with no luck (through a hub and directly to the computer).  I have successfully automounted a mass storage drive in Ubuntu, but not the card reader.

Specifically, it is a Fujifilm Memory Card Reader DPC-R1 (xD/SmartMedia combo) and is the same as the Olympus MAUSB-10.  The card reader does work, there is a 16 MB card in it, and it has pictures on it.  It is supported in Ubuntu by the "alauda" driver.

"lsusb" shows that the device is found, and it knows what it is:
```

Bus 001 Device 003: ID 0584:0008 RATOC System, Inc. Fujifilm MemoryCard ReaderWriter

```

The device does not appear when running "fdisk -l"

"tail -f /var/log/messages" gives following:

```

Nov 21 23:23:45 office kernel: [  198.190076] usb 1-1.2: new full speed USB device using uhci_hcd and address 3
Nov 21 23:23:45 office kernel: [  198.334374] usb 1-1.2: configuration #1 chosen from 1 choice
Nov 21 23:23:45 office kernel: [  198.729487] alauda: alauda probed
Nov 21 23:23:45 office kernel: [  198.735169] usbcore: registered new interface driver alauda
Nov 21 23:23:46 office kernel: [  198.806242] usbcore: registered new interface driver libusual

```

If anyone can help, I would greatly appreciate it.

---

### Post by NM5TF on 2008-12-01
did you ever get your card reader to work???  I'm having the exact same problem with an Olympus MAUSB-10 reader.....the system sees it, but won't open any files.....

---

### Post by flem on 2008-12-02
I haven't had any success or received any help yet.  I can load the pictures straight from the camera, but that isn't ideal since it kills the batteries pretty quickly.

---

### Post by acreech on 2008-12-03
I have an internal card reader that says it supports both SD and xD. I can not get the xD to work, however the SD works out of the box. I have another card reader that attaches via USB and the xD works fine in it. 

I have read some other threads that suggest that xD is not supported by Ubuntu. 

Is this true? Is there away around this problem so that the internal card reader will read a xD?

thanks for the help.

---

### Post by acreech on 2008-12-03
There is a bug report on this at 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490")

---

