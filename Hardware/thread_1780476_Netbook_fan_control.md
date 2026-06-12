---
title: "Netbook fan control"
date: 2011-06-12
forum: Hardware
---

### Post by mikewhatever on 2011-06-12
A relative of mine has a brandless netbook which works well with Ubuntu 10.04. The only 'problem' is the fan that drones constantly and never stops. We've installed lm-sensors, and run sensors-detect as root, but it didn't detect anything other then coretemp, which seems to be the cpu temperature.
/proc/acpi/fan is empty, and we've tried acpi_enforce_resources=lax and acpi_osi=Linux boot options that produced no effect. ACPI functions such as CPU stepping, suspending, screen dimming, etc all work. The BIOS has nothing related to fan control.

Does anyone know how to control the fan?

Edit1:
Here is a relatively comprehensive explanation -> [http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)
The problem is, 'sudo pwmconfig' finds no fan sensors.

Edit2:
Thinkfan seems to be an alternative option.
[http://thinkfan.sourceforge.net/](http://thinkfan.sourceforge.net/)

The README suggests the following command which find nothing.
```
find -L /sys/class/hwmon -maxdepth 3 -name "pwm?"         -print -exec cat \{\} \; 2>/dev/null
```


Some more info:
```

sudo lshw

description: Desktop Computer
    product: czc
    vendor: czc
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: czc
       vendor: czc
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080016 (03/16/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10

```

```
dmesg | grep ACPI

[    0.000000]  BIOS-e820: 000000007f580000 - 000000007f58e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f58e000 - 000000007f5d0000 (ACPI NVS)
[    0.000000]  modified: 000000007f580000 - 000000007f58e000 (ACPI data)
[    0.000000]  modified: 000000007f58e000 - 000000007f5d0000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f9ac0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7f580000 00048 (v01 NEC             20100316 MSFT 00000097)
[    0.000000] ACPI: FACP 7f580200 00084 (v01 031610 FACP1924 20100316 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f5805c0 05075 (v01  1AEME PA00R014 00000008 INTL 20051117)
[    0.000000] ACPI: FACS 7f58e000 00040
[    0.000000] ACPI: APIC 7f580390 0006C (v01 031610 APIC1924 20100316 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f580400 0003C (v01 031610 OEMMCFG  20100316 MSFT 00000097)
[    0.000000] ACPI: SLIC 7f580440 00176 (v01 NEC             20100316 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f58e040 00083 (v01 031610 OEMB1924 20100316 MSFT 00000097)
[    0.000000] ACPI: HPET 7f58a5c0 00038 (v01 031610 OEMHPET  20100316 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f58e0d0 02024 (v01 031610 GMCHSCI  20100316 MSFT 00000097)
[    0.000000] ACPI: NVOP 7f590100 10024 (v01 031610 GMCHSCI  20100316 MSFT 00000097)
[    0.000000] ACPI: SSDT 7f5a0a30 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] ACPI: Added _OSI(Linux)
[    0.024222] ACPI: Core revision 20090903
[    0.184692] ACPI: bus type pci registered
[    0.191929] ACPI: EC: Look up EC in DSDT
[    0.194783] ACPI Error: No handler for Region [ECOR] (f7015cd0) [EmbeddedControl] (20090903/evregion-319)
[    0.194803] ACPI Error: Region EmbeddedControl(3) has no handler (20090903/exfldio-295)
[    0.194821] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._REG] (Node f7016450), AE_NOT_EXIST
[    0.195778] ACPI: Executed 1 blocks of module-level executable AML code
[    0.206791] ACPI: Interpreter enabled
[    0.206791] ACPI: (supports S0 S3 S4 S5)
[    0.206791] ACPI: Using IOAPIC for interrupt routing
[    0.213012] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.230531] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.231578] ACPI Warning: Incorrect checksum in table [GSCI] - 90, should be 49 (20090903/tbutils-314)
[    0.238228] ACPI: No dock devices found.
[    0.240177] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.243371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.243690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.243966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.277338] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.277627] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.277903] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.278174] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.278452] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.280126] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.280403] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.280679] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.282411] ACPI: WMI: Mapper loaded
[    0.282417] PCI: Using ACPI for IRQ routing
[    0.292839] pnp: PnP ACPI init
[    0.292877] ACPI: bus type pnp registered
[    0.300342] pnp: PnP ACPI: found 15 devices
[    0.300350] ACPI: ACPI bus type pnp unregistered
[    0.300360] PnPBIOS: Disabled by ACPI PNP
[    0.377683] ACPI: AC Adapter [AC] (on-line)
[    0.378520] ACPI: Lid Switch [LID0]
[    0.378787] ACPI: Sleep Button [SLPB]
[    0.379034] ACPI: Power Button [PWRB]
[    0.379275] ACPI: Power Button [PWRF]
[    0.380912] ACPI: SSDT 7f5a0200 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.382024] ACPI: SSDT 7f5a0490 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.392606] ACPI: SSDT 7f5a0130 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.393405] ACPI: SSDT 7f5a0400 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.406464] ACPI: Thermal Zone [TZ01] (39 C)
[    0.748637] ACPI: Battery Slot [BAT0] (battery present)
[   12.401463] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

```

```
cat /proc/acpi/thermal_zone/*/trip_points

critical (S5):           94 C
passive:                 84 C: tc1=4 tc2=3 tsp=150 devices=CPU0 

```

---

### Post by yesterfox on 2012-02-16
i have same problem.
i think problem is with bios. by the way we have same motherboard and bios infos.

---

### Post by mikewhatever on 2012-02-17
Interesting. What's your netbook model?

I am gonna be testing it with the latest build of Precise soon.

---

