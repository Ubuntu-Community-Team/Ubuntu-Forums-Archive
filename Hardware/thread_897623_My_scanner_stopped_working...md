---
title: "My scanner stopped working.."
date: 2008-08-22
forum: Hardware
---

### Post by ubun_two on 2008-08-22
I have a Memorex scanner.  This worked just fine on both Hardy 32bit and 64bit.  Now I primarily use 64bit.

I can't remember the last time I did the scan, but I know it used to work just fine.  But when I tried it today, it simply didn't work.  As far as I remember, only things I've been doing to the system are installation through Synaptec and regular updating.

After some investigation, it looks like there is an error while trying to connect the scanner to USB.  Below is the result of lsusb and what appears on kern.log when I issue lsusb command.

> Bus 008 Device 005: ID 046d:c041 Logitech, Inc. 
Bus 008 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 008 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 005: ID 03f0:7504 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

> Aug 22 11:11:36 xxxx kernel: [11502.835720] usb 2-2: new full speed USB device using uhci_hcd and address 18
Aug 22 11:11:36 xxxx kernel: [11502.959624] usb 2-2: device descriptor read/64, error -71
Aug 22 11:11:36 xxxx kernel: [11503.187447] usb 2-2: device descriptor read/64, error -71
Aug 22 11:11:37 xxxx kernel: [11503.404852] usb 2-2: new full speed USB device using uhci_hcd and address 19
Aug 22 11:11:37 xxxx kernel: [11503.527184] usb 2-2: device descriptor read/64, error -71
Aug 22 11:11:37 xxxx kernel: [11503.755008] usb 2-2: device descriptor read/64, error -71
Aug 22 11:11:37 xxxx kernel: [11503.974863] usb 2-2: new full speed USB device using uhci_hcd and address 20
Aug 22 11:11:38 xxxx kernel: [11504.383520] usb 2-2: device not accepting address 20, error -71
Aug 22 11:11:38 xxxx kernel: [11504.494435] usb 2-2: new full speed USB device using uhci_hcd and address 21
Aug 22 11:11:38 xxxx kernel: [11504.902119] usb 2-2: device not accepting address 21, error -71

Also, here is my output for uname -a
> 
Linux xxxxxx 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

Anyone has any thought?  Thanks.

---

### Post by ubun_two on 2008-11-08
Just as an update, It seems it started working again on Intrepid 64bit.  Furthermore, my eeePC with Hardy 32bit never had any problem.

---

