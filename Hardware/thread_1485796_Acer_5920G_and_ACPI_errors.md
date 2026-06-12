---
title: "Acer 5920G and ACPI errors"
date: 2010-05-17
forum: Hardware
---

### Post by littlesatan on 2010-05-17
Hey guys.
Here is the problem:
```

$ dmesg |grep ACPI
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfee1000 (ACPI NVS)
[    0.000000]  modified: 00000000bfed0000 - 00000000bfee1000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f7ae0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfed38c5 0007C (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfeddc2a 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfed4db5 08E01 (v02 INTEL  CRESTLNE 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS bfee0fc0 00040
[    0.000000] ACPI: APIC bfeddd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bfeddd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfedddbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfedddfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfedde62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfedde8a 00176 (v01 ACRSYS ACRPRDCT 06040000 acer 00000000)
[    0.000000] ACPI: SSDT bfed4ad8 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed3efd 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed3e57 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed3941 00516 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.026705] ACPI: Core revision 20090903
[    0.176598] ACPI: bus type pci registered
[    0.181306] ACPI: EC: Look up EC in DSDT
[    0.185461] ACPI: BIOS _OSI(Linux) query ignored
[    0.204112] ACPI: Interpreter enabled
[    0.204122] ACPI: (supports S0 S3 S4 S5)
[    0.204147] ACPI: Using IOAPIC for interrupt routing
[    0.209184] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.209542] ACPI: No dock devices found.
[COLOR=Red][B][    0.210127] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.210134] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND[/B][/COLOR]
[    0.210164] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.211687] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[B][    0.214482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.214823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.214908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.214983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.215089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[COLOR=Red][    0.215184] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.215190] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND[/COLOR]
[    0.227292] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.227402] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.227510] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.227615] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.227721] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.227827] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.227931] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.228050] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)[/B]
[    0.228753] ACPI: WMI: Mapper loaded
[    0.228756] PCI: Using ACPI for IRQ routing
[    0.234207] pnp: PnP ACPI init
[    0.234222] ACPI: bus type pnp registered
[    0.236585] pnp: PnP ACPI: found 11 devices
[    0.236588] ACPI: ACPI bus type pnp unregistered
[    0.236592] PnPBIOS: Disabled by ACPI PNP
[COLOR=Red][B][    0.287518] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287524] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287598] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287603] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287667] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287673] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287737] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287743] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287822] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287828] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287891] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287897] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.287959] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.287964] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND
[    0.288026] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.288032] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013270), AE_NOT_FOUND[/B][/COLOR]
[    0.288431] ACPI: AC Adapter [ACAD] (on-line)
[    0.288576] ACPI: Lid Switch [LID]
[    0.288623] ACPI: Power Button [PWRB]
[    0.288670] ACPI: Sleep Button [SLPB]
[    0.288718] ACPI: Power Button [PWRF]
[    0.289415] ACPI: SSDT bfed47d8 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.289993] ACPI: SSDT bfed415c 005F7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.292836] ACPI: SSDT bfed4a10 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.293230] ACPI: SSDT bfed4753 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.304294] ACPI: Thermal Zone [THRM] (61 C)
[    0.317359] ACPI: Battery Slot [BAT1] (battery absent)
[COLOR=Red]**[    1.185313] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)**[/COLOR]
[   24.870319] acer-wmi: Acer Laptop ACPI-WMI Extras
[   25.049651] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

```I'm running 10.04 with 2.6.32-22-generic.

Any suggestions?

---

### Post by littlesatan on 2010-05-17
Maybe somebody know some guy who at least heard something about how to fix that? :(

---

### Post by dino99 on 2010-06-06
this line (you have posted) have given you this suggestion:

ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]

so add [COLOR="Blue"]acpi_apic_instance=2[/COLOR] on the boot line to know if that help

and send a email to [COLOR="Red"]linux-acpi@vger.kernel.org[/COLOR]

about: ae_not_found

[http://www.google.fr/search?as_q=%22AE_NOT_FOUND%22&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=%22AE_NOT_FOUND%22&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by littlesatan on 2010-07-01
Thank you, dino99! [COLOR=Blue]acpi_apic_instance=2[/COLOR] fix all the errors, except «[COLOR=Red]ae_not_found[/COLOR]», which as i believe can be fixed by custom DSDT table, but i can't find any for my laptop, and i don't want to recompile system kernel.
Thank you anyway.

---

### Post by mockingbird on 2010-10-25
I am adding acpi_apic_instance=2 to my /etc/default/grub but it still gives me that message.  I'm not getting any ACPI errors, but I want to try the second table to see if that populates my /proc/acpi/fan

I've already tried recompiling my DSDT without errors.

---

