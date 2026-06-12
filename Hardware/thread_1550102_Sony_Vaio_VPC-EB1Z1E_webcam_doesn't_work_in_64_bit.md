---
title: "Sony Vaio VPC-EB1Z1E webcam doesn't work in 64 bit 10.04"
date: 2010-08-10
forum: Hardware
---

### Post by parttis on 2010-08-10
I am running the 64 bit version of Lucid Lynx 10.04 Ubuntu on my Sony Vaio VPC-EB1Z1E laptop. I am unable to use the integrated webcam because it doesn't enumerate properly.

When Linux is running the /var/log/kern.log file fills up with following text (where the value of address goes from 3 to 127):
kernel: [ 5673.457912] hub 1-1:1.0: unable to enumerate USB device on port 2
kernel: [ 5673.697241] usb 1-1.2: new high speed USB device using ehci_hcd and address 110

From Windows 7 I was able to use USB view program to see that on the first Generic USB Hub there is an USB device on Loc112 with following idVendor and idProduct values: 0C45:6409. IdVendor 0C45 means that the webcam is manufactured by Microdia. [Microdia Webcam support group]("http://groups.google.com/group/microdia") has no record of idProduct 6409.

But on the Linux side it doesn't show webcam at all:
$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any suggestions?

---

### Post by aircooledbusnut on 2010-08-30
Same problem on Sony Vaio VPC-EA24FM

Update:  Issue solved by removing all power and battery for thirty minutes.

Webcam now works, but no sound through speakers yet (different issue)

---

### Post by parttis on 2010-09-18
> **aircooledbusnut said:**
> Same problem on Sony Vaio VPC-EA24FM

Update:  Issue solved by removing all power and battery for thirty minutes.

Webcam now works, but no sound through speakers yet (different issue)



I fixed similar audio issue on my laptop with [these instructions]("http://translate.google.com/translate?hl=en&sl=it&tl=en&u=http%3A%2F%2Fit.bongolinux.com%2Fsony-vaio-e-ubuntu-lucid%2F124802%2F").

---

