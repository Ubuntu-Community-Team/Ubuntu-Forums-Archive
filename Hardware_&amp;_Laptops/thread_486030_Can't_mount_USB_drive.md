---
title: "Can't mount USB drive"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2007-06-27
I have trouble mounting a 2.5" USB drive on Ubuntu 7.04.

dmesg shows this:

```

[   70.600000] scsi3 : SCSI emulation for USB Mass Storage devices
[   70.632000] usb-storage: device found at 3
[   70.632000] usb-storage: waiting for device to settle before scanning
[   75.632000] usb-storage: device scan complete
[   75.640000] scsi 3:0:0:0: Direct-Access     IBM-DJSA -220             0811 PQ: 0 ANSI: 0
[   75.640000] SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
[   75.644000] sdb: test WP failed, assume Write Enabled
[   75.644000] sdb: assuming drive cache: write through
[   75.644000] SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
[   75.644000] sdb: test WP failed, assume Write Enabled
[   75.644000] sdb: assuming drive cache: write through
[   75.644000]  sdb:<6>usb 1-1: new low speed USB device using uhci_hcd and address 2

```

Is the drive broken?

---

### Post by Jaxilian on 2007-06-27
I get this from lsusb with having the USb drive in and a mouse

```

~$ lsusb
Bus 005 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000 

```

---

### Post by Jaxilian on 2007-06-27
I get this when doin a scsi_info

```

~$ scsi_info /dev/sdb
SCSI_ID="0,0,0"
HOST="2"
MODEL="IBM-DJSA -220"
FW_REV="0811"

```

Might be broken: got this from dmesg when I replugged it.

```

[  834.744000] end_request: I/O error, dev sdb, sector 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] ldm_validate_partition_table(): Disk read failed.
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Dev sdb: unable to read RDB block 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000] Buffer I/O error on device sdb, logical block 3
[  834.744000] Buffer I/O error on device sdb, logical block 3
[  834.744000] Buffer I/O error on device sdb, logical block 0
[  834.744000]  unknown partition table
[  834.744000] sd 2:0:0:0: Attached scsi disk sdb
[  834.744000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1268.000000] printk: 40 messages suppressed.
[ 1268.000000] Buffer I/O error on device sdb, logical block 0
[ 1268.000000] Buffer I/O error on device sdb, logical block 0
[ 1268.000000] Buffer I/O error on device sdb, logical block 0
[ 1268.000000] Buffer I/O error on device sdb, logical block 1
[ 1268.000000] Buffer I/O error on device sdb, logical block 2
[ 1268.000000] Buffer I/O error on device sdb, logical block 3
[ 1268.000000] Buffer I/O error on device sdb, logical block 0
[ 1551.184000] ehci_hcd 0000:00:1d.7: remove, state 1
[ 1551.184000] usb usb5: USB disconnect, address 1
[ 1658.132000] Buffer I/O error on device sdb, logical block 0
[ 1658.132000] Buffer I/O error on device sdb, logical block 0
[ 1658.132000] Buffer I/O error on device sdb, logical block 0
[ 1658.132000] Buffer I/O error on device sdb, logical block 1
[ 1658.132000] Buffer I/O error on device sdb, logical block 2
[ 1658.132000] Buffer I/O error on device sdb, logical block 3
[ 1658.132000] Buffer I/O error on device sdb, logical block 0

```

It worked before on windows, but now that I tried it on ubuntu, it doesn't show up there either.

---

### Post by Jaxilian on 2007-06-28
Any knows what this is?
Is the drive wasted now or can I save it with some tricky linux hack command? :popcorn:

---

### Post by elsaturnino on 2007-06-29
Have you confirmed that the drive works on another machine (or possibly in windows)?

---

### Post by Jaxilian on 2007-06-30
> **elsaturnino said:**
> Have you confirmed that the drive works on another machine (or possibly in windows)?

yes

---

### Post by senken12 on 2007-06-30
I had the same problem with my USB mouse when I installed Edgy.
I just searched google trying to find solution and found out that the problem was the grub forgetting about the USB on startup

Shamefully - This was the beginning of the year thus can't remember the URL or how to do it :(

---

