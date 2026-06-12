---
title: "thinkpad w500 ubuntu and fingerprint reader?"
date: 2008-12-07
forum: Hardware
---

### Post by Bashar &quot; on 2008-12-07
anyone knows if it works with ubuntu 8.10 ?

i dont see it in lsusb output list:
root@bashar-laptop:/etc/apt# lsusb
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 0bdb:1900 Ericsson Business Mobile Networks BV 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 17ef:4807 Lenovo 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0a5c:2145 Broadcom Corp. 
Bus 002 Device 004: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@bashar-laptop:/etc/apt#

---

### Post by antmo on 2008-12-08
the new thinkpads use a different vendor for their fingerprint reader...  the device is in your list, it is the:

Bus 002 Device 004: ID 08ff:2810 AuthenTec, Inc.

this is different from the older vendor, i believe it was upek.

mjb

---

### Post by Bashar &quot; on 2008-12-08
when i reached the acquire step i got this:
bashar@bashar-laptop:~$ sudo tf-tool --acquire

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.
bashar@bashar-laptop:~$ 


thats why i thought AuthenTec is not the device.

any idea how can i make thinkfinger identify the device? 

i'm following steps at [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

thanks

---

### Post by Bashar &quot; on 2008-12-08
thinkfinger does not support AuthenTec unfortunately

googling starts...

---

### Post by antmo on 2008-12-08
unfortunately, neither thinkfinger nor fprint support the w500 fingerprint reader right now...  they are working on it though...  you can see the latest at the wiki: [http://reactivated.net/fprint/wiki/Unsupported_devices]("http://reactivated.net/fprint/wiki/Unsupported_devices")

scroll about half way down to the "AuthenTec AES2550 & AES2810" section.  the w500 has the aes2810.

mjb

---

### Post by deepclutch on 2009-03-04
Is there any update regarding the support?any patches available?

---

