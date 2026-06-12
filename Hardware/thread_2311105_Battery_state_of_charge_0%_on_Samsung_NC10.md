---
title: "Battery state of charge 0% on Samsung NC10"
date: 2016-01-24
forum: Hardware
---

### Post by Querby on 2016-01-24
Hi Forum!

I have digged out my old Samsung NC10 and thrown lubuntu 15.10 on it. It runs fine, the only problem is that the battery state of charge is stuck on 0%. 
The battery is definitely working fine. If I unplug the charger it goes into sleep mode and after I turned it on again it runs for ours. the bad thing is that Windows shows the battery state of charge quite nicely, no problem at all. But that is not an option.
As I thought I had ubuntu fully running and working on this machine in the past (but not sure about it) I also tried:

lubuntu 14.04.3
lubuntu 10.10
lubuntu 10.04
elementry
and even the latest Fedora

They all have the same problem :-(

There is one problem though that I'm not sure about whether that might be connected to my battery problem. This is what dmesg tells me about it:

[   11.862010] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\PMIO) (20150619/utaddress-254)
[   11.862037] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.862048] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150619/utaddress-254)
[   11.862067] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.862075] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150619/utaddress-254)
[   11.862092] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.862098] lpc_ich: Resource conflict(s) found affecting gpio_ich

Does anybody have an idea?
Is there a patch for this?

Thanks for any help.

Cheers, Querby

---

### Post by Querby on 2016-01-25
Sorry to bug again, is there really nobody with an idea?

---

