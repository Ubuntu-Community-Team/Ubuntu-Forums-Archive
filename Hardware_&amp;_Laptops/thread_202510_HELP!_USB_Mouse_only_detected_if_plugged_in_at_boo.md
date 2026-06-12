---
title: "HELP! USB Mouse only detected if plugged in at boot"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by IndigoMontoya on 2006-06-23
Hi.  I have a USB mouse that works fine when it is plugged in during the boot, but if I plug it in after the computer (a laptop) is already on it does not work.

The red light on the bottom flashes red and the mouse does not respond.

dmesg says ```
hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?

```

but clearly the cable is fine because, well it works when at boot.

Also, I have USB thumbdrives that work fine.  Oh and I have tried difference ports.

Any ideas?

Thanks!

---

### Post by IndigoMontoya on 2006-06-24
Someone on another forum had suggested I revert to a 2.4 series kernel because 2.6 has been reported to be slightly buggy with USB.  What potential problems might this bring to my ubuntu installation, and is there a way to do this without compiling my own kernel (which I am fine doing?

---

### Post by Agabus on 2006-06-24
I am having the same problem with my laptop at the moment, and I'm searching for answers. I plug the USB mouse in after booting up, the light on the bottom of the mouse keeps flashing on and off until it is unplugged.

Reverting to the 2.4 kernel is not an option that I am willing to take to just get my mouse working. I am hopeful someone here will have the knowledge on how to fix this issue.

Agabus

---

### Post by Sye d'Burns on 2006-06-24
Perhaps try: sudo modprobe uhci_hcd

---

### Post by IndigoMontoya on 2006-06-24
I have already tried all combinations of uhci_hcd, ehci_hcd, and ohci_hcd.  A normal boot has uhci_hcd and ehci_hcd.  Ohci seems to have no effect.  

Thanks for the idea though.

ps am I right in thinking uchi is for 1.1 ports and ehci is for 2.0 ports?

---

