---
title: "USB ports not working"
date: 2013-08-17
forum: Hardware
---

### Post by kiwipenguin on 2013-08-17
Hello.

Recently my USB ports all stopped working for no apparent reason.
When I plug in a USB device, it gets power but the laptop doesn't see it.
I have searched the forums for answers but haven't found anything beyond typing lsusb into Terminal... Then what do I do?

One person said it came right after resetting the BIOS but I have no idea what that does and other posts recommended against doing it without good reason.

Here is my lsusb output:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Please help. I'm using 11.10
Thanks

---

### Post by VMC on 2013-08-17
When did it stop working? After an upgrade?

Output the following command:
```
uname -r
```

---

### Post by kiwipenguin on 2013-08-24
Output is:

3.0.0-32-generic

I haven't up graded my version of Ubuntu for a while so that wasn't the cause, although there are sometimes Ubuntu updates and downloads going on that might have had something to do with it.

---

