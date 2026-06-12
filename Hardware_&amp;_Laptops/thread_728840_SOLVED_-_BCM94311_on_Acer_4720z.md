---
title: "SOLVED - BCM94311 on Acer 4720z"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by WhiteHorse on 2008-03-19
This worked for my Acer 4720z. The wireless card is a Broadcom BCM94311MCG. I performed the following steps in this order:

1. Connect the Ethernet to internet and get all updates.
2. In System->Administration->Restricted Drivers, enable the broadcom firmware. 
3. Reboot

Now it works fine and my lsmod shows:
ieee80211_crypt_tkip    11776  2
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211

lspci shows:
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

And dmesg shows:
[   19.212000] ieee80211_crypt: registered algorithm 'NULL'
[   19.224000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.224000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.432000] bcm43xx driver
[   19.432000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[   19.432000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16

---

