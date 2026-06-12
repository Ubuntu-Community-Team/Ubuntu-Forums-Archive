---
title: "Battery Status Not Being Reported (64-bit)"
date: 2008-07-14
forum: Hardware
---

### Post by ve4cib on 2008-07-14
Hello, all. The last couple days I've run into an odd bug on one of my Ubuntu-equipped laptops. Starting Saturday afternoon when I booted it up gnome-power-manager and Conky both report my battery as having 0% charge. The hardware light indicates that it is not charging, but when I unplug the AC adaptor the brightness dims, my CPU downclocks, and I'm running on the battery. I just have no indication of how much power there is.

I've googled all over the place trying to figure out what's going on. The closest I came was something about CONFIG_ACPI_PROCFS_POWER needing to be enabled in some of the later kernels, but not being an OS guy I don't quite understand what that means, or how to enable it. I've found similar bugs for Macs, but they were for older kernels, and the reported fixes had no effect on my situation.

I have tried using different boot options, and I've booted with several different kernels, all with the same result. Some system information is behind the cut.


I'm running Hardy x86_64 with all the updates. It's not a clean installation; I upgraded from Gutsy using the Alternate Install CD. The computer itself is an HP Pavillion dv6308ca with a dual-core AMD Turion 64.


$uname -r
2.6.24-19-generic


~$ dmesg|grep -i 'acpi\|BAT\|power'
[ 0.000000] Command line: root=UUID=48771a69-09f5-44e1-846d-60a9d3afb53d ro quiet nosplash noapic acpi_irq_balance
[ 0.000000] BIOS-e820: 0000000037f00000 - 0000000037f17000 (ACPI data)
[ 0.000000] BIOS-e820: 0000000037f17000 - 0000000037f80000 (ACPI NVS)
[ 0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8930 checksum 0
[ 0.000000] ACPI: RSDP 000F8930, 0014 (r0 HP )
[ 0.000000] ACPI: RSDT 37F0DD1B, 0040 (r1 HPQOEM SLIC-MPC 6040000 LTP 0)
[ 0.000000] ACPI: FACP 37F16B9A, 0074 (r1 HP MCP51M 6040000 PTL_ F4240)
[ 0.000000] ACPI: DSDT 37F0DD5B, 8E3F (r1 HP MCP51M 6040000 MSFT 3000000)
[ 0.000000] ACPI: FACS 37F17FC0, 0040
[ 0.000000] ACPI: SSDT 37F16C0E, 0182 (r1 HP POWERNOW 6040000 LTP 1)
[ 0.000000] ACPI: MCFG 37F16D90, 003C (r1 HP MCFG 6040000 LTP 0)
[ 0.000000] ACPI: HPET 37F16DCC, 0038 (r1 PTLTD HPETTBL 6040000 LTP 1)
[ 0.000000] ACPI: APIC 37F16E04, 005E (r1 HP APIC 6040000 LTP 0)
[ 0.000000] ACPI: BOOT 37F16E62, 0028 (r1 HP $SBFTBL$ 6040000 LTP 1)
[ 0.000000] ACPI: SLIC 37F16E8A, 0176 (r1 HPQOEM SLIC-MPC 6040000 LTP 1)
[ 0.000000] ACPI: DMI detected: Hewlett-Packard
[ 0.000000] DMA zone: 2721 pages, LIFO batch:0
[ 0.000000] DMA32 zone: 221948 pages, LIFO batch:31
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[ 0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[ 0.000000] Using ACPI for processor (LAPIC) configuration information
[ 0.000000] Kernel command line: root=UUID=48771a69-09f5-44e1-846d-60a9d3afb53d ro quiet nosplash noapic acpi_irq_balance
[ 14.295145] ACPI: Core revision 20070126
[ 14.295241] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 14.297985] ACPI: setting ELCR to 0200 (from 0ca0)
[ 14.595319] ACPI: bus type pci registered
[ 14.596616] ACPI: EC: Look up EC in DSDT
[ 14.598797] ACPI: BIOS _OSI(Linux) query ignored via DMI
[ 14.599063] ACPI: Interpreter enabled
[ 14.599066] ACPI: (supports S0 S3 S4 S5)
[ 14.599083] ACPI: Using PIC for interrupt routing
[ 14.600257] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 14.607353] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[ 14.607357] ACPI: EC: driver started in interrupt mode
[ 14.607438] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 14.608791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 14.608908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[ 14.608944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[ 14.608984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[ 14.647996] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.648192] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[ 14.648385] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[ 14.648574] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.648765] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.648955] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.649147] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[ 14.649336] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.649528] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[ 14.649719] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[ 14.649910] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[ 14.650121] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[ 14.650311] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[ 14.650500] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.650690] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.650884] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.651073] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[ 14.651272] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[ 14.651462] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15)
[ 14.651684] pnp: PnP ACPI init
[ 14.651696] ACPI: bus type pnp registered
[ 14.654925] pnp: PnP ACPI: found 13 devices
[ 14.654929] ACPI: ACPI bus type pnp unregistered
[ 14.655214] PCI: Using ACPI for IRQ routing
[ 16.198358] ACPI: Thermal Zone [THRM] (65 C)
[ 16.742180] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[ 16.742189] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[ 16.891343] libata version 3.00 loaded.
[ 16.902633] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 10
[ 16.902643] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 10 (level, low) -> IRQ 10
[ 16.962653] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[ 16.962657] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[ 16.966064] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 10
[ 16.966070] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 10 (level, low) -> IRQ 10
[ 17.083045] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 9
[ 17.083053] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 9 (level, low) -> IRQ 9
[ 17.888813] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[ 17.888817] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[ 32.653811] input: Power Button (FF) as /devices/virtual/input/input2
[ 32.751704] ACPI: Power Button (FF) [PWRF]
[ 32.751776] input: Power Button (CM) as /devices/virtual/input/input3
[ 33.055304] ACPI: Power Button (CM) [PWRB]
[ 33.119242] ACPI: Sleep Button (CM) [SLPB]
[ 33.151581] ACPI: Lid Switch [LID]
[ 33.152116] ACPI: AC Adapter [ACAD] (on-line)
[ 33.278381] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 11
[ 33.278386] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 11 (level, low) -> IRQ 11
**[ 33.411547] ACPI: Battery Slot [BAT0] (battery present)**
[ 33.411700] ACPI: WMI-Acer: Mapper loaded
[ 33.583609] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 9
[ 33.583612] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 9 (level, low) -> IRQ 9
[ 33.727164] ACPI: Video Device [UVGA] (multi-head: yes rom: no post: no)
[ 33.775189] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
[ 34.731251] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[ 34.731256] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[ 41.963146] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[ 41.962746] powernow-k8: 0 : fid 0x8 (1600 MHz), vid 0x12
[ 41.962750] powernow-k8: 1 : fid 0x0 (800 MHz), vid 0x1e


$ ls /proc/acpi/battery/
BAT0


$ cat /proc/acpi/battery/BAT0/*
alarm: unsupported
present: yes
design capacity: 6000 mAh
last full capacity: unknown
battery technology: rechargeable
design voltage: 14800 mV
design capacity warning: 250 mAh
design capacity low: 150 mAh
capacity granularity 1: 10 mAh
capacity granularity 2: 25 mAh
model number: Primary
serial number:
battery type: LION
OEM info: Hewlett-Packard
present: yes
capacity state: ok
charging state: charged
present rate: unknown
remaining capacity: unknown
present voltage: 12228 mV


$ acpi -V with AC plugged in
Thermal 1: ok, 53.0 degrees C
AC Adapter 1: on-line


$ acpi -V with AC unplugged
Thermal 1: ok, 52.0 degrees C
AC Adapter 1: off-line



I've tried booting with the following kernels:
2.6.24-19, -18, -17, and -16



My best guess as to why Conky and GPM aren't getting the battery right is because ACPI isn't reporting anything about the battery.  It's not even telling me that it's unsupported; it's just skipping the battery.  $acpi -b simply returns nothing at all.

dmesg reports that the battery is present, and everything behaves properly when the AC is plugged in/removed; /proc/acpi/battery/BAT0/state reports that the battery is charging/discharging/charged, etc...

My other laptop is a slightly older 32-bit Toshiba, running the 32-bit version of Hardy with all the updates, working from a clean install, and everything is fine.  Because this bug only just popped up I don't think it has anything to do with upgrade versus clean install.  I'm thinking it might have been a HAL-related or kernel update, but I'm just guessing.

If anyone has any suggestions please feel free to speak up.  If I don't get any help within a few days I'll probably go and log a bug report.  Thanks a lot for the help!

---

