---
title: "need a HowTo: forcing a system to use custom DSDT"
date: 2009-05-25
forum: Hardware
---

### Post by CylnZ on 2009-05-25
Hi, I am using a Gateway 6860fx laptop
bios 94.29
running 9.04 2.6.29-02062903-generic

my problem:

```
CylnZ@CylnZ-laptop1:~$ dmesg | grep ACPI
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F7DC0, 0024 (r2 GATEWA)
[    0.000000] ACPI: XSDT BFED7620, 0074 (r1 GATEWA SYSTEM    6040000 WTAG        0)
[    0.000000] ACPI: FACP BFEDFC3A, 00F4 (r3 GATEWA SYSTEM    6040000 WIST        1)
[    0.000000] ACPI: DSDT BFED8784, 7442 (r2 GATEWA Godzilla  6040000 MSFT  2000001)
[    0.000000] ACPI: FACS BFEE2FC0, 0040
[    0.000000] ACPI: HPET BFEDFD2E, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFEDFD66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BFEDFDA2, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: SLIC BFEDFDD4, 0176 (r1 GATEWA SYSTEM    6040000 WIST        1)
[    0.000000] ACPI: TMOR BFEDFF4A, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC BFEDFF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFEDFFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BFED84A7, 02DD (r1 SataRe SataAhci     1000 INTL 20061109)
[    0.000000] ACPI: SSDT BFED7694, 04E6 (r1  PmRef    CpuPm     3000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.004000] ACPI: Core revision 20081204
[    0.148462] ACPI: bus type pci registered
[    0.161817] ACPI: EC: Look up EC in DSDT
[    0.166891] ACPI: BIOS _OSI(Linux) query ignored
[    0.168302] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.188126] ACPI: Interpreter enabled
[    0.188129] ACPI: (supports S0 S3 S4 S5)
[    0.188149] ACPI: Using IOAPIC for interrupt routing
[    0.209222] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.209224] ACPI: EC: driver started in interrupt mode
[    0.209403] ACPI: No dock devices found.
[    0.209441] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.209447] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    0.209491] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.212594] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.214477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.214822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.214911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.214996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.215081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.215165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.215268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.215364] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.215370] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    0.227671] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.227808] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.228094] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.228228] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.228361] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.228500] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.228636] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.228769] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.229131] ACPI: WMI: Mapper loaded
[    0.229131] PCI: Using ACPI for IRQ routing
[    0.256008] pnp: PnP ACPI init
[    0.256026] ACPI: bus type pnp registered
[    0.264532] pnp: PnP ACPI: found 10 devices
[    0.264535] ACPI: ACPI bus type pnp unregistered
[    1.056859] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.056865] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057356] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057361] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057463] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057468] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057570] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057575] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057675] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057680] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057780] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057785] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.057903] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.057909] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.058369] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.058374] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.058475] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.058480] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.058580] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.058586] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.058686] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.058691] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.058791] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.058796] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88013f812fe0), AE_NOT_FOUND
[    1.060650] ACPI: AC Adapter [ADP1] (on-line)
[    1.243520] ACPI: Battery Slot [BAT0] (battery present)
[    1.243599] ACPI: Power Button (FF) [PWRF]
[    1.251307] ACPI: Lid Switch [LID0]
[    1.251361] ACPI: Sleep Button (CM) [SLPB]
[    1.253932] ACPI: SSDT BFED81E9, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[    1.254449] ACPI: SSDT BFED7B7A, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
[    1.262684] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.262710] processor ACPI_CPU:00: registered as cooling_device0
[    1.268424] ACPI: SSDT BFED83DF, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20061109)
[    1.268808] ACPI: SSDT BFED8164, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20061109)
[    1.281153] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.281172] processor ACPI_CPU:01: registered as cooling_device1
[    1.324538] ACPI: Thermal Zone [TZS0] (41 C)
[    1.340598] ACPI: Thermal Zone [TZS1] (43 C)
[    1.684620] ACPI Warning (nspredef-0934): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20081204]
[    2.481818] ACPI Warning (nspredef-0934): \_SB_.PCI0.SATA.PRT1._GTF: Return type mismatch - found Integer, expected Buffer [20081204]
[   10.216202] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.555969] iwlagn 0000:02:00.0: power state changed by ACPI to D0
[   22.955972] iwlagn 0000:02:00.0: power state changed by ACPI to D0 
```I'm hoping this is my solution:

a custom DSDT file that has,

```
 Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  /home/CylnZ/dsdt.dsl - 7427 lines, 258581 bytes, 2928 keywords
AML Output: /home/CylnZ/dsdt.aml - 27724 bytes, 715 named objects, 2213 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 872 Optimizations

```That I fixed using 67GTA's tutorial on Buggy dsdt's.

Unfortunately, I have been unsuccessful at getting the system to use said DSDT file.
google gives me several hits @ insanelymac site but using a mac patcher doesnt really fit my needs. I'm sure there some of your penguins out there that can point me in the right direction, please? 
                                  -Thanks.

p.s. The fixed DSDT for the Gateway 6860 fx is post #15 in 
[http://ubuntuforums.org/showthread.php?p=7340745#post7340745](http://ubuntuforums.org/showthread.php?p=7340745#post7340745)  ):P

These are the final steps I've been using to install and try to use the dsdt:

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml

sudo update-initramfs -u -k 2.6.29-02062903-generic

or

sudo update-initramfs -c -k all
```I've tried both to no avail.

[COLOR=Red][COLOR=Black]ANSWER:[/COLOR] MUST USE A STABLE CURRENT KERNEL RELEASE NO RCS OR FUTURE KERNELS HAVE THE PATCH TO SUPPORT CUSTOM DSDTS[/COLOR]
                                                                        Thanks 67GTA for the answer.

I used kernel 2.6.28-12, applied dsdt in normal fashion, reboot and uses custom dsdt just fine, and also fixed all the ACPI errors above

---

### Post by CylnZ on 2009-05-25
Funnily enough, using the custom dsdt file fixed the ACPI errors from above and gave me 3 new ones to chase.
Ok, here's the answers I've found for all 3 current errors are  kernel bugs.

[COLOR=Red]ACPI Error (psargs-0358): [CDW1] Namespace lookup failure, AE_NOT_FOUND[/COLOR] 
& 
[COLOR=Red]ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC][/COLOR]



" In Ubuntu 9.04, ac is built in to the kernel (CONFIG_ACPI_AC=y), and the power manager was broken."
[http://ubuntuforums.org/showthread.php?t=1155641&page=2](http://ubuntuforums.org/showthread.php?t=1155641&page=2)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/366200](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/366200)

Other error
[COLOR=Red]"ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]"
[/COLOR]
[http://lkml.indiana.edu/hypermail/linux/kernel/0902.2/01600.html](http://lkml.indiana.edu/hypermail/linux/kernel/0902.2/01600.html)

"It means your BIOS returns an incorrect object from the ACPI _GTF method  which is used to figure out what ATA commands should be used to resume  the hard drive properly. In this case the kernel just doesn't send such  BIOS-provided commands. Usually these aren't necessary as the kernel  knows how to re-initialize the drive itself, so it's likely not a  serious problem."

Lol, I'm guessing that these will be fixed automatically as soon as the 2.6.29-02062903-generic kernel becomes stable/official and has the patch to allow custom dsdts. Hopefully that's real soon. 
Leaving me with no errors in dmesg a clean dsdt and all hardware working on my 6860fx. :)

---

