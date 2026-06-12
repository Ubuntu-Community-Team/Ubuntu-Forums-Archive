---
title: "Dell 6000 idles hot, overheats under any load"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by vayu on 2006-07-03
My laptop is frying with Dapper.  It always ran about 4c higher on Breezy than windows but now it's out of control.  In Windows it idles at about 40c in Dapper 50c.  When I play the same DVD in windows it runs 46c, in Dapper 66-72c.  GL screensavers will get it to 90c.  The fan is always on high, even when idling.

Please point me in the direction to fix, I am stuck. I don't know much about ACPI but it seems like ACPI is on. Here's all that I know what to show:

~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

There are a lot of entries from dmesg.  There is only one that looks like an error to me:
[17179573.984000] ACPI: Looking for DSDT ... not found!


~$ dmesg | grep ACPI
```
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc9b0
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d50503 ASL  0x00000061) @ 0x1ffd3fd3
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d50503 ASL  0x00000061) @ 0x1ffd4c00
[17179569.184000] ACPI: MADT (v001 DELL    CPi R   0x27d50503 ASL  0x00000047) @ 0x1ffd5400
[17179569.184000] ACPI: MCFG (v016 DELL    CPi R   0x27d50503 ASL  0x00000061) @ 0x1ffd53c0
[17179569.184000] ACPI: BOOT (v001 DELL    CPi R   0x27d50503 ASL  0x00000061) @ 0x1ffd4fc0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1ffd43e6
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1ffd420e
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1ffd4013
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
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
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179573.984000] ACPI: Looking for DSDT ... not found!
[17179574.132000] ACPI: bus type pci registered
[17179574.148000] ACPI: Subsystem revision 20051216
[17179574.172000] ACPI: Interpreter enabled
[17179574.172000] ACPI: Using IOAPIC for interrupt routing
[17179574.172000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.172000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.184000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179574.188000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.204000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179574.204000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[17179574.204000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179574.204000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[17179574.208000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.208000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.208000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179574.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179574.208000] pnp: PnP ACPI init
[17179574.228000] pnp: PnP ACPI: found 10 devices
[17179574.228000] PnPBIOS: Disabled by ACPI PNP
[17179574.228000] PCI: Using ACPI for IRQ routing
[17179574.268000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.268000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179574.268000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.688000] ACPI wakeup devices:
[17179574.688000] ACPI: (supports S0 S3 S4 S5)
[17179575.832000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179575.832000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.836000] ACPI: Thermal Zone [THM] (56 C)
[17179576.144000] ACPI: bus type scsi registered
[17179576.144000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
[17179576.144000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17179576.144000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
[17179577.620000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179577.724000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 201
[17179577.828000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179577.932000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179578.036000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
[17179578.144000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 209
[17179595.724000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179595.864000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 169
[17179596.684000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179596.692000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179597.100000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 201
[17179601.988000] ACPI: AC Adapter [AC] (on-line)
[17179602.264000] ACPI: Battery Slot [BAT0] (battery present)
[17179602.332000] ACPI: Lid Switch [LID]
[17179602.332000] ACPI: Power Button (CM) [PBTN]
[17179602.332000] ACPI: Sleep Button (CM) [SBTN]
[17179602.516000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179602.516000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179602.516000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179611.420000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
```

---

### Post by Patrick-Ruff on 2006-07-03
wow, thats bloody insane! I have the same laptop by the way, but mine doesn't even touch those temp's idling. hell, it doesn't touch those temps idling with XGL/Compiz on dapper.


perhaps your CPU isant scaling?

also, heres my specs just for reference

1.6GHz Pentium M
512MB DDR2 RAM
ATI Mobility Radeon X300 PCI Express 64MB
40GB HD
6cell Lion battery


mine only gets around 40c when I move the desktop around in XGL/Compiz (which is very very very video-based and is insanely 3d)

what are the specs?

---

### Post by gmertr on 2006-07-03
Try cleaning out the vents. My laptop was shutting down due to over heating. I vacumed as much dust as I could, then, took a leaf blower, and blew the rest of it out. Worked for me.

---

### Post by vayu on 2006-07-03
[QUOTE=Patrick-Ruff]wow, thats bloody insane! I have the same laptop by the way, but mine doesn't even touch those temp's idling. hell, it doesn't touch those temps idling with XGL/Compiz on dapper.


perhaps your CPU isant scaling?

also, heres my specs just for reference

1.6GHz Pentium M
512MB DDR2 RAM
ATI Mobility Radeon X300 PCI Express 64MB
40GB HD
6cell Lion battery


mine only gets around 40c when I move the desktop around in XGL/Compiz (which is very very very video-based and is insanely 3d)

what are the specs?[/QUOTE]


Exact same except 60GB HD.  Which kernel version are you running?



[QUOTE=gmertr]Try cleaning out the vents. My laptop was shutting down due to over heating. I vacumed as much dust as I could, then, took a leaf blower, and blew the rest of it out. Worked for me.[/QUOTE]

I am planning on doing that, I just bought air in a can type stuff, but It still doesn't make sense because Windows runs so much cooler.

---

### Post by vayu on 2006-07-04
[QUOTE=Patrick-Ruff]
also, heres my specs just for reference

1.6GHz Pentium M
512MB DDR2 RAM
ATI Mobility Radeon X300 PCI Express 64MB
40GB HD
6cell Lion battery


mine only gets around 40c when I move the desktop around in XGL/Compiz (which is very very very video-based and is insanely 3d)

what are the specs?[/QUOTE]

Patrick, what version is your BIOS?  I'm wondering if there could be something with the way the latest kernel interacts with the bios.

---

### Post by Hellkeepa on 2006-07-04
HELLo!

I also recommend you to read the following thread, sounds very much like the same issue as discussed in there.
[http://ubuntuforums.org/showthread.php?p=1183935#post1183935](http://ubuntuforums.org/showthread.php?p=1183935#post1183935)

Happy codin'!

---

### Post by insanedc on 2006-07-04
Do a search on ACPI, DSDT and Linux. Dell BIOS have faulty ACPI implementation. My Inspiron 8600 had similar issues. Replacing the DSDT should address the issue.

---

