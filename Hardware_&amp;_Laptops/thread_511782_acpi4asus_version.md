---
title: "acpi4asus version"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by codedmin on 2007-07-28
Hy there, how can i update acpi4asus version ? latest stable version is 0.40

I have gutsy in my laptop and version is 0.30

Why so old?

I have one asus W6A, this model enter in 0.32 version, but only have 0.30 :( don't have bluetooth active and don't know how to do it...

Thanks

---

### Post by Bachstelze on 2007-07-28
Did you load the *asus-acpi* module ? If so, it's normal, the new one is *asus-laptop*.

---

### Post by codedmin on 2007-07-28
I don't load none! ubuntu load automatically asus-acpi
I have this 

~$ lsmod | grep acpi
acpi_cpufreq           10568  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
asus_acpi              17308  0 
processor              31944  2 acpi_cpufreq,thermal

When i try load asus-laptop get one error
~$ sudo modprobe asus-laptop 
FATAL: Error inserting asus_laptop (/lib/modules/2.6.22-8-generic/kernel/drivers/misc/asus-laptop.ko): No such device

Can you help ?

---

### Post by codedmin on 2007-07-28
Please i really need this :S

---

### Post by Bachstelze on 2007-07-28
Before you load asus-laptop, you need to unload asus-acpi :

```
sudo modprobe -r asus-acpi
sudo modprobe asus-laptop
```

---

### Post by codedmin on 2007-07-29
Thanks that worked.

But i must do that everytime i reboot. How can remove asus_acpi from auto load?

Thanks

---

### Post by codedmin on 2007-08-02
Anyone can help?

Thanks

---

### Post by cemelmaci on 2007-11-22
hi i have same problem,
```
sc@sc-laptop:~$ modinfo asus-laptop
filename:       /lib/modules/2.6.22-14-generic/acpi/asus-laptop.ko
license:        GPL
description:    Asus Laptop Support
author:         Julien Lerouge, Karol Kozimor, Corentin Chary
srcversion:     1C8ACA4F4E5C188FAB9AA29
depends:        led-class
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           wapf:WAPF value (uint)
sc@sc-laptop:~$ sudo modprobe -r asus-acpi
sc@sc-laptop:~$ sudo modprobe asus-laptop
FATAL: Error inserting asus_laptop (/lib/modules/2.6.22-14-generic/acpi/asus-laptop.ko): No such device
sc@sc-laptop:~$ lsmod |grep acpi
acpi_cpufreq           10568  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              32072  2 acpi_cpufreq,thermal

```

```
~$ dmesg |grep ACPI
[    0.000000]  BIOS-e820: 000000007fe8a000 - 000000007febf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007febf000 - 000000007ff00000 (ACPI data)
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 NEC   )
[    0.000000] ACPI: RSDT 7FEFE038, 0034 (r1 NEC    H2O             1       1000013)
[    0.000000] ACPI: FACP 7FEFD000, 0074 (r1 NEC    H2O             1 MSFT  1000013)
[    0.000000] ACPI: DSDT 7FEF8000, 4CDB (r1 NEC    H2O             1 MSFT  1000013)
[    0.000000] ACPI: FACS 7FE8A000, 0040
[    0.000000] ACPI: SSDT 7FEF7000, 0210 (r1 NEC    H2O             1 MSFT  1000013)
[    0.000000] ACPI: APIC 7FEF6000, 0068 (r1 NEC    H2O             1 MSFT  1000013)
[    0.000000] ACPI: MCFG 7FEF4000, 003C (r1 NEC    H2O             1 MSFT  1000013)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   25.693941] ACPI: Core revision 20070126
[   25.693982] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.314221] ACPI: bus type pci registered
[   26.317869] ACPI: EC: Look up EC in DSDT
[   26.318959] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   26.319757] ACPI: Interpreter enabled
[   26.319760] ACPI: (supports S0 S1 S3 S4 S5)
[   26.319777] ACPI: Using IOAPIC for interrupt routing
[   26.326137] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   26.326178] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.326908] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   26.328245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.328462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   26.328536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   26.328645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   26.328746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   26.328846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   26.328946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[   26.331170] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12)
[   26.331257] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   26.331342] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   26.331426] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   26.331510] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[   26.331595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   26.331680] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   26.331764] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   26.331870] pnp: PnP ACPI init
[   26.331876] ACPI: bus type pnp registered
[   26.334152] pnp: PnP ACPI: found 8 devices
[   26.334154] ACPI: ACPI bus type pnp unregistered
[   26.334158] PnPBIOS: Disabled by ACPI PNP
[   26.334194] PCI: Using ACPI for IRQ routing
[   26.364722] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.364748] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.364777] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   26.364805] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.364833] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   27.553692] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   27.553701] ACPI: Processor [CPU0] (supports 8 throttling states)
[   27.554973] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   27.554977] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.292000] ACPI: PCI Interrupt 0000:09:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[    2.320000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.396000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    3.256000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[    3.364000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.468000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[    3.572000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.676000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   13.660000] ACPI: PCI Interrupt 0000:09:02.2[A] -> GSI 16 (level, low) -> IRQ 16
[   13.956000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.200000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 23 (level, low) -> IRQ 21
[   19.004000] ACPI: Battery Slot [BAT0] (battery present)
[   19.148000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[   19.204000] ACPI: AC Adapter [AC] (on-line)
[   19.276000] ACPI: Power Button (FF) [PWRF]
[   19.276000] ACPI: Power Button (CM) [PWRB]
[   19.276000] ACPI: Lid Switch [LID]
[   19.276000] ACPI: Sleep Button (CM) [SLPB]
[   25.968000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

```

any ideas?

---

### Post by suoko on 2007-11-28
put asus-laptop into /etc/modules and remove asus-acpi

---

### Post by cemelmaci on 2007-12-08
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
asus-laptop
tun

---

### Post by devillious on 2007-12-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/150091/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/150091/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Codedmin:
You need to blacklist the old asus_acpi module:
```
sudo nano /etc/modprobe.d/blacklist
```
and then add this line:
```
blacklist asus_acpi
```

cemelmaci:
To remove asus_acpi when it's already loaded you must:
```
sudo modprobe -r asus_acpi
```
Please notice the underscore.
The old module is called asus_acpi (underscore), while the new one is asus-laptop (minus sign).

---

### Post by cemelmaci on 2008-01-10
```
sc@sc-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for sc:
sc@sc-laptop:~$ sudo modprobe -r asus_acpi
sc@sc-laptop:~$ sudo modprobe asus-laptop
FATAL: Error inserting asus_laptop (/lib/modules/2.6.22-14-generic/acpi/asus-laptop.ko): No such device

```

---

