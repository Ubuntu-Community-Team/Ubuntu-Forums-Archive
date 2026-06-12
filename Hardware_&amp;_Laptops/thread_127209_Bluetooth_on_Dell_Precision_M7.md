---
title: "Bluetooth on Dell Precision M7"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by swinchen on 2006-02-08
Hello all.

A friend of mine has a Dell Precision M70 w/ built in bluetooth capability.  

Note:  hci0 is the bluetooth module built into his laptop.  hci1 is a usb bluetooth module that we connected for testing.
```

root@monroe:/# hcitool dev
Devices:
        hci0    00:10:C6:9C:FC:D6
        hci1    00:0A:3A:59:35:BA
root@monroe:/#

```

So first we tried scanning with the Belkin USB bluetooth dongle:
```

root@monroe:/# hcitool -i hci1 scan
Scanning ...
        00:0C:84:00:0D:28       eb500
root@monroe:/#

```

excellent, it found the bluetooth device we are trying to connect to.   Now we tried it with the built in functionality of the laptop:
```

root@monroe:/# hcitool -i hci0 scan
Scanning ...
root@monroe:/#

```

Bummer, no bluetooth devices found.  Interestingly enough the bluetooth light on his computer lights up during the scan, so at the very least there is some communication happening.

If anyone has any ideas or needs more information please let me know!  thanks.

Here is the output of lsusb if that is any help:

```

root@monroe:/# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 050d:0081 Belkin Components
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
root@monroe:/#

```

---

