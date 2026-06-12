---
title: "Continous error"
date: 2017-04-07
forum: Hardware
---

### Post by 4l3x2 on 2017-04-07
Good morning.
I have a problem with a pci card, if I write

tail -f /var/log/kern.log

I get continously the same 2 messages:
```
Apr  7 07:13:53 Alex kernel: [  185.786709] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.810770] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.814900] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.838960] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.843093] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.867152] pciehp 0000:00:1c.1 :pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.873966] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.898029] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.902159] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.926221] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.930351] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.954411] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.960964] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.985025] pciehp 0000:00:1c.1: pcie004: Card not present on Slot(33)
Apr  7 07:13:53 Alex kernel: [  185.989158] pciehp 0000:00:1c.1: pcie004: Card present on Slot(33)

```
I use Xubuntu 16.04.2 fully updated (but I had the same behavior with Debian 8) on an Intel 4core, 4Gb ram, Ati Radeon Toxic R09.
I also have 2 generic pci cards:
1 etthernet, because the integrated lan doesn't work
1 Firewire to connect my old Nikon SuperCoolscan 4000

Thank you very much for your help.

---

### Post by wildmanne39 on 2017-04-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

