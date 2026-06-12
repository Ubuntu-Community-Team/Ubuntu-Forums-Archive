---
title: "firewire expresscard issue"
date: 2008-09-04
forum: Hardware
---

### Post by gregolak on 2008-09-04
Hi,

I am trying a firewire expresscard on my acer laptop, and it does not work(I read that this card is working on linux, that's why I choose it).The card is recognized as PCI device, but il should IMHO also appear as firewire device.

```

lspci -v :

02:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
	Capabilities: [80] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [90] Express PCI/PCI-X Bridge IRQ 0

```

I tried "modprobe pciehp pciehp_force=1", "modprobe pci_hotplug" but same thing...
I tried to plug the card before boot (just a few seconds after turning the laptop on, it freezes
if I plug it before...) and after.


```

/var/log/syslog while I plus the card
Sep  4 12:03:54 felicien kernel: [  219.018074] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep  4 12:04:29 felicien kernel: [  229.482108] pciehp: Card present on Slot(0002_0000)
Sep  4 12:04:29 felicien kernel: [  229.494238] pciehp: Card not present on Slot(0002_0000)
Sep  4 12:04:29 felicien kernel: [  229.506370] pciehp: Card present on Slot(0002_0000)
Sep  4 12:04:29 felicien kernel: [  229.512563] pciehp: Card not present on Slot(0002_0000)
Sep  4 12:04:29 felicien kernel: [  229.513923] hub 6-0:1.0: over-current change on port 2
Sep  4 12:04:29 felicien kernel: [  229.518609] pciehp: Card present on Slot(0002_0000)
Sep  4 12:04:29 felicien kernel: [  229.545152] hub 1-0:1.0: over-current change on port 2
Sep  4 12:04:30 felicien kernel: [  229.803697] pciehp: No bus number available for hot-added bridge 0000:02:00.0
Sep  4 12:04:30 felicien kernel: [  229.803765] program_fw_provided_values: Could not get hotplug parameters
Sep  4 12:04:30 felicien NetworkManager: <debug> [1220522670.621720] nm_hal_device_added(): New device added (hal udi is '/org/freedesk
top/Hal/devices/pci_104c_8231').

```



```

 cat /proc/interrupts
           CPU0       CPU1       
  0:     273785     271984   IO-APIC-edge      timer
  1:        476        476   IO-APIC-edge      i8042
  8:          4          3   IO-APIC-edge      rtc
  9:        622        648   IO-APIC-fasteoi   acpi
 12:         67         82   IO-APIC-edge      i8042
 14:       1514       1433   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:       7734       7705   IO-APIC-fasteoi   uhci_hcd:usb1, nvidia
 18:          1          0   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb6
 19:        727        697   IO-APIC-fasteoi   uhci_hcd:usb4
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:         16         11   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb7
 22:          1          1   IO-APIC-fasteoi   ohci1394
 23:         68         75   IO-APIC-fasteoi   sdhci:slot0, HDA Intel
216:          2          2   PCI-MSI-edge      eth0
217:       4614       4586   PCI-MSI-edge      iwl3945
218:       6543       6447   PCI-MSI-edge      ahci
219:          0          0   PCI-MSI-edge      pciehp
220:          0          0   PCI-MSI-edge      pciehp
221:          0          0   PCI-MSI-edge      pciehp
222:          0          0   PCI-MSI-edge      pciehp
223:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:     168646     171337   Local timer interrupts
RES:     315974     310272   Rescheduling interrupts
CAL:       5181       5047   function call interrupts
TLB:        457        444   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:         29
MIS:          0

```

Do you think a bios flash could help ? I never did this but if I can't avoid...
Any other idea ? Thanks...

---

### Post by linuxpyro on 2011-05-02
Sorry to resurrect this thread, but I'm having pretty much the same problem in Maverick, also with an expresscard FireWire card.  I also tried the "modprobe pciehp pciehp_force=1" bit doesn't work for me.  I will add, though, that after running that, there is no pciehp module loaded when I do an lsmod.

Has anyone come up with a fix for this?  It seems like a kernel thing.  If I plug in the card and restart my laptop it is recognized just fine, and I can unplug it and replug it and it will then get hotplugged properly.

---

### Post by locutus42 on 2011-06-18
I didn't get lockups with the "pciehp.pciehp_force=1" option but it did stall for a long time. While I don't have your firewire/1394 card I was having problems getting hotswapping working with my eSATA card. What worked was enabling the ACPI hotplug driver with:

sudo modprobe acpiphp

again, no need for pciehp.pciehp_force=1

maybe that'll help some.

---

