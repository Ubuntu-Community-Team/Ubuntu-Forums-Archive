---
title: "Can not modprobe coretemp in 8.04-64-Bit"
date: 2008-06-04
forum: Hardware
---

### Post by Thyrus on 2008-06-04
I have a problem inserting the module "coretemp" into the running kernel on Ubuntu 8.04 64-bit. The module seems to be there:

```
chris@laptop:/lib/modules/2.6.24-17-generic/kernel/drivers/hwmon$ locate coretemp
/lib/modules/2.6.24-16-generic/kernel/drivers/hwmon/coretemp.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/hwmon/coretemp.ko
/usr/src/linux-headers-2.6.24-16-generic/include/config/sensors/coretemp.h
/usr/src/linux-headers-2.6.24-17-generic/include/config/sensors/coretemp.h

```

But when I try to load the module I get the following:
```
FATAL: Error inserting coretemp (/lib/modules/2.6.24-17-generic/kernel/drivers/hwmon/coretemp.ko): No such device

```

the content of /proc/cpuinfo is:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
stepping	: 6
cpu MHz		: 2501.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips	: 4993.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
stepping	: 6
cpu MHz		: 2501.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips	: 4987.50
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

and lspci (for the chipset) gives:
```
chris@laptop:/lib/modules/2.6.24-17-generic/kernel/drivers/hwmon$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
14:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
1c:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

```

this prevents me from using lm_sensors and the content of /proc/acpi/thermal_zone is completely useless

Any Ideas?

---

### Post by sdennie on 2008-06-04
I believe that when you get that error message from a modprobe it means you don't have hardware that supports that module.  If /proc/acpi/thermal_zone isn't giving you reasonable information, you may want to look for a bios update for your laptop.

---

### Post by Thyrus on 2008-06-04
A friend of mine uses Gentoo on the same machine also with 2.6.24-64-bit and he gets sensible information out of lm-sensors using coretemp

---

