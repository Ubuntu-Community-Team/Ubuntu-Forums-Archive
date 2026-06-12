---
title: "Heat issue on HP Compaq nc6230"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by ig0tch4 on 2007-05-15
The fans of my laptop are always spinning. It wouldn't bother me at all if the temperature would stay below 45 C but it usually looks like that.
```
~ acpi -V
     Battery 1: charged, 97%
     Thermal 1: active[1], 65.0 degrees C
     Thermal 2: ok, 70.0 degrees C
     Thermal 3: ok, 34.0 degrees C
     Thermal 4: ok, 80.0 degrees C
  AC Adapter 1: on-line
```

The noise of the fans above 50 C are really annoying.
Here is also my top 10 processes and their cpu utilization.

```
%CPU   PID USER     COMMAND
 3.5 12006 dan      gnome-terminal
 2.0 12012 dan      bash
 1.5  5795 dan      /usr/lib/firefox/firefox-bin
 1.2  5114 root     /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 0.2  5568 dan      trackerd
 0.0     7 root     [kthread]
 0.0     6 root     [khelper]
 0.0  6013 cupsys   /usr/sbin/cupsd
 0.0     5 root     [events/0]
```

As you can see there is nothing really going on here. I can't make heads or tails of this.

I also looked into the ACPI table, but I couldn't find a solution for the warning or the error message on yahoo or google. I am not sure if the temperature problem is even related to this.

```
~ sudo cp /proc/acpi/dsdt .
~ sudo iasl -d dsdt
~ sudo iasl -sa dsdt.dsl 
dsdt.dsl  3232:                                         And (Local1, 0xFFFF)
Warning  1104 -        Result is not used, operator has no effect ^ 

dsdt.dsl  8079:                 CreateByteField (C1A0, \_SB.C002.C003._Y0F._LEN, C069)
Error    4062 -                                         Object does not exist ^  (\_SB.C002.C003._Y0F._LEN)
ASL Input:  dsdt.dsl - 8525 lines, 296677 bytes, 3985 keywords
Compilation complete. 1 Errors, 1 Warnings, 0 Remarks, 1193 Optimizations
```


```
~ dmesg |grep ACPI
[    0.000000]  BIOS-e820: 000000003ffefc00 - 000000003fffb000 (ACPI NVS)
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000fe270
[    0.000000] ACPI: RSDT (v001 HP     0944     0x27020720 HP   0x00000001) @ 0x3ffefc84
[    0.000000] ACPI: FADT (v002 HP     0944     0x00000002 HP   0x00000001) @ 0x3ffefc00
[    0.000000] ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x3ffefcb8
[    0.000000] ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x3ffefd14
[    0.000000] ACPI: SSDT (v001 HP       HPQPpc 0x00001001 MSFT 0x0100000e) @ 0x3fff81ff
[    0.000000] ACPI: DSDT (v001 HP       nc6200 0x00010000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   17.352874] ACPI: Core revision 20060707
[   17.353659] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.565708] ACPI: bus type pci registered
[   17.575180] ACPI: Interpreter enabled
[   17.575229] ACPI: Using IOAPIC for interrupt routing
[   17.575561] ACPI: PCI Root Bridge [C002] (0000:00)
[   17.575631] ACPI: Assume root bridge [\_SB_.C002] bus is 0
[   17.579634] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.580907] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[   17.609982] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C058._PRT]
[   17.610324] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[   17.611026] ACPI: Power Resource [C1D1] (on)
[   17.626300] ACPI: Power Resource [C1AA] (on)
[   17.627151] ACPI: Power Resource [C1B2] (on)
[   17.628251] ACPI: Power Resource [C1B9] (on)
[   17.628897] ACPI: Power Resource [C1C9] (on)
[   17.631292] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[   17.631705] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[   17.632743] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[   17.633393] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[   17.634032] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[   17.634672] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[   17.635314] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[   17.635955] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[   17.636599] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[   17.637129] ACPI Exception (pci_link-0180): AE_NOT_FOUND, Evaluating _PRS [20060707]
[   17.638821] ACPI: Power Resource [C251] (off)
[   17.638993] ACPI: Power Resource [C252] (off)
[   17.639165] ACPI: Power Resource [C253] (off)
[   17.639336] ACPI: Power Resource [C254] (off)
[   17.639691] pnp: PnP ACPI init
[   17.650146] pnp: PnP ACPI: found 15 devices
[   17.650197] PnPBIOS: Disabled by ACPI PNP
[   17.650275] PCI: Using ACPI for IRQ routing
[   17.753487] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.753605] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.753726] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   17.753856] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   18.786417] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 22 (level, low) -> IRQ 19
[   18.786520] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   18.821943] ACPI: (supports S0 S3 S4 S5)
[   20.087540] ACPI: Transitioning device [C255] to D3
[   20.087544] ACPI: Transitioning device [C255] to D3
[   20.087548] ACPI: Fan [C255] (off)
[   20.087738] ACPI: Transitioning device [C256] to D3
[   20.087740] ACPI: Transitioning device [C256] to D3
[   20.087743] ACPI: Fan [C256] (off)
[   20.087931] ACPI: Transitioning device [C257] to D3
[   20.087933] ACPI: Transitioning device [C257] to D3
[   20.087936] ACPI: Fan [C257] (off)
[   20.088123] ACPI: Transitioning device [C258] to D3
[   20.088125] ACPI: Transitioning device [C258] to D3
[   20.088128] ACPI: Fan [C258] (off)
[   20.099076] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.099081] ACPI: Processor [C000] (supports 8 throttling states)
[   20.157333] ACPI: Thermal Zone [TZ1] (37 C)
[   20.189725] ACPI: Thermal Zone [TZ2] (26 C)
[    3.124000] ACPI: Thermal Zone [TZ3] (19 C)
[    3.128000] ACPI: Thermal Zone [TZ4] (36 C)
[    3.532000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[    3.636000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[    3.740000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.844000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[    3.964000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.468000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.216000] ACPI: PCI Interrupt 0000:02:06.3[B] -> GSI 19 (level, low) -> IRQ 21
[   16.736000] ACPI: PCI Interrupt 0000:02:06.4[C] -> GSI 22 (level, low) -> IRQ 19
[   16.832000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 22
[   17.572000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 22
[   23.516000] ACPI: Video Device [C0FA] (multi-head: yes  rom: no  post: no)
[   23.648000] ACPI: Power Button (FF) [PWRF]
[   23.688000] ACPI: Sleep Button (CM) [C1F2]
[   23.732000] ACPI: Lid Switch [C1F3]
[   23.764000] ACPI: Battery Slot [C178] (battery present)
[   23.764000] ACPI: Battery Slot [C177] (battery absent)
[   23.772000] ACPI: AC Adapter [C176] (on-line)
[   29.280000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
```


I appreciate any help you can offer.

---

### Post by ig0tch4 on 2007-05-17
I found a solution for the dsdt error messages. For the first message I added another parameter, from
```
And (Local1, 0xFFFF)
```
to 
```
And (Local1, 0xFFFF, Local1)
```
and for the other message I looked for the device name a few lines above. The device name was
```
Device (\_SB.C002.C003.C276)
```
so I changed
```
CreateByteField (C1A0, \_SB.C002.C003._Y0F._LEN, C069)
```
to
```
CreateByteField (C1A0, \_SB.C002.C003.C276._Y0F._LEN, C069)
```
and the error messages were gone.
I must say, I don't have a clue if this is correct, but my laptop works fine thus far.

Additionally I set the CPU governor to "conservative" and the ATI graphics card to the lower frequency setting. This keeps the fans from being to noisy.

---

