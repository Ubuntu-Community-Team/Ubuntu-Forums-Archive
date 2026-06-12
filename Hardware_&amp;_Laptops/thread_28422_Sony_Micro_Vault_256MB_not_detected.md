---
title: "Sony Micro Vault 256MB not detected"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by PaRRoT.it on 2005-04-20
Hi,
i've a 256MB Sony Micro Vault USB 2.0 that works fine in Windows (after connection to USB ports blink a green led on it) but i don't understand why don't works in Ubuntu.

If I connect Micro Vault to USB ports (whichever ports) green led don't blink and "lsusb" don't find my pendrive.
If I connect others USB storage peripherals (MMC/SD reader [USB 1.1] or 32MB pendrive [USB 1.1]) work fine and "lsusb" find them.

What is the problem? USB 2.0 storage incompatibility?

Thank you in advance.

---

### Post by PaRRoT.it on 2005-04-20
up

---

### Post by PaRRoT.it on 2005-04-21
[QUOTE=PaRRoT.it]up[/QUOTE]
 I've found the error (in syslog and kern.log):

```
Apr 21 10:07:21 papousek kernel: usb 4-1: new high speed USB device using ehci_hcd and address 3
Apr 21 10:07:22 papousek kernel: usb 4-1: device descriptor read/all, error -71

```

What is this? :(

---

### Post by sergiopcms on 2005-05-01
exact same problem here  :| 

i have too a sony micro vault 256MB that any linux distribution recognize.

does anyone have a solution for this?

---

