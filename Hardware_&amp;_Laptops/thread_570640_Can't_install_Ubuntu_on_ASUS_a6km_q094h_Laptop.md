---
title: "Can't install Ubuntu on ASUS a6km q094h Laptop"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by kiriashoo on 2007-10-08
Config:
ASUS A6KM-Q094H AMD TURION 64 ML34, 512MB DDR, 80GB HDD, NVIDIA GEFORCE GO 7300, DVD-RW
Setup hangs early on... Tried some boot commands under Adv. Options like  vga=771 noapic nolapic but no change.
After Loading 100% frame... it gets black and after a few seconds the dvd stops spinning. (like idle mode)
The Kubuntu 7.10 DVD worked well on other laptop. 
Any help would be appreciated.

---

### Post by Kyran on 2007-10-12
Probably an ACPI issue. Try booting without any USB devices plugged in, and if that doesn't work, try booting with noacpi and acpi=off for advanced options.

---

### Post by kiriashoo on 2007-10-29
Thank you big time. I've tried it and it works well now. I always had  connected my usb optical mouse which came with the laptop. I've tried allmost all the comands on help index (F4,F5,F6) but not that one :)
Thanks again for the advice.

---

