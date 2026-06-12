---
title: "[SOLVED] Pci soundcard removed but still in cat /proc/interrupts"
date: 2008-09-23
forum: Hardware
---

### Post by DARKAD on 2008-09-23
I manually removed my pci soundcard but entering cat /proc/interrupts I see this on interrupt 10:
           CPU0       
  0:     882817    XT-PIC-XT        timer
  1:         81    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          1    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:       5112    XT-PIC-XT        ohci_hcd:usb1
  6:          2    XT-PIC-XT        floppy
  7:          0    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
 10:       1482    XT-PIC-XT        ohci1394, ehci_hcd:usb3, Ensoniq AudioPCI
 11:         28    XT-PIC-XT        eth0
 12:          0    XT-PIC-XT        ohci_hcd:usb2, uhci_hcd:usb4, uhci_hcd:usb5
 14:       8764    XT-PIC-XT        libata
 15:       6288    XT-PIC-XT        libata
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

Is that a bad error to remove?
Can I continue with it?

Thanks.

---

### Post by DARKAD on 2008-09-23
Sorry I made a mistake.

---

