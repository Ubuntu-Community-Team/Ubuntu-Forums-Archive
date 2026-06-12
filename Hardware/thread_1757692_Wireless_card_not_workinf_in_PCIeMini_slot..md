---
title: "Wireless card not workinf in PCIeMini slot."
date: 2011-05-13
forum: Hardware
---

### Post by Pone77 on 2011-05-13
Hi everyone!
  Ive been in love with ubuntu since Lucid, and I'm using Natty on a Packard Bell Dot S2 netbook at the moment, but I've got an odd problem:

I've changed my wireless card from a half height card to a full height card, which means I have to use the other PCIe Mini slot, as there isn't room.

When I start Natty with the new card, although iwconfig and lshw show it as present and the drivers are ok, it doesn't work, and says "device not ready" in the network manager.  **HOWEVER**, if i put it into the half-height slot, and hold it in place with my finger (!) it works great! Strange!

I'm aware that this may not be an Ubuntu issue, but can anyone shed any light as to why the** card works in one slot, but not the other?** And is it possible to make it work in the other slot, otherwise I've have to get out the saw to make it fit....!

Huge thanks to all on the forums, as you've already solved so many of my Ubuntu teething problems!

-Tony

---

### Post by Pone77 on 2011-05-14
I've been doing a little more digging, but still no success.  Maybe I need ot move this to the networking forum? I ran lshw and the output was:

>  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: [REMOVED]
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan4
       version: 02
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:55000000-55000fff


Its the intel wireless on wlan4 that's giving me trouble.  Its almost as if if just turned off?  i've tried basic things like fn+f2.  Maybe its a irq problem? I appreciate any help,

Thanks again, Tony

---

### Post by Pone77 on 2011-05-14
I added 

```
acpi=off
```to the start up via grub, and the wifi card will work, but obviously I loose all acpi functions (audio, battery etc), so its not really a practical solution.

Does this narrow it down at all?

-Tony

---

### Post by PhantmKllr on 2011-05-14
I know it may be a long-shot, but you should try updating your BIOS to the latest version (provided by your computer manufacturer).

---

### Post by Pone77 on 2011-05-15
Hi, thanks for the idea, but I checked and I already have the latest version.  For what its worth, I cant seem to get it to work when I boot Windows 7 either, which presumably has its own acpi settings.

 I also tried the original card in the problematic slot, and the problem is the same, so I'm ruling out any driver issue, or card specific issues.

-Tony

---

### Post by PhantmKllr on 2011-05-15
Perhaps the slot was disabled by the manufacturer. They probably didn't expect anyone to use it.

---

### Post by Pone77 on 2011-05-16
Well theres the odd thing, with ACPI=off, the slot DOES work, but I don't want to lose all the ACPI stuff (sound control, power save etc etc).

For the time being, I've just snipped of the plastic tabs that were in the way of the other slot, and jammed the card in there!  A 'hardware' solution to a software problem!

-Tony

---

### Post by PhantmKllr on 2011-05-17
=D>

Whatever works for you. :D

---

