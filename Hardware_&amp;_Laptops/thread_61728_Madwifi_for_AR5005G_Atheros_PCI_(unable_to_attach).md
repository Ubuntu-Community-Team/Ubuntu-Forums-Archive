---
title: "Madwifi for AR5005G Atheros PCI (unable to attach)"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by techpastor on 2005-09-01
I followed the recipe provided in this thread
[http://ubuntuforums.org/showthread.php?t=38972&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=38972&highlight=madwifi)
a few days ago on an ubuntu installation.  I prefer KDE so I installed kbuntu and went through the same steps.

I rebooted and it showed up in kwifi but it wouldn't connect me to the internet.  I tried to configure it in the control center but it wouldn't accept my password for the advanced controls.

I used the command line and the iwconfig but still it could see the  signal strength in kwifi but something was missing.  I did a dmesg again and it returned this  pertaining to ath_pci

ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
wlan: 0.8.6.0 (EXPERIMENTAL)
ath_rate_sample: 1.2
ath_pci: 0.9.6.0 (EXPERIMENTAL)
PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

any ideas? anything I can do to get it to attach?  I didn't give this message the first time.  Also kwifi won't find it at all now.

Thanks for you help

---

