---
title: "Sony Micro Vault: update [Please Help Me]"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by PaRRoT.it on 2005-04-22
I've a Sony Micro Vault 256MB and 2 PCs.

PC1: Athlon XP 2600+, M/B with Via KT400, ... kernel 2.6.10 for k7
PC2: Celeron 300A, M/B with Intel i440LX,... kernel 2.6.10 for i686

All PCs have Ubuntu Hoary 5.04.
If I use Sony Micro Vault 256MB in PC1 I've in syslog this error:
```
Apr 21 10:07:21 papousek kernel: usb 4-1: new high speed USB device using ehci_hcd and address 3
Apr 21 10:07:22 papousek kernel: usb 4-1: device descriptor read/all, error -71

```
...and "lsusb" doesn't find my pendrive.
```

root@papousek:~ # lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c506 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

If I use SMV256 in PC2 all works fine.
```
root@zoccolotta:~ # lsusb
Bus 001 Device 004: ID 054c:019e Sony Corp.
Bus 001 Device 002: ID 06b9:4061 Alcatel Telecom Speed Touch ISDN or ADSL Modem
Bus 001 Device 001: ID 0000:0000
```

If I use other USB products (modem, other pendrive, card reader, mouse, etc) all works fine in PC1 and PC2.

I tried all USB ports in PC1 but Sony Micro Vault doesn't work.

What I have to do?

Thank you.

PS: I'm sorry for my english

---

### Post by PaRRoT.it on 2005-04-23
up  :?

---

### Post by PaRRoT.it on 2005-04-24
I tried also the same kernel (2.6.10 686)... but I've the same problem.

:(

---

### Post by PaRRoT.it on 2005-04-25
Up

---

### Post by az on 2005-04-25
I have a 64 Meg Sony Microvault.  It is a bit funny in comparison to other pen drives.  To be a usb2 device, they have a usb hub integrated in the device.  This is problematic for me at work, since it is not detected as an external hard drive, but an external usb hub.  It is /dev/sda instread of /dev/sda1.  This is fine, and it is not the only device on the market to do that.

If you are sure that there is not other hardware problem (like, try unplugging all the other usb devices to see if that helps.) you should look to see if there is a bug report for this.  If not, maybe open one.

bugzilla.ubuntu.com

---

### Post by PaRRoT.it on 2005-04-25
[QUOTE=azz]I have a 64 Meg Sony Microvault.  It is a bit funny in comparison to other pen drives.  To be a usb2 device, they have a usb hub integrated in the device.  This is problematic for me at work, since it is not detected as an external hard drive, but an external usb hub.  It is /dev/sda instread of /dev/sda1.  This is fine, and it is not the only device on the market to do that.

If you are sure that there is not other hardware problem (like, try unplugging all the other usb devices to see if that helps.) you should look to see if there is a bug report for this.  If not, maybe open one.

bugzilla.ubuntu.com[/QUOTE]
 I tried various bios versions and settings: under Windows works good, under Ubuntu works on PC2 and not on PC1...

I don't know what to think...

---

