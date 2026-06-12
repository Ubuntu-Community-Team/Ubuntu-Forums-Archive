---
title: "IRQ Conflict - Nvidia vs AHCI"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by abeowitz on 2008-03-24
When AHCI and Nvidia share the same IRQ, the system is very unstable:

```
           CPU0       CPU1       
  0:     102221     125316   IO-APIC-edge      timer
  1:        316        163   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:       3738       3310   IO-APIC-fasteoi   acpi
 12:         58         58   IO-APIC-edge      i8042
 14:         31         32   IO-APIC-edge      ide0
** 16:     108838      90344   IO-APIC-fasteoi   [COLOR="Red"]ahci,[/COLOR] firewire_ohci, uhci_hcd:usb3, [COLOR="Red"]nvidia[/COLOR]**
 18:         15         13   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 20:      20615      19242   IO-APIC-fasteoi   ata_piix
 21:         16         16   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        130        119   IO-APIC-fasteoi   HDA Intel
 23:          8          8   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
311:          2          1   PCI-MSI-edge      eth0
312:      58167      55444   PCI-MSI-edge      iwl4965
316:          0          0   PCI-MSI-edge      pciehp
319:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:      63724      87802   Local timer interrupts
RES:      20832      19099   Rescheduling interrupts
CAL:        350        563   function call interrupts
TLB:         34         14   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

```

I get tons of these messages in dmesg... ONLY while X is running.  i.e. gdm and logged in sessions.  If I disable GDM and reboot, the system is stable.

```
ACPI: EC: acpi_ec_wait timeout, status = 9, expect_event = 2
ACPI: EC: input buffer is not empty, aborting transaction
ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.BRCP] (Node ffff81013fc3ee00), AE_TIME
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node ffff81013fc3ebc0), AE_TIME
ACPI Exception (battery-0361): AE_TIME, Evaluating _BST [20070126]
ACPI: EC: acpi_ec_wait timeout, status = 9, expect_event = 2
ACPI: EC: input buffer is not empty, aborting transaction
ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.BSTS] (Node ffff81013fc3edc0), AE_TIME
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node ffff81013fc3ebc0), AE_TIME
ACPI Exception (battery-0361): AE_TIME, Evaluating _BST [20070126]
ata1: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
ata1: exception Emask 0x73 SAct 0x0 SErr 0xffffffff action 0xe frozen t4
ata1: irq_stat 0xff7fffff, unknown FIS 00000000 00000000 00000000 00000000, host bus 
ata1: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }
ata1: hard resetting link
ACPI: EC: acpi_ec_wait timeout, status = 1, expect_event = 2
ACPI: EC: input buffer is not empty, aborting transaction
ata1: SATA link down (SStatus 0 SControl 300)
ata1: exception Emask 0x33 SAct 0x0 SErr 0x0 action 0xa t3
ata1: irq_stat 0xff7fffff, unknown FIS 00000000 00000000 00000000 00000000, host bus 
ata1: hard resetting link
ata1: SATA link down (SStatus 0 SControl 300)
ata1: EH complete
ata1: exception Emask 0x73 SAct 0x0 SErr 0xffffffff action 0xe frozen
ata1: irq_stat 0xffffffff, unknown FIS 00000000 00000000 00000000 00000000, host bus 
ata1: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }

```

I've tried all the noapic, acpi=off, irqpoll, nolapic, etc. kernel parameters, and compiled many different kernels with different settings.  Nothing helps.  I've spent 2 weeks on this bug!

**The ONLY thing that stabilizes Linux on my laptop is booting into windows, then rebooting into Linux.  Booting into windows sets my interrupts up in a stable manner:**

```

           CPU0       CPU1       
  0:      79670      87189   IO-APIC-edge      timer
  1:        750        638   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:        839        820   IO-APIC-fasteoi   acpi
 12:         62         66   IO-APIC-edge      i8042
 14:         35         28   IO-APIC-edge      ide0
** 16:      22413      16866   IO-APIC-fasteoi   firewire_ohci, uhci_hcd:usb3, nvidia**
 18:       2559       2303   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 20:       6247       5703   IO-APIC-fasteoi   ata_piix
 21:         16         16   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        192        194   IO-APIC-fasteoi   HDA Intel
 23:          8          9   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
311:          0          0   PCI-MSI-edge      eth0
312:      11113       9987   PCI-MSI-edge      iwl4965
316:          0          0   PCI-MSI-edge      pciehp
319:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:      75148      80356   Local timer interrupts
RES:      22570      24056   Rescheduling interrupts
CAL:       4875       3963   function call interrupts
TLB:        166        182   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

```

Note no AHCI this boot...?!?!?  

Sometimes my wireless card (iwl4965) would appear in IRQ 16, too.  

Same problem in 2.6.24 and also 2.6.25-rc6

**[SIZE="4"]So, my question is, HOW can I tell Linux to assign my interrupts in a stable manner?[/SIZE]**  

Without having to boot into windows all the time... :(  

Why do the IRQ's vary from boot to boot?  :confused:

---

### Post by abeowitz on 2008-03-25
OK, learning a lot here...

Here's what I found out.

AHCI and ata_piix are 2 different drivers.  I thought I needed both, as Ubuntu Hardy's 2.6.24 loads both modules.  It seems these modules conflict with each other.

More info:
[http://linux-ata.org/driver-status.html](http://linux-ata.org/driver-status.html)

ALSO, the BIOS in my laptop (Asus G2S) has a 'compatible' and 'enhanced' SATA mode.  When in compatible, the ata_piix driver works great.  When set to 'enhanced', I need the AHCI driver working.

The AHCI driver will fail if the BIOS is set to SATA 'compatible' mode.

I had both of these drivers compiled into the kernel.  (Wasn't using initrd due to many recompiles.)  So, I suspect these conflicted.

It turns out that booting into Vista *sometimes* changed the AHCI state, and the AHCI driver failed in Linux, so the ata_piix driver took over, and all was stable.

It looks like I need pci=noacpi and acpi=strict as kernel parameters, however.

---

