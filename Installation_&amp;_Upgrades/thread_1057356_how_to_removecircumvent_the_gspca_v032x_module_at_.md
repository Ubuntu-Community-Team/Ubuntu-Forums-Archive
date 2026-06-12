---
title: "how to remove/circumvent the gspca_v032x module at boot"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by sethedge on 2009-02-01
Hi guys,
I'm having some troubles installing a fresh ubuntu 8.10.
I'll tell you what the problem is: while installing, at the point "Loading hardware drivers..." the installation gets totally stuck!

After rebooting in recovery mode to see the kernel output, I realized that the system enters in a loop when trying to detect my integrated usb camera with the gspca_v032x module.

Here is the dmesg looped output:
> [  537.370514] vc032x: I2c Bus Busy Wait 0
[  537.370524] vc032x: I2c Bus Busy Wait 0
[  537.370531] vc032x: I2c Bus Busy Wait 0
[  537.370539] vc032x: I2c Bus Busy Wait 0
[  537.370547] vc032x: I2c Bus Busy Wait 0
[  537.370555] vc032x: I2c Bus Busy Wait 0
[  537.370559] vc032x: Unknown sensor...
[  537.370578] vc032x: probe of 5-4:1.0 failed with error -22
[  537.644142] usb 5-4: new high speed USB device using ehci_hcd and address 35
[  537.800407] usb 5-4: configuration #1 chosen from 1 choice
[  537.801173] gspca: probing 046d:0896
[  538.008549] vc032x: check sensor header 44
[  538.009311] usb 5-4: USB disconnect, address 35


I tried to deactivate the module by adding some boot options (F6), like:
> debian-installer/probe/usb=false
gspca-vc032x=0
acpi=noirq
but they didn't give any solution.

Any clue?

Thanks in advance.

p.s.: here is my system...
Acer Aspire 5630
Intel Core2 Duo T5500 1.66GHz
2GB DDR2

---

### Post by sethedge on 2009-02-02
up?

---

### Post by sethedge on 2009-02-03
maybe if i can deactivate the usb just for the installation?

does somebody know how to do it?

---

