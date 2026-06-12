---
title: "Asus P5Q-E and USB-keyboard"
date: 2008-10-20
forum: Hardware
---

### Post by Ape3000 on 2008-10-20
I have an Asus P5Q-E motherboard and a Razer Tarantula USB-keyboard. The keyboard is working fine on Ubuntu, but it doesn't work on BIOS or GRUB. I must plug a PS/2 keyboard to use these.

So this problem is not related to Ubuntu, but my motherboard. My old motherboard did work on BIOS with this keyboard. I have also tried enabling legacy USB etc from the BIOS with no luck.

---

### Post by raygj on 2008-10-21
boot up into "bios setup utility"
go to "advanced" tab
select "usb configuration"
select "legacy usb support" and change its setting from "auto" to "enabled"


also in "advanced pci/pnp settings"
set "plug and play o/s" to "NO" so that the "bios" sets up all devices before "Grub" tries to access "keyboard"

save new settings (F10)
reboot and bios  and "grub" will use usb keyboard for input" 
regards ray

---

### Post by Ape3000 on 2008-10-26
> **raygj said:**
> boot up into "bios setup utility"
go to "advanced" tab
select "usb configuration"
select "legacy usb support" and change its setting from "auto" to "enabled"


also in "advanced pci/pnp settings"
set "plug and play o/s" to "NO" so that the "bios" sets up all devices before "Grub" tries to access "keyboard"

save new settings (F10)
reboot and bios  and "grub" will use usb keyboard for input" 
regards ray

It still doesn't work with those settings.

---

### Post by Ape3000 on 2008-10-29
bump

---

### Post by Ape3000 on 2008-11-10
last bump

---

