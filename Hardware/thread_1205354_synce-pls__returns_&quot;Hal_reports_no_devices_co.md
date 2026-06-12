---
title: "synce-pls  returns &quot;Hal reports no devices connected&quot;??"
date: 2009-07-05
forum: Hardware
---

### Post by sderrick on 2009-07-05
I followed the installation instructions at the Synce wiki for Ubuntu.
[http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu)

Using Ubuntu Jaunty 9.04 
Kernel 2.6.29
Phone is MotoQ, OS  WindowsMmobile 6

Phone has enhanced networking for usb connection set and USB is the active connection.

Blacklisted ipaq.

running synce-pls returns

scott@scotts-laptop:~$ synce-pls
** Message: Hal reports no devices connected

** (process:8801): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'

dmesg after pluggin in phone

[ 3753.888133] usb 6-1: new full speed USB device using uhci_hcd and address 8
[ 3754.066908] usb 6-1: configuration #1 chosen from 1 choice
[ 3754.068199] usb 6-1: bad CDC descriptors
[ 3754.074591] usb 6-1: bad CDC descriptors

lsusb reports the phone

Bus 006 Device 008: ID 22b8:7003 Motorola PCS 

What am I missing??

Scott

---

