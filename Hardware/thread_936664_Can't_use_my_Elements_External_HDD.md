---
title: "Can't use my Elements External HDD?"
date: 2008-10-03
forum: Hardware
---

### Post by knivessout on 2008-10-03
Hello everyone!

I am new to ubuntu and I am having trouble using my external hard drive.  My computer is a Dell Inspiron 6000 laptop running Ubuntu 8.04 Hardy. Intel Pentium M processor 1.60 GHz; 512 MB ram. My external HDD is a Western Digital "Elements" USB 2.0, 250 GB.

I have tried plugging it in before boot, and after boot and no luck. Nothing happens. When I type "lsusb" into terminal, it is recognized as "Western Digital Technologies, Inc." When I type "dmesg", the last lines containing info about my drive are as follows:

```
[   42.010952] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[   84.137370] scsi 2:0:0:0: Device offlined - not ready after error recovery
[   45.024413] NET: Registered protocol family 17
[   90.391493] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   98.290535] eth1: no IPv6 routers present
[  102.200840] usb 5-5: USB disconnect, address 2
[  106.036723] usb 5-8: new high speed USB device using ehci_hcd and address 3
[  106.100512] usb 5-8: configuration #1 chosen from 1 choice
[  106.143749] scsi3 : SCSI emulation for USB Mass Storage devices
[  106.150677] usb-storage: device found at 3
[  106.150684] usb-storage: waiting for device to settle before scanning
[  106.427211] usb-storage: device scan complete
[  110.335757] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  112.430959] usb 5-8: device descriptor read/64, error -71
[  117.466223] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[   62.839181] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  125.915405] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  132.438117] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[   66.234895] scsi 3:0:0:0: Device offlined - not ready after error recovery
[  127.448778] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[  395.069296] usb 5-8: USB disconnect, address 3
[  395.482455] usb 5-5: new high speed USB device using ehci_hcd and address 4
[  395.550660] usb 5-5: configuration #1 chosen from 1 choice
[  395.558645] scsi4 : SCSI emulation for USB Mass Storage devices
[  395.562190] usb-storage: device found at 4
[  395.562197] usb-storage: waiting for device to settle before scanning
[  396.047464] usb-storage: device scan complete
[  398.048513] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[  399.917991] usb 5-5: device descriptor read/64, error -71
[  403.567543] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[  409.465814] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[  409.527273] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[  413.772005] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[  413.805905] scsi 4:0:0:0: Device offlined - not ready after error recovery

```

any suggestions? my gut instinct is that this drive is simply not compatible with Ubuntu but I will note that I have used Knoppix quite a few times and it worked in there. This drive was originally formatted in Windows XP.

p.s. this is the result for lsusb:

```
Bus 005 Device 004: ID 1058:1000 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by knivessout on 2008-10-03
Ok so I was fooling around for a while. Got something to eat, and when I came back and tried unplugging and plugging my external back into the USB port, it just worked!

I just plugged it in first then powered up the drive. Maybe powering up the drive before plugging it in messes something up? Or I could have experienced just a weird glitch. Anyway, I'm all good now. :D

---

### Post by hiltontian on 2008-10-03
Generally, external HDD is easy to use.

---

### Post by Gonzalo_VC on 2008-10-05
[COLOR="Navy"]Well, I got a WD MyPassport Essential = 160 GB external USB hard-drive, but can't access it neither in Ubuntu/Poseidon nor in winXP... I should get some drivers for the second one, but what about Linux? Any clues?
Maybe one problem is that my "old" machine as only slow USB connections...[/COLOR]:confused:

---

