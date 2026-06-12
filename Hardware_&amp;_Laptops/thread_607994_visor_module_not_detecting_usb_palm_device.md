---
title: "visor module not detecting usb palm device"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by guleblanc on 2007-11-09
I'm having trouble with the usb subsystem in my feisty installation.  I have a USB hub attached to my asrock k7upgrade-880 motherboard. My kernel is the stock ubuntu 2.6.15-27.  

 When I attach a palm tungsten t3 via the usb cable to the hub, the first time I attach after a fresh reboot works fine.  However, after the first sync, the palm no longer syncs.  The USB mouse and keyboard work fine.  I don't know about other usb devices.

After the first, successful sync, the kern.log file says:

Nov  9 07:09:19 crasher kernel: [17180219.284000] usb 5-3.6: new full speed USB device using ehci_hcd and address 8
Nov  9 07:09:19 crasher kernel: [17180219.376000] visor 5-3.6:1.0: Handspring Visor / Palm OS converter detected
Nov  9 07:09:19 crasher kernel: [17180219.376000] usb 5-3.6: Handspring Visor / Palm OS converter now attached to ttyUSB0
Nov  9 07:09:19 crasher kernel: [17180219.376000] usb 5-3.6: Handspring Visor / Palm OS converter now attached to ttyUSB1
Nov  9 07:09:39 crasher kernel: [17180239.048000] usb 5-3.6: USB disconnect, address 8
Nov  9 07:09:39 crasher kernel: [17180239.048000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Nov  9 07:09:39 crasher kernel: [17180239.048000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Nov  9 07:09:39 crasher kernel: [17180239.048000] visor 5-3.6:1.0: device disconnected

This is all well and good.   But then, after the second sync, the kern.log file says:
Nov  9 07:09:58 crasher kernel: [17180257.680000] usb 5-3.6: new full speed USB device using ehci_hcd and address 9
Nov  9 07:10:01 crasher kernel: [17180260.752000] usb 5-3.6: device descriptor read/64, error -110
Nov  9 07:10:16 crasher kernel: [17180275.928000] usb 5-3.6: device descriptor read/64, error -110
      ... This line is repeated many times ...

FWIW, the contents of /proc/interrupts says:
           CPU0
  0:    1410693    IO-APIC-edge  timer
  7:          2    IO-APIC-edge  parport0
  8:          3    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 14:      84867    IO-APIC-edge  ide0
 15:      50182    IO-APIC-edge  ide1
169:          0   IO-APIC-level  libata
177:     377465   IO-APIC-level  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5
185:      25992   IO-APIC-level  EMU10K1
193:      12062   IO-APIC-level  eth1
201:     333164   IO-APIC-level  radeon@pci:0000:01:00.0
and the network uses eth1.  eth


Has anybody seen this before?  I have tried these fixes:
1.) Reset the palm T3 device.
2.) rmmod the visor.ko module and modprobe it again.
3.) rmmod both visor.ko and usbserial.ko, then modprobe visor.ko
4.) boot with noapio, noapic nolapic, noacpi

I'm very confused.  This very hardware worked with eft just fine.

---

### Post by guleblanc on 2007-11-10
FWIW, the way to find an answer is to ask.  Once you ask publically, you will find it where you should have looked all along.

It appears that 2.6.15 has some problems with the usb subsystem.  2.6.12 does not, and
2.6.17 and above do not.  So, I need to upgrade or downgrade.

Sorry for bothering.

---

