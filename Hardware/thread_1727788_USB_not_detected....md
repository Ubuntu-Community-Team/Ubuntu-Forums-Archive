---
title: "USB not detected..."
date: 2011-04-12
forum: Hardware
---

### Post by ccookie66 on 2011-04-12
Hello, I just installed Ubuntu 10.04 on my IBM ThinkPad, and when I plug a USB drive into the laptop, nothing happens. ? How can I fix this?? Thanks.

---

### Post by mikewhatever on 2011-04-13
Can you post the output of **dmesg | tail**. What file system is there on the usb drive?

---

### Post by ccookie66 on 2011-04-13
> **mikewhatever said:**
> Can you post the output of **dmesg | tail**. What file system is there on the usb drive?

Wow, this doesn't look good...

[  277.716395] hub 1-0:1.0: unable to enumerate USB device on port 4
[  277.960107] usb 1-4: new high speed USB device using ehci_hcd and address 22
[  278.028405] hub 1-0:1.0: unable to enumerate USB device on port 4
[  278.216435] hub 1-0:1.0: unable to enumerate USB device on port 4
[  278.404439] hub 1-0:1.0: unable to enumerate USB device on port 4
[  278.592441] hub 1-0:1.0: unable to enumerate USB device on port 4
[  278.780434] hub 1-0:1.0: unable to enumerate USB device on port 4
[  278.968435] hub 1-0:1.0: unable to enumerate USB device on port 4
[  279.212167] usb 1-4: new high speed USB device using ehci_hcd and address 28
[  279.280315] hub 1-0:1.0: unable to enumerate USB device on port 4

I think it formated as FAT32.

---

### Post by mikewhatever on 2011-04-13
There is a bug report about this issue, and post #74 suggests a solution.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767)

... and here is another:
[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

---

### Post by ccookie66 on 2011-04-13
> **mikewhatever said:**
> There is a bug report about this issue, and post #74 suggests a solution.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767)

... and here is another:
[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

Thanks it worked! :)  Problem solved!

---

