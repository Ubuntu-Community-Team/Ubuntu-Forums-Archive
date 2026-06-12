---
title: "Atheros AR5001X Mini PCI Wireless Adaptor"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by fwallace99 on 2007-04-14
Hi All --

Hope you can help me.

I have a Toshiba Satellite A135-S2276 Laptop. I'm running Ubuntu 6.06. I like it a lot.

However, I have to use a spare Belkin Wireless PCMCIA adapter instead of the built-in adapter. My built in adapter is an Atheros AR5001X Mini PCI Wireless Adapter.

Here's my output from dmesg:

[17179587.756000] new_ath_hal: module license 'Proprietary' taints kernel.
[17179587.756000] new_ath_hal: 0.9.16.16 (AR5210, AR5211, AR5212, RF5111, RF5112 , RF2413, RF5413)
[17179587.968000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179588.000000] wlan: 0.8.4.2 (svn 2007-02-01)
[17179588.004000] new_ath_rate_sample: 1.2 (svn 2007-02-01)
[17179588.012000] ath_pci: 0.9.4.5 (svn 2007-02-01)
[17179588.012000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 233
[17179588.012000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179588.012000] wifi%d: unable to attach hardware: 'Hardware revision not supp orted' (HAL status 13)

Why does the "module license 'Propietary' taint the kernel? 

What can I do to get my internal adapter working? I'd like to be able to use the internal adapter and use the Belkin adapter on another computer.

Any help greatly appreciated.

ETA: Moving this to wireless forum, sorry i didn't see it there first.

---

