---
title: "[SOLVED] HP Pavilion Laptop Wireless"
date: 2008-07-14
forum: Hardware
---

### Post by kalchas on 2008-07-14
Hi all,

I've installed Ubuntu on an HP Pavilion DV6810 Laptop and I've been having trouble with getting the wireless to work. I turned of the atheros proprietary drivers, installed madwifi and ran sudo modprobe ath_pci. Everything worked. Then I rebooted the machine and wireless was down. I was able to isolate that as long as I run sudo modprobe ath_pci on each reboot, I'm good to go, wireless-wise. But this doesn't really seem like the best solution.

Any advice on how I might be able to get the machine to hold state on this?

Cheers,

K.

---

### Post by cdtech on 2008-07-14
Just add the ath_pci module to the /etc/modules file and it will load on every boot.

---

### Post by kalchas on 2008-07-16
Perfect, worked like a charm. Thank you, cdtech!

---

