---
title: "USB SD Card Reader"
date: 2008-07-10
forum: Hardware
---

### Post by mattwho on 2008-07-10
Can't get my card reader to work.
```
matt@desktop:~$ lsusb
Bus 004 Device 058: ID 058f:6335 Alcor Micro Corp. 
Bus 004 Device 002: ID 0d49:3200 Maxtor 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

It's the Alcor device

```
matt@desktop:~$ dmesg | tail
[161644.869308] usb 4-4: reset high speed USB device using ehci_hcd and address 60
[161645.212597] usb 4-4: reset high speed USB device using ehci_hcd and address 60
[161645.555888] usb 4-4: reset high speed USB device using ehci_hcd and address 60
[161645.899171] usb 4-4: reset high speed USB device using ehci_hcd and address 60
[161646.035298] sd 56:0:0:0: [sdd] Write Protect is off
[161646.035309] sd 56:0:0:0: [sdd] Mode Sense: 00 00 00 00
[161646.035313] sd 56:0:0:0: [sdd] Assuming drive cache: write through
[161646.035477] sd 56:0:0:0: [sdd] Attached SCSI removable disk
[161646.035562] sd 56:0:0:0: Attached scsi generic sg5 type 0
[161646.334958] usb 4-4: reset high speed USB device using ehci_hcd and address 60

```

From google all I can find is that it might not be getting enough power?
I'm using Hardy Heron

---

### Post by avmian on 2008-07-28
I had the same problem with a SanDisk card reader
I resolved it using these command:

```

sudo mkdir /media/card
sudo mount -t vfat /dev/sdb1 /media/card

```

But I think it's a hardy bug. Maybe somebody could open it in launchpad ?

Other information, with the partition editor I see that the system want to mount by default the car in media/cdrom0 !

---

