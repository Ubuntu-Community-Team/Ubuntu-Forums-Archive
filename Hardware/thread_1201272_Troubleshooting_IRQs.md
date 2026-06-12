---
title: "Troubleshooting IRQs"
date: 2009-06-30
forum: Hardware
---

### Post by gurt on 2009-06-30
I need to get all this stuff working in my 9.04 64-bit Desktop....
- 4-port serial card (SIIG Cyberserial 4S PCIe) <installed>
- 3 dual-port Ethernet cards (Intel Pro 100) <installed>
- 6 Davicom Ethernet USBs (using 2 4-port unpowered USB dongle)

I had a pretty big crash and had to reinstall Ubuntu. I think the problem was HW related. I'm trying to figure out how to set up my IRQs -- just guess that might be part of the problem.

Looking at some other posts I've collected some output -- but I'm not really sure what it's telling me or how I should go about resolving IRQ issues.

```
gurt@mingus:~$ cat /proc/interrupts 
           CPU0       CPU1       
  0:        112          5   IO-APIC-edge      timer
  1:       2059       2048   IO-APIC-edge      i8042
  4:          2          3   IO-APIC-edge    
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      56567      56899   IO-APIC-edge      i8042
 14:      17496      17492   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:       2088       2055   IO-APIC-fasteoi   uhci_hcd:usb5, HDA Intel, eth1
 17:        861        862   IO-APIC-fasteoi   eth2
 18:       1717       1711   IO-APIC-fasteoi   uhci_hcd:usb4, eth4, eth3
 19:       6926       6998   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3, eth5
 23:      52821      53215   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
2300:     196767     197050   PCI-MSI-edge      i915@pci:0000:00:02.0
2301:          0          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     189431     277100   Local timer interrupts
RES:       3649       5774   Rescheduling interrupts
CAL:         72         59   Function call interrupts
TLB:       1084       2416   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
``````

gurt@mingus:~$ lspci -b -vv |grep Interrupt:
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 3
    Interrupt: pin B routed to IRQ 5
    Interrupt: pin C routed to IRQ 10
    Interrupt: pin D routed to IRQ 10
    Interrupt: pin A routed to IRQ 3
    Interrupt: pin A routed to IRQ 0
    Interrupt: pin B routed to IRQ 5
    Interrupt: pin B routed to IRQ 5
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 11
    Interrupt: pin B routed to IRQ 10
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 11
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 10
    Interrupt: pin A routed to IRQ 5
```Please be gentle, I'm still learning -- Thanks ](*,)

---

