---
title: "Spurious wakeups on Thinkpad X61"
date: 2009-04-29
forum: Hardware
---

### Post by D0ckR0ach on 2009-04-29
Has anyone else run into an issue (especially on the Thinkpad X61) where the computer gets very hot while idle?  Further investigation using powertop reveals this to be caused by the dreaded Rescheduling Interrupts.  Here is what my /proc/interrupts looks like:

```
           CPU0       CPU1       
  0:     246993     246995   IO-APIC-edge      timer
  1:       1808       1865   IO-APIC-edge      i8042
  4:          1          1   IO-APIC-edge    
  7:          0          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:       2935       2975   IO-APIC-fasteoi   acpi
 12:     112263     112478   IO-APIC-edge      i8042
 14:       1563       1522   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5, yenta
 17:       2300       2326   IO-APIC-fasteoi   uhci_hcd:usb6, ohci1394, ath, HDA Intel
 18:          0          0   IO-APIC-fasteoi   mmc0
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 20:         83         99   IO-APIC-fasteoi   uhci_hcd:usb3
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:         21         17   IO-APIC-fasteoi   ehci_hcd:usb1
2299:      53705      53341   PCI-MSI-edge      i915@pci:0000:00:02.0
2300:       4927       4809   PCI-MSI-edge      eth0
2301:      20550      20254   PCI-MSI-edge      ahci
2302:          0          0   PCI-MSI-edge      pciehp
2303:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:     774979     771060   Local timer interrupts
RES:    6370922    7064462   Rescheduling interrupts
CAL:         88         72   Function call interrupts
TLB:        281        250   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Booting with the noacpi kernel parameter solves the issue (but isn't a viable solution because of other issues it causes).  I'm wondering if I should make a bug report of this or if anyone has any suggestions of what might fix it.  I do not want to have to compile my own DSDT for this, simply because Ubuntu should support the default hardware DSDT.  Thanks in advance for any help you can give me.

---

### Post by D0ckR0ach on 2009-04-29
Oh, BTW, this was a minor issue in Intrepid, but ever since upgrading to Jaunty, it has caused my laptop to get *really* hot.

---

### Post by ubunxpm on 2009-06-07
Hello,

I`m using a 7767-C3U x61t. Wonder what your hardware specs look like.. cause I`m not having such high temp issues. Though my interrupts don`t look any better than yours...

```
           CPU0       CPU1
  0:      54262      54315   IO-APIC-edge      timer
  1:       3436       3376   IO-APIC-edge      i8042
  5:          7         11   IO-APIC-edge      serial
  8:          0          1   IO-APIC-edge      rtc0
  9:       2075       2056   IO-APIC-fasteoi   acpi
 12:      11096      10848   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5, yenta
 17:       1231       1117   IO-APIC-fasteoi   uhci_hcd:usb6, ohci1394, HDA Intel
 18:          0          0   IO-APIC-fasteoi   mmc0
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 20:        103        113   IO-APIC-fasteoi   uhci_hcd:usb3
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:          1          4   IO-APIC-fasteoi   ehci_hcd:usb1
2298:      23244      22062   PCI-MSI-edge      i915@pci:0000:00:02.0
2299:      23986      22440   PCI-MSI-edge      iwl3945
2300:        553        631   PCI-MSI-edge      eth0
2301:       6461       6215   PCI-MSI-edge      ahci
2302:          0          0   PCI-MSI-edge      pciehp
2303:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:      42521      52250   Local timer interrupts
RES:      39070      32189   Rescheduling interrupts
CAL:         67         60   Function call interrupts
TLB:        338        320   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

I know this really is a late reply, just wanted to comment on it.

---

