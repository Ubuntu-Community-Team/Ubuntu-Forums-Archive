---
title: "Unibrain Fireboard 800 1394b adapter causes boot to fail"
date: 2008-10-24
forum: Hardware
---

### Post by ubt_user_0331 on 2008-10-24
Hello all, I recently got a new Unibrain Fireboard 800 1394 adapter and Ubuntu 8.04 cannot boot normally anymore. The problem occurs only when the adapter is inserted in the PCI slot. The system boots normally without the adapter in the slot.
I know that using different hardware is probably the best solution but this is not my personal computer and the people I answer to wants this combo up and running.
My hardware configurations are:
1. PCI 6870 Board computer
2. Unibrain Fireboard 800

During recovery mode, the boot stops after assigning IRQ to the 1394 device.
Oddly, the system boots if I perform the following
1. Add boot option "break" during GRUB menu
2. after initramfs prompt comes, wait for a few seconds and do "modprobe ohci1394"
3. (initramfs) return

I tried noapic noacpi and also messed with the BIOS settings but to no avail.
When it does boot (after above steps), lspci shows the correct device, TSB82AA2 1394b adapter. 
Output from /proc/interrupts showed that the device was sharing IRQ with SMBus (whatever this is) and I tried changing IRQ assignments from BIOS and /interrupts showed that ohci1394 was alone but still couldnt boot.

Any suggestions will be appreciated,
Thanks.

---

