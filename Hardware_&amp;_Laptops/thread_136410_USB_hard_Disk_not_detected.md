---
title: "USB hard Disk not detected"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by Mohd Hafiz on 2006-02-25
Hi,
my hard disk wont detect at all,
when i run dmesg, here is the output:
#dmesg
 usb 4-1: new high speed USB device using ehci_hcd and address 12
[17182120.076000] usb 4-1: can't set config #1, error -110
[17182120.188000] usb 4-1: new high speed USB device using ehci_hcd and address 13
[17182120.708000] usb 4-1: device not accepting address 13, error -71
[17182120.820000] usb 4-1: new high speed USB device using ehci_hcd and address 14
[17182120.840000] usb 4-1: device descriptor read/all, error 8
[17182120.956000] usb 4-1: new high speed USB device using ehci_hcd and address 15
[17182121.364000] usb 4-1: device not accepting address 15, error -71

i run fdisk -l
the external hard disk not appear,
theris no /dev/sda or sdb or any, only my /dev/hda

But i'm sure my hard disk is ok, beause i can mount it using winXp(dual boot).

one more think, my kernel configuration is ok because i can read another usb hardisk(small size(laptop)). the problem one is the big size(hard disk for desktop size which I put in casing power with extra power supply)

---

### Post by pestilence4hr on 2006-02-25
How about trying:

```
sudo modprobe scsi_mod
sudo modprobe usb_storage
```

Then look for a /dev/sda* device.

---

### Post by cperdana on 2006-02-26
it didnot work,
i compile that in my kernel, not as module

---

