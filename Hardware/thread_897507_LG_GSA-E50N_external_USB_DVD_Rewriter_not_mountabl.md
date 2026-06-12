---
title: "LG GSA-E50N external USB DVD Rewriter not mountable in Heron"
date: 2008-08-22
forum: Hardware
---

### Post by Greg K on 2008-08-22
I've just received this drive. Having ordered it because my Superdrive is a victim of [Apple's 2.1 fireware update]("http://forums.macosxhints.com/showthread.php?t=75081") and no longer reliably reads many discs.

This external DVD rewriter requires one USB cable to transfer the data and a second to power the unit. I've verified I have power to it but I can't seem to mount this device. I've read reports it [works on eeebutu]("http://forum.eeeuser.com/viewtopic.php?id=2127") with the Asus EEE PC.

This drive doesn't show up in lsusb when connected to my Macbook Pro (15.4")
```
$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:8205 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00e3 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 005 Device 003: ID 05ac:021b Apple Computer, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05ac:8502 Apple Computer, Inc.

```

The Microsoft device is my USB keyboard. I'm not sure what the Apple devices are though.

Any help appreciated.

---

### Post by Greg K on 2008-08-26
No one else encountered any issues mounting this drive?

---

### Post by Greg K on 2008-08-26
OK. So I plugged my drive in this evening, USB data cable only, with a disc already in the drive before I connected it and it span up and mounted automatically!

Weirdest thing ever, guess this thread can be closed now :)

---

