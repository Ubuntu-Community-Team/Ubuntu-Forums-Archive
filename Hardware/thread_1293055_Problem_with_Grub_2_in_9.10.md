---
title: "Problem with Grub 2 in 9.10"
date: 2009-10-16
forum: Hardware
---

### Post by grazzmudhorze on 2009-10-16
Hi, guys,

I have been trying out the new 9.10 beta. I found some problem with the grub2 on my thinkpad T43. The bluetooth won't start automatically in ubuntu and XP! Also in XP, the screen won't turn off after idling for the time I set. I believe this is related to the ACPI setting in grub2. Any work around? BTW, I am installing Grub2 in MBR.

Another small bug is that I try to downgrade to grub 0.97, however the Synaptic said grub is depend on grub-common which is for grub 1.97. Any workaround for that?

Thanks

---

### Post by Giblet5 on 2009-10-16
Grub2 doesn't alter ACPI for Windows unless you changed the config to do so.

Grub2 boot to XP is the same as an XP-installed MBR boot.

Bluetooth has nothing to do with grub0-grub2.

---

### Post by Giblet5 on 2009-10-16
Are you using internal BT or a USB dongle?

---

### Post by grazzmudhorze on 2009-10-17
It is a internal Bluetooth. I think grub2 will preload some bios settings. This is actually how they hack the Win7 loader.

---

