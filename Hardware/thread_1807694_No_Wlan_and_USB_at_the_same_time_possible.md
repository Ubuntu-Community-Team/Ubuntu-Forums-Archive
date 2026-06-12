---
title: "No Wlan and USB at the same time possible"
date: 2011-07-19
forum: Hardware
---

### Post by PatrickH on 2011-07-19
H
I'm running Ubuntu 11.04 on my Packard Bell EasyNote R1900 Laptop.

My problem is, that I could not get the Wlan Card and the USB working at the same time.

At the first start after installation my USB mouse works well but not the Wlan card.  I found out, that the bootoption "acpi=force" bring on the Wlan but ruin the USB mouse (the trackpad works well).

I tryed some combinations but all either with no Wlan or no USB.

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=force usb=bios"

# GRUB_CMDLINE_LINUX="acpi=force pci=routeirq" Wlan but problems with USB
# GRUB_CMDLINE_LINUX="pci=routeirq" no Wlan
# GRUB_CMDLINE_LINUX="pci=bios no Wlan
# GRUB_CMDLINE_LINUX="nolapic" no Wlan
# GRUB_CMDLINE_LINUX="noapic" no Wlan
# GRUB_CMDLINE_LINUX="acpi=off" no Wlan
# GRUB_CMDLINE_LINUX="lapic" no Wlan
# GRUB_CMDLINE_LINUX="acpi=force" Wlan but problems with USB
# GRUB_CMDLINE_LINUX="pci=use_crs acpi=force lapic" Wlan but problems with USB
# GRUB_CMDLINE_LINUX="pci=use_crs pci=noacpi acpi=force lapic" no Wlan
# GRUB_CMDLINE_LINUX="pci=noacpi acpi=force lapic" no Wlan
# GRUB_CMDLINE_LINUX="pci=noacpi acpi_irq_balance acpi=force lapic" no Wlan
# GRUB_CMDLINE_LINUX="pci=use_crs pci=noacpi acpi_irq_balance acpi=force lapic" no Wlan
```

I would be happy if someone have an idea

regards
Patrick

---

### Post by ieee488 on 2011-07-19
Anything in your BIOS about USB etc?

---

### Post by PatrickH on 2011-07-20
Unfortunatey not, this Bios have very less parameters. I can only change the bootmedia

---

### Post by PatrickH on 2011-07-20
I posted this issue in the german ubuntu forum.
At this post you can see lots of informations about my system if that helps.

[http://forum.ubuntuusers.de/topic/ralink-rt2500-keine-verbindung-moeglich/](http://forum.ubuntuusers.de/topic/ralink-rt2500-keine-verbindung-moeglich/)

---

