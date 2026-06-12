---
title: "Toshiba A105-S4011"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by Titan_Prometheus on 2006-09-01
... As Stated above, I have a toshiba A105-S4011 And have Ubuntu Installed on it. When switching to battery I only get 2 hours instead of the normal 3:30 in windows. This is because I can't lower my screen brightness with the Fn keys on my board. I have tashutils and such, but when i try to run  it, it tells me I need kerenel support of Toshiba. I Know it's modular, so I proceed to put it in such that modprobe toshiba or modprobe toshiba_acpi, but it gives me an error, even though i know those are the commands and proper modules. Short of trying to recompile the kernel, can anyone else help me?

---

### Post by wasteed on 2006-09-01
Maybe this applies to your laptop :

[http://www.ubuntuforums.org/showthread.php?t=148797#6](http://www.ubuntuforums.org/showthread.php?t=148797#6)

---

### Post by Titan_Prometheus on 2006-09-01
No, I've tried all those programs, but unfortinuatly I have come to the decision to just recompile, because it seems that the ACPI for my kernel just got left out for configing. Thanks anyways.

---

### Post by wasteed on 2006-09-01
Not sure I follow why your modules aren't being picked up and loaded then.
On my Toshiba Tecra, after a Dapper live-CD desktop install, and subsequently updated with the latest kernel etc,  all the toshiba modules get loaded automatically at boot time - I've never had to load them manually using modprobe. Also, the Fn keys just work for me - a consequence of a working ACPI, I guess.

What messages do you see about ACPI at boot-time? For example, what does
dmesg | grep -i acpi
say? Or is there anything ACPI related in the system log files?

---

### Post by Titan_Prometheus on 2006-09-01
#dmesg | grep -i acpi

[17179569.184000]  BIOS-e820: 000000001f670000 - 000000001f687000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f687000 - 000000001f700000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f64c0
[17179569.184000] ACPI: RSDT (v001 TOSINV Capell00 0x06040000  LTP 0x00000000) @ 0x1f67f2b5
[17179569.184000] ACPI: FADT (v001 TOSINV CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f686dfc
[17179569.184000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f686e70
[17179569.184000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f686ed8
[17179569.184000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f686f10
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f686fd8
[17179569.184000] ACPI: MADT (v001 TOSINV   APIC   0x06040000  LTP 0x00000000) @ 0x1f686f7e
[17179569.184000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x1f680211
[17179569.184000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x1f67fb7f
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20050624) @ 0x1f67f9d7
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f67f7fb
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f67f305
[17179569.184000] ACPI: DSDT (v001 TOSINV CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.888000] ACPI: Looking for DSDT ... not found!
[17179570.100000] ACPI: bus type pci registered
[17179570.100000] ACPI: Subsystem revision 20051216
[17179570.108000] ACPI: Interpreter enabled
[17179570.108000] ACPI: Using IOAPIC for interrupt routing
[17179570.108000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.200000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.364000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.364000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.364000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.364000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.396000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.396000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.396000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.396000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.396000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.396000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.396000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.396000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.396000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179570.464000] ACPI: Power Resource [FN00] (off)
[17179570.464000] pnp: PnP ACPI init
[17179570.560000] pnp: PnP ACPI: found 11 devices
[17179570.560000] PnPBIOS: Disabled by ACPI PNP
[17179570.560000] PCI: Using ACPI for IRQ routing
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.588000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.588000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.008000] ACPI wakeup devices:
[17179571.008000] ACPI: (supports S0 S3 S4 S5)
[17179572.280000] ACPI: Fan [FAN0] (off)
[17179572.284000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.284000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.284000] ACPI: Thermal Zone [TZ00] (37 C)
[17179572.288000] ACPI: Thermal Zone [TZ01] (35 C)
[17179572.700000] ACPI: bus type scsi registered
[17179572.700000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179572.872000] ata_acpi_push_id: skipping for PATA mode
[17179573.200000] ata_acpi_push_id: skipping for PATA mode
[17179573.640000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179573.744000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179573.848000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179573.952000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179574.064000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179574.172000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 169
[17179586.408000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 50
[17179587.356000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 185
[17179587.384000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179587.456000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179587.688000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179595.720000] ACPI: AC Adapter [ADP0] (on-line)
[17179595.724000] ACPI: Battery Slot [BAT0] (battery present)
[17179595.796000] ACPI: Power Button (FF) [PWRF]
[17179595.796000] ACPI: Lid Switch [LID]
[17179595.796000] ACPI: Power Button (CM) [PWRB]
[17179595.948000] ibm_acpi: ec object not found
[17179595.976000] pcc_acpi: loading...
[17179596.056000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179596.056000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179601.032000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177


~# modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.15-26-686/kernel/drivers/char/toshiba.ko): No such device
~#

~# modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-26-686/kernel/drivers/acpi/toshiba_acpi.ko): No such device
~#

~# lsmod | grep acpi
sony_acpi               5580  0
pcc_acpi               12416  0
dev_acpi               11236  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
~# lsmod | grep toshiba
~#


That's it. But I'm recompiling as we speak, hoping it will work, if not, any more advice?

---

### Post by Titan_Prometheus on 2006-09-01
Hold The Phone. 
~# dmesg | grep -i tosh
[17179586.344000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[17186620.976000] toshiba: not a supported Toshiba laptop
~#

---

### Post by Titan_Prometheus on 2006-09-01
I've just been informed I can't use the "Git" Source because security updates won't apply, and the current kernel it seems does not support my Laptop, any other recommendations?

---

### Post by Titan_Prometheus on 2006-09-01
I recompiled with the 2.6.15 kernel and i got jack. It's keeps saying My laptop is not supported.

---

### Post by mdmarmer on 2006-09-02
Most of these programs are written for Toshibas which have Toshiba BIOS --
newer Toshibas like yours have Phoenix BIOS, these programs don't work --
try this one

[http://tz.exit0.net/tecras1.html](http://tz.exit0.net/tecras1.html)

Also look here

[http://www.tuxmobile.com/toshiba.html](http://www.tuxmobile.com/toshiba.html)
[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)
[https://wiki.ubuntu.com/HardwareSupp...LaptopsToshiba](https://wiki.ubuntu.com/HardwareSupp...LaptopsToshiba)

Mike

---

### Post by Titan_Prometheus on 2006-09-03
Still not doing it. I tried that, but it stuck to only brightness level 0, and wouldn't move. I Don't know what to do, my BIOS type is listed as tosinv, I just really think it's the ACPI support. Maybe it's because of the generic ACPI loaded in, is their any way to sub in toshiba_Acpi inplace of regular ACPI?

---

### Post by Titan_Prometheus on 2006-09-04
Honestly I think i'm going to just give up. If I can't turn the battery down I lose so much battery life that it's almost not worth the reason I got the processor. Thanks for all the help.

---

### Post by Titan_Prometheus on 2006-09-05
root@Cerberus:/proc/acpi/video/GFX0/LCD# sudo echo current 80 > brightness
echo: write error: Invalid argument


I've learned that in this file their is a setting

levels: 80 60 0 20 40 60 80 100
current: 0

but i can't mod the file. Any help?

---

### Post by jtibau on 2007-01-11
how about picking this thread up. I have an A105-S4014 and am interested in learning how to dim the screen too.

---

### Post by Titan_Prometheus on 2007-04-18
Sorry It took me so long. I've been using ubuntu in VMware for the longest while, but now I have a full install because of beryl. The problem is slightly solved, in that updating to feisty allows for a little modification of the brightness, but not as smooth or complete as in windows. Anyone know of any other solutions?

---

