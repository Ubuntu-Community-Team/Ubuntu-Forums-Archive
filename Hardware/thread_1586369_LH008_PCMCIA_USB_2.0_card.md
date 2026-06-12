---
title: "LH008 PCMCIA USB 2.0 card"
date: 2010-10-01
forum: Hardware
---

### Post by poltr1 on 2010-10-01
I recently picked up a generic 4-port USB 2.0 PCMCIA card off of EBay.  I'm trying to get it to work, and it doesn't appear to be doing so.  The only identification I could find was on the underside: LH008.  

output from lspci:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

selected output from lshw:
        .
        .
        .
     *-usb:0
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:02:00.0
          version: 62
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=uhci_hcd latency=22
          resources: irq:11 memory:24000000-240000ff ioport:1000(size=32)
     *-usb:1
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 0.1
          bus info: pci@0000:02:00.1
          version: 62
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=uhci_hcd latency=22
          resources: irq:11 memory:24000100-240001ff ioport:1020(size=32)
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: VIA Technologies, Inc.
          physical id: 0.2
          bus info: pci@0000:02:00.2
          version: 65
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ehci_hcd latency=22
          resources: irq:11 memory:24000200-240002ff 
        .
        .
        .

So I now know it contains a VIA Technologies chipset.  Yet when I go to their website, they don't list this device as one of their own.  Looking at the configuration, I'm wondering if there's a driver conflict and whether I'll need to blacklist one of these drivers.

---

### Post by poltr1 on 2010-10-02
Tried blacklisting uhci_hcd.  Rebooted.  No effect.  (Except for KO'ing the wireless network adapter i had plugged in the computer's USB 1.1 port.)

Tried blacklisting ehci_hcd.  Rebooted.  No effect.

Also put the card into a laptop running Windows XP.  It found and installed the drivers, but none of the ports had power.

I also have a Startech 4-port USB 2.0 PCMCIA card.  That worked on Ubuntu,

I think I have a bad card.  I'll see about getting a replacement.

---

### Post by igor47 on 2011-01-27
I too got one of these from ebay, tho mine came with a power cable.

Apparently the unit will not function w/out DC being "plugged in" to the female jack in between the 4 USB ports.

I'm still unable to find instructions, tho. 


Hoping that this may help.

:confused:

---

