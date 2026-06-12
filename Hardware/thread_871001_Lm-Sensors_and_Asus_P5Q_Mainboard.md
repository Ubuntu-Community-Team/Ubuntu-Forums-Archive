---
title: "Lm-Sensors and Asus P5Q Mainboard"
date: 2008-07-26
forum: Hardware
---

### Post by NineseveN on 2008-07-26
So I'm trying to get LM-sensors running on my Asus P5Q. I read over at Phoronix that the latest legacy release of LM-sensors and LM-sensors 3 recognize the chip on this mobo (Intel ICH10R). The lm-sensors in the repositories won't work, it's not new enough. So I got Lm-sensors 3 installed all fine and ran sensors-detect. But at the end, it's supposed to give me the information that I need to put into modules, but for some reason, mine doesn't, it stops after telling me what sensors-detect found (and lists one as "to-be-written"?).

```
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `to-be-written')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xa513
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.
```

Any thoughts/help?

---

### Post by mgc8 on 2008-08-06
> **NineseveN said:**
> So I'm trying to get LM-sensors running on my Asus P5Q. I read over at Phoronix that the latest legacy release of LM-sensors and LM-sensors 3 recognize the chip on this mobo (Intel ICH10R). The lm-sensors in the repositories won't work, it's not new enough. So I got Lm-sensors 3 installed all fine and ran sensors-detect. But at the end, it's supposed to give me the information that I need to put into modules, but for some reason, mine doesn't, it stops after telling me what sensors-detect found (and lists one as "to-be-written"?).

I have a similar board (p5q-pro) and sensors-detect from Intrepid also doesn't see the chip. However if you look here:
[http://article.gmane.org/gmane.linux.drivers.sensors/17253]("http://article.gmane.org/gmane.linux.drivers.sensors/17253")

you can see a workaround:

$ sudo modprobe w83627ehf force_id=0x8860

afterwards, do a 'sensors -s' and then 'sensors' should display something like this:
```

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.06 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +11.35 V  (min = +12.14 V, max =  +2.96 V)   ALARM
AVCC:        +3.20 V  (min =  +0.54 V, max =  +0.06 V)   ALARM
3VCC:        +3.17 V  (min =  +1.17 V, max =  +0.53 V)   ALARM
in4:         +1.69 V  (min =  +0.53 V, max =  +0.01 V)   ALARM
in5:         +2.04 V  (min =  +0.52 V, max =  +0.58 V)   ALARM
in6:         +4.84 V  (min =  +0.67 V, max =  +0.23 V)   ALARM
VSB:         +3.36 V  (min =  +2.40 V, max =  +1.06 V)   ALARM
VBAT:        +3.30 V  (min =  +0.99 V, max =  +0.27 V)   ALARM
in9:         +0.00 V  (min =  +1.63 V, max =  +0.62 V)   ALARM
Case Fan:      0 RPM  (min = 5273 RPM, div = 128)  ALARM
CPU Fan:    2410 RPM  (min =  753 RPM, div = 16)
Aux Fan:       0 RPM  (min = 3245 RPM, div = 32)  ALARM
fan4:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 2109 RPM, div = 128)  ALARM
Sys Temp:    +38.0°C  (high = -51.0°C, hyst = +34.0°C)  ALARM  sensor = thermistor
CPU Temp:    +36.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +11.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```

Obviously some values are wrong, but at least you get the MB(Sys) temp and fan speed. I needs more work but it's a start.

> **NineseveN said:**
> 
```

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.
```
Any thoughts/help?

BTW, you should avoid installing source packages unless you use something like 'checkinstall'... it seems the one you compiled is looking for a Fedora/RPM distro -- there is no '/etc/sysconfig' under Debian/Ubuntu. Better try to 'make uninstall' it and delete anything that's been added to /etc, then reinstall the repository package and try the above workaround.

Good luck!

---

### Post by NineseveN on 2008-08-06
> **mgc8 said:**
> I have a similar board (p5q-pro) and sensors-detect from Intrepid also doesn't see the chip. However if you look here:
[http://article.gmane.org/gmane.linux.drivers.sensors/17253]("http://article.gmane.org/gmane.linux.drivers.sensors/17253")

you can see a workaround:

$ sudo modprobe w83627ehf force_id=0x8860

afterwards, do a 'sensors -s' and then 'sensors' should display something like this:
```

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.06 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +11.35 V  (min = +12.14 V, max =  +2.96 V)   ALARM
AVCC:        +3.20 V  (min =  +0.54 V, max =  +0.06 V)   ALARM
3VCC:        +3.17 V  (min =  +1.17 V, max =  +0.53 V)   ALARM
in4:         +1.69 V  (min =  +0.53 V, max =  +0.01 V)   ALARM
in5:         +2.04 V  (min =  +0.52 V, max =  +0.58 V)   ALARM
in6:         +4.84 V  (min =  +0.67 V, max =  +0.23 V)   ALARM
VSB:         +3.36 V  (min =  +2.40 V, max =  +1.06 V)   ALARM
VBAT:        +3.30 V  (min =  +0.99 V, max =  +0.27 V)   ALARM
in9:         +0.00 V  (min =  +1.63 V, max =  +0.62 V)   ALARM
Case Fan:      0 RPM  (min = 5273 RPM, div = 128)  ALARM
CPU Fan:    2410 RPM  (min =  753 RPM, div = 16)
Aux Fan:       0 RPM  (min = 3245 RPM, div = 32)  ALARM
fan4:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 2109 RPM, div = 128)  ALARM
Sys Temp:    +38.0°C  (high = -51.0°C, hyst = +34.0°C)  ALARM  sensor = thermistor
CPU Temp:    +36.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +11.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```

Obviously some values are wrong, but at least you get the MB(Sys) temp and fan speed. I needs more work but it's a start.



BTW, you should avoid installing source packages unless you use something like 'checkinstall'... it seems the one you compiled is looking for a Fedora/RPM distro -- there is no '/etc/sysconfig' under Debian/Ubuntu. Better try to 'make uninstall' it and delete anything that's been added to /etc, then reinstall the repository package and try the above workaround.

Good luck!

Thanks for the help. I had no idea about the Fedora/RPM thing above. I'll make the uninstall and then try the repository version of LM-sensors. Thanks a million!

---

### Post by NineseveN on 2008-08-06
I tired it, got the following: 

FATAL: Error inserting w83627ehf (/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/w83627ehf.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by mgc8 on 2008-08-08
> **NineseveN said:**
> I tired it, got the following: 
FATAL: Error inserting w83627ehf (/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/w83627ehf.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And what does 'dmesg' say? Maybe it helps...

The problem is that the more recent versions of lm_sensors are developed in the kernel, therefore by downloading and installing from lm-sensors.org you only get the userspace tools (libraries and programs). If your version of the driver (w83627ehf.ko) is too old, you need to update the module itself, which means either a) install a new kernel or b) download the sensors part of the kernel tree, install the source for your kernel and try compiling it that way -- although it will probably fail and require more patching.

I'd say the easiest would be to either install one of the [[COLOR="Red"]Intrepid kernels[/COLOR]]("http://packages.ubuntu.com/intrepid/base/linux-image-2.6.26-5-generic") or download the [[COLOR="Red"]source[/COLOR]]("http://www.kernel.org") and compile it yourself (depends on how comfortable you are with doing that). If you need help with any of that feel free to ask...[COLOR="Red"][/COLOR]

---

### Post by NineseveN on 2008-08-11
> **mgc8 said:**
> And what does 'dmesg' say? Maybe it helps...


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 21:01:46 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] Command line: root=UUID=778ac2b4-e137-4876-b4bc-2a6a4c88e2e2 ro splash 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 156) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851824) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FAF00 checksum 0
[    0.000000] ACPI: RSDP 000FAF00, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF70000, 003C (r1 A_M_I_ OEMRSDT   5000826 MSFT       97)
[    0.000000] ACPI: FACP CFF70200, 0084 (r2 A_M_I_ OEMFACP   5000826 MSFT       97)
[    0.000000] ACPI: DSDT CFF70440, 92A7 (r1  A0993 A0993001        1 INTL 20060113)
[    0.000000] ACPI: FACS CFF7E000, 0040
[    0.000000] ACPI: APIC CFF70390, 006C (r1 A_M_I_ OEMAPIC   5000826 MSFT       97)
[    0.000000] ACPI: MCFG CFF70400, 003C (r1 A_M_I_ OEMMCFG   5000826 MSFT       97)
[    0.000000] ACPI: OEMB CFF7E040, 0081 (r1 A_M_I_ AMI_OEM   5000826 MSFT       97)
[    0.000000] ACPI: HPET CFF796F0, 0038 (r1 A_M_I_ OEMHPET   5000826 MSFT       97)
[    0.000000] ACPI: OSFR CFF79730, 00B0 (r1 A_M_I_ OEMOSFR   5000826 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 156) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851824) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      156
[    0.000000]     0:      256 ->   851824
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048332
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1237 pages reserved
[    0.000000]   DMA zone: 2703 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 000000000009d000
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff70000 - 00000000cff7e000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff7e000 - 00000000cffd0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cffd0000 - 00000000d0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000d0000000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000fff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ee00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030071
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=778ac2b4-e137-4876-b4bc-2a6a4c88e2e2 ro splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   34.527147] time.c: Detected 2999.659 MHz processor.
[   34.528595] Console: colour VGA+ 80x25
[   34.528598] console [tty0] enabled
[   34.532522] Checking aperture...
[   34.532575] Calgary: detecting Calgary via BIOS EBDA area
[   34.532576] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   34.532577] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   34.557818] Placing software IO TLB between 0x104d000 - 0x504d000
[   34.585010] Memory: 4046488k/4980736k available (2489k kernel code, 146840k reserved, 1318k data, 320k init)
[   34.585115] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   34.664986] Calibrating delay using timer specific routine.. 6003.09 BogoMIPS (lpj=12006181)
[   34.665105] Security Framework initialized
[   34.665158] SELinux:  Disabled at boot.
[   34.665214] AppArmor: AppArmor initialized
[   34.665264] Failure registering capabilities with primary security module.
[   34.665550] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   34.667265] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   34.668100] Mount-cache hash table entries: 256
[   34.668241] Initializing cgroup subsys ns
[   34.668294] Initializing cgroup subsys cpuacct
[   34.668353] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.668435] CPU: L2 cache: 6144K
[   34.668483] CPU 0/0 -> Node 0
[   34.668530] using mwait in idle threads.
[   34.668579] CPU: Physical Processor ID: 0
[   34.668627] CPU: Processor Core ID: 0
[   34.668679] CPU0: Thermal monitoring enabled (TM2)
[   34.668737] SMP alternatives: switching to UP code
[   34.669438] Early unpacking initramfs... done
[   34.899164] ACPI: Core revision 20070126
[   34.899248] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   34.963890] Using local APIC timer interrupts.
[   34.997242] APIC timer calibration result 20830974
[   34.997243] Detected 20.830 MHz APIC timer.
[   34.997341] SMP alternatives: switching to SMP code
[   34.997952] Booting processor 1/2 APIC 0x1
[   35.008547] Initializing CPU#1
[   35.085197] Calibrating delay using timer specific routine.. 5999.30 BogoMIPS (lpj=11998605)
[   35.085202] CPU: L1 I cache: 32K, L1 D cache: 32K
[   35.085203] CPU: L2 cache: 6144K
[   35.085204] CPU 1/1 -> Node 0
[   35.085205] CPU: Physical Processor ID: 0
[   35.085205] CPU: Processor Core ID: 1
[   35.085210] CPU1: Thermal monitoring enabled (TM2)
[   35.085835] Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[   35.085892] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   35.106420] Brought up 2 CPUs
[   35.106523] CPU0 attaching sched-domain:
[   35.106524]  domain 0: span 03
[   35.106525]   groups: 01 02
[   35.106526]   domain 1: span 03
[   35.106527]    groups: 03
[   35.106528] CPU1 attaching sched-domain:
[   35.106529]  domain 0: span 03
[   35.106530]   groups: 02 01
[   35.106531]   domain 1: span 03
[   35.106532]    groups: 03
[   35.106688] net_namespace: 120 bytes
[   35.106969] Time:  1:09:43  Date: 08/12/08
[   35.107034] NET: Registered protocol family 16
[   35.107202] ACPI: bus type pci registered
[   35.107296] PCI: Using configuration type 1
[   35.109524] ACPI: EC: Look up EC in DSDT
[   35.115055] ACPI: Interpreter enabled
[   35.115104] ACPI: (supports S0 S1 S3 S4 S5)
[   35.115317] ACPI: Using IOAPIC for interrupt routing
[   35.115490] Error attaching device data
[   35.115563] Error attaching device data
[   35.115635] Error attaching device data
[   35.115709] Error attaching device data
[   35.120433] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.121567] PCI: Transparent bridge - 0000:00:1e.0
[   35.121639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.121746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   35.121802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   35.121885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   35.121939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   35.122002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   35.132396] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   35.132898] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   35.133401] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   35.133901] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   35.134401] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   35.134977] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   35.135476] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   35.135976] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   35.136477] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  AB, should be A2 [20070126]
[   35.136610] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.136677] pnp: PnP ACPI init
[   35.136728] ACPI: bus type pnp registered
[   35.138674] pnp: PnP ACPI: found 15 devices
[   35.138723] ACPI: ACPI bus type pnp unregistered
[   35.138909] PCI: Using ACPI for IRQ routing
[   35.138959] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.173126] NET: Registered protocol family 8
[   35.173178] NET: Registered protocol family 20
[   35.173252] PCI-GART: No AMD northbridge found.
[   35.173304] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   35.173511] hpet0: 4 64-bit timers, 14318180 Hz
[   35.174578] AppArmor: AppArmor Filesystem Enabled
[   35.177099] Time: tsc clocksource has been installed.
[   35.177155] Switched to high resolution mode on CPU 0
[   35.178337] Switched to high resolution mode on CPU 1
[   35.185090] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   35.185150] system 00:07: ioport range 0x290-0x29f has been reserved
[   35.185213] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   35.185265] system 00:08: ioport range 0x800-0x87f has been reserved
[   35.185318] system 00:08: ioport range 0x500-0x57f has been reserved
[   35.185371] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[   35.185424] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   35.185478] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   35.185532] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   35.185588] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   35.185642] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   35.185710] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   35.185765] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   35.186651] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   35.186704] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   35.186758] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[   35.186823] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   35.187107] PCI: Bridge: 0000:00:01.0
[   35.187156]   IO window: c000-cfff
[   35.187205]   MEM window: fa000000-fe8fffff
[   35.187254]   PREFETCH window: d0000000-dfffffff
[   35.187305] PCI: Bridge: 0000:00:1c.0
[   35.187352]   IO window: disabled.
[   35.187402]   MEM window: disabled.
[   35.187451]   PREFETCH window: f8f00000-f8ffffff
[   35.187503] PCI: Bridge: 0000:00:1c.4
[   35.187551]   IO window: e000-efff
[   35.187601]   MEM window: fea00000-feafffff
[   35.187651]   PREFETCH window: disabled.
[   35.187701] PCI: Bridge: 0000:00:1c.5
[   35.187750]   IO window: d000-dfff
[   35.187800]   MEM window: fe900000-fe9fffff
[   35.187850]   PREFETCH window: disabled.
[   35.187900] PCI: Bridge: 0000:00:1e.0
[   35.187948]   IO window: disabled.
[   35.187997]   MEM window: feb00000-febfffff
[   35.188048]   PREFETCH window: disabled.
[   35.188104] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.188201] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.188212] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.188310] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.188321] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   35.188419] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.188430] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   35.188527] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   35.188534] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   35.188539] NET: Registered protocol family 2
[   35.221139] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.221840] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   35.224128] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   35.224571] TCP: Hash tables configured (established 524288 bind 65536)
[   35.224624] TCP reno registered
[   35.233151] checking if image is initramfs... it is
[   35.685374] Freeing initrd memory: 7552k freed
[   35.687636] audit: initializing netlink socket (disabled)
[   35.687704] audit(1218503383.084:1): initialized
[   35.689057] VFS: Disk quotas dquot_6.5.1
[   35.689145] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   35.689268] io scheduler noop registered
[   35.689317] io scheduler anticipatory registered
[   35.689366] io scheduler deadline registered
[   35.689479] io scheduler cfq registered (default)
[   35.694229] Boot video device is 0000:01:00.0
[   35.694341] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.694359] assign_interrupt_mode Found MSI capability
[   35.694426] Allocate Port Service[0000:00:01.0:pcie00]
[   35.694472] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.694498] assign_interrupt_mode Found MSI capability
[   35.694569] Allocate Port Service[0000:00:1c.0:pcie00]
[   35.694588] Allocate Port Service[0000:00:1c.0:pcie02]
[   35.694638] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.694664] assign_interrupt_mode Found MSI capability
[   35.694735] Allocate Port Service[0000:00:1c.4:pcie00]
[   35.694755] Allocate Port Service[0000:00:1c.4:pcie02]
[   35.694806] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   35.694833] assign_interrupt_mode Found MSI capability
[   35.694904] Allocate Port Service[0000:00:1c.5:pcie00]
[   35.694922] Allocate Port Service[0000:00:1c.5:pcie02]
[   35.708972] Real Time Clock Driver v1.12ac
[   35.709132] hpet_resources: 0xfed00000 is busy
[   35.709155] Linux agpgart interface v0.102
[   35.709205] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.709362] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.709738] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.710184] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.710283] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   35.710398] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   35.710450] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   35.710986] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.725018] mice: PS/2 mouse device common for all mice
[   35.725096] cpuidle: using governor ladder
[   35.725148] cpuidle: using governor menu
[   35.725270] NET: Registered protocol family 1
[   35.725375] registered taskstats version 1
[   35.725491]   Magic number: 4:631:154
[   35.725545]   hash matches device ttyp8
[   35.725610]   hash matches device device:21
[   35.725662] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   35.725729] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   35.725780] EDD information not available.
[   35.725833] Freeing unused kernel memory: 320k freed
[   35.752091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   36.843744] fuse init (API version 7.9)
[   36.878346] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   36.878353] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   36.975079] usbcore: registered new interface driver usbfs
[   36.975093] usbcore: registered new interface driver hub
[   36.979376] usbcore: registered new device driver usb
[   36.984226] USB Universal Host Controller Interface driver v3.0
[   36.984262] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.984270] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   36.984272] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   36.984433] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   36.984455] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[   36.984532] usb usb1: configuration #1 chosen from 1 choice
[   36.984545] hub 1-0:1.0: USB hub found
[   36.984548] hub 1-0:1.0: 2 ports detected
[   37.074876] SCSI subsystem initialized
[   37.086978] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   37.086987] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   37.086989] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   37.087002] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   37.087023] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[   37.087084] usb usb2: configuration #1 chosen from 1 choice
[   37.087096] hub 2-0:1.0: USB hub found
[   37.087099] hub 2-0:1.0: 2 ports detected
[   37.092416] libata version 3.00 loaded.
[   37.112955] Floppy drive(s): fd0 is 1.44M
[   37.131021] FDC 0 is a post-1991 82077
[   37.190853] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.190861] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   37.190864] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   37.190881] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   37.190902] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[   37.190964] usb usb3: configuration #1 chosen from 1 choice
[   37.190977] hub 3-0:1.0: USB hub found
[   37.190980] hub 3-0:1.0: 2 ports detected
[   37.294731] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   37.294738] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   37.294740] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   37.294754] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   37.294774] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[   37.294834] usb usb4: configuration #1 chosen from 1 choice
[   37.294849] hub 4-0:1.0: USB hub found
[   37.294852] hub 4-0:1.0: 2 ports detected
[   37.398604] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   37.398611] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   37.398613] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   37.398625] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   37.398645] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[   37.398702] usb usb5: configuration #1 chosen from 1 choice
[   37.398714] hub 5-0:1.0: USB hub found
[   37.398717] hub 5-0:1.0: 2 ports detected
[   37.502479] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.502485] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   37.502488] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   37.502503] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   37.502523] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[   37.502583] usb usb6: configuration #1 chosen from 1 choice
[   37.502595] hub 6-0:1.0: USB hub found
[   37.502598] hub 6-0:1.0: 2 ports detected
[   37.606453] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   37.607626] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   37.607630] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   37.607667] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   37.611565] ehci_hcd 0000:00:1a.7: debug port 1
[   37.611568] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   37.611572] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[   37.638778] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   37.650258] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.650346] usb usb7: configuration #1 chosen from 1 choice
[   37.650370] hub 7-0:1.0: USB hub found
[   37.650375] hub 7-0:1.0: 6 ports detected
[   37.754205] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   37.755571] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   37.755575] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   37.755618] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   37.759502] ehci_hcd 0000:00:1d.7: debug port 1
[   37.759506] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   37.759510] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[   37.774116] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.774196] usb usb8: configuration #1 chosen from 1 choice
[   37.774216] hub 8-0:1.0: USB hub found
[   37.774229] hub 8-0:1.0: 6 ports detected
[   37.878143] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[   37.930174] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   37.942873] ahci 0000:00:1f.2: version 3.0
[   37.942890] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   38.177653] usb 4-1: device not accepting address 2, error -71
[   38.601168] usb 8-1: new high speed USB device using ehci_hcd and address 2
[   38.734944] usb 8-1: configuration #1 chosen from 1 choice
[   38.916848] usbcore: registered new interface driver libusual
[   38.919108] Initializing USB Mass Storage driver...
[   38.919171] scsi0 : SCSI emulation for USB Mass Storage devices
[   38.919200] usbcore: registered new interface driver usb-storage
[   38.919202] USB Mass Storage support registered.
[   38.919234] usb-storage: device found at 2
[   38.919235] usb-storage: waiting for device to settle before scanning
[   38.944792] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   38.944795] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part 
[   38.944799] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   38.944961] scsi1 : ahci
[   38.944986] scsi2 : ahci
[   38.949189] scsi3 : ahci
[   38.949212] scsi4 : ahci
[   38.949232] scsi5 : ahci
[   38.949252] scsi6 : ahci
[   38.949312] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 507
[   38.949314] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 507
[   38.949316] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 507
[   38.949317] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 507
[   38.949319] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 507
[   38.949321] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 507
[   39.204475] usb 6-1: new low speed USB device using uhci_hcd and address 2
[   39.213025] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00014b351a]
[   39.380565] usb 6-1: configuration #1 chosen from 1 choice
[   39.393713] usbcore: registered new interface driver hiddev
[   39.407636] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb6/6-1/6-1:1.0/input/input2
[   39.432239] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1
[   39.432249] usbcore: registered new interface driver usbhid
[   39.432251] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.588485] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   39.589433] ata1.00: ATA-8: WDC WD2500AAKS-00VSA0, 01.01B01, max UDMA/133
[   39.589436] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   39.590463] ata1.00: configured for UDMA/133
[   39.908109] ata2: SATA link down (SStatus 0 SControl 300)
[   40.227741] ata3: SATA link down (SStatus 0 SControl 300)
[   40.547377] ata4: SATA link down (SStatus 0 SControl 300)
[   40.867006] ata5: SATA link down (SStatus 0 SControl 300)
[   41.186642] ata6: SATA link down (SStatus 0 SControl 300)
[   41.186705] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
[   41.186828] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.186851] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   41.186860] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   41.188032] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.188049] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   41.188072] scsi7 : pata_marvell
[   41.188094] scsi8 : pata_marvell
[   41.188108] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[   41.188109] ata8: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
[   41.189225] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00 
[   41.192006] Driver 'sd' needs updating - please use bus_type methods
[   41.202704] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   41.202714] sd 1:0:0:0: [sda] Write Protect is off
[   41.202715] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.202728] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.202765] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   41.202773] sd 1:0:0:0: [sda] Write Protect is off
[   41.202774] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.202791] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.202793]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[   41.266573] sd 1:0:0:0: [sda] Attached SCSI disk
[   41.268356] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   41.551523] Attempting manual resume
[   41.551526] swsusp: Resume From Partition 8:8
[   41.551526] PM: Checking swsusp image.
[   41.551629] PM: Resume from disk failed.
[   41.591139] kjournald starting.  Commit interval 5 seconds
[   41.591143] EXT3-fs: mounted filesystem with ordered data mode.
[   41.873753] ata7.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL0C, max UDMA/66
[   41.873763] ata7.01: ATAPI: LITE-ON LTR-52327S, QS5A, max UDMA/33
[   41.873768] ata7.00: limited to UDMA/33 due to 40-wire cable
[   42.061540] ata7.00: configured for UDMA/33
[   42.249320] ata7.01: configured for UDMA/33
[   42.250450] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00 
[   42.420930] scsi 7:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0C PQ: 0 ANSI: 5
[   42.420988] scsi 7:0:0:0: Attached scsi generic sg1 type 5
[   42.421817] scsi 7:0:1:0: CD-ROM            LITE-ON  LTR-52327S       QS5A PQ: 0 ANSI: 5
[   42.421862] scsi 7:0:1:0: Attached scsi generic sg2 type 5
[   43.911240] usb-storage: device scan complete
[   43.946576] scsi 0:0:0:0: Direct-Access     WDC WD12 00VE-00KWT0      01.0 PQ: 0 ANSI: 0
[   43.947813] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   43.948685] sd 0:0:0:0: [sdb] Write Protect is off
[   43.948688] sd 0:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   43.948689] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   43.949684] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   43.950560] sd 0:0:0:0: [sdb] Write Protect is off
[   43.950562] sd 0:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   43.950563] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   43.950566]  sdb: sdb1
[   43.951099] sd 0:0:0:0: [sdb] Attached SCSI disk
[   43.951122] sd 0:0:0:0: Attached scsi generic sg3 type 0
[   46.717629] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   46.751865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.766947] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.840091] input: Power Button (FF) as /devices/virtual/input/input4
[   46.971586] ACPI: Power Button (FF) [PWRF]
[   46.971644] input: Power Button (CM) as /devices/virtual/input/input5
[   47.031508] ACPI: Power Button (CM) [PWRB]
[   47.366877] Atheros(R) AR8121/AR8113 PCI-E Ethernet Network Driver - version 1.0.0.4
[   47.366880] Copyright (c) 2007 Atheros Corporation.
[   47.366924] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   47.366935] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   47.405753] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   47.406881] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   47.444778] Driver 'sr' needs updating - please use bus_type methods
[   47.444861] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   47.452470] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   47.452471] Uniform CD-ROM driver Revision: 3.20
[   47.452498] sr 7:0:0:0: Attached scsi CD-ROM sr0
[   47.457586] sr1: scsi3-mmc drive: 76x/52x writer cd/rw xa/form2 cdda tray
[   47.457608] sr 7:0:1:0: Attached scsi CD-ROM sr1
[   47.622787] nvidia: module license 'NVIDIA' taints kernel.
[   47.877419] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   47.877427] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   47.877471] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.09  Wed Jun  4 23:40:50 PDT 2008
[   48.298306] NET: Registered protocol family 10
[   48.298424] lo: Disabled Privacy Extensions
[   48.298597] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.026666] lp: driver loaded but no devices found
[   49.159187] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   49.162330] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   49.162806] Adding 7815580k swap on /dev/sda8.  Priority:-1 extents:1 across:7815580k
[   49.731688] EXT3 FS on sda1, internal journal
[   59.820801] eth0: no IPv6 routers present
[   60.383461] kjournald starting.  Commit interval 5 seconds
[   60.383766] EXT3 FS on sda5, internal journal
[   60.383768] EXT3-fs: mounted filesystem with ordered data mode.
[   60.795411] ip_tables: (C) 2000-2006 Netfilter Core Team
[   61.395786] No dock devices found.
[   62.362960] ppdev: user-space parallel port driver
[   62.489370] audit(1218503410.596:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5485 profile="/usr/sbin/cupsd" namespace="default"

```


> The problem is that the more recent versions of lm_sensors are developed in the kernel, therefore by downloading and installing from lm-sensors.org you only get the userspace tools (libraries and programs). If your version of the driver (w83627ehf.ko) is too old, you need to update the module itself, which means either a) install a new kernel or b) download the sensors part of the kernel tree, install the source for your kernel and try compiling it that way -- although it will probably fail and require more patching.

I'd say the easiest would be to either install one of the [[COLOR="Red"]Intrepid kernels[/COLOR]]("http://packages.ubuntu.com/intrepid/base/linux-image-2.6.26-5-generic") or download the [[COLOR="Red"]source[/COLOR]]("http://www.kernel.org") and compile it yourself (depends on how comfortable you are with doing that). If you need help with any of that feel free to ask...[COLOR="Red"][/COLOR]

I might try that, but right now, I'm just not needing sensors enough to do all of that when I really don't know what it entails. But thanks for the help, it's been awesome.

---

### Post by grigio on 2008-08-27
thank you for the tip. It works perfectly on 2.6.26

---

### Post by Anubis on 2009-07-17
Thanks for the modprobe line. It is the same line my XFX 680i used.

---

### Post by ScottNZ on 2009-08-12
Hi All,

Yes I'm new to Linux, but I'm learning as fast as I can...

>> $ sudo modprobe w83627ehf force_id=0x8860

I have an Asus P5Q Deluxe running Ubuntu Jaunty, and the above command works for me as well (or at least most of the values seem accurate thus far). Can I put the "w83627ehf force_id=0x8860" bit into my /etc/modules file? Will the "force_id" option work that way?

Cheers,
Scott

---

### Post by Anubis on 2009-08-23
> **ScottNZ said:**
> Hi All,

Yes I'm new to Linux, but I'm learning as fast as I can...

>> $ sudo modprobe w83627ehf force_id=0x8860

I have an Asus P5Q Deluxe running Ubuntu Jaunty, and the above command works for me as well (or at least most of the values seem accurate thus far). Can I put the "w83627ehf force_id=0x8860" bit into my /etc/modules file? Will the "force_id" option work that way?

Cheers,
Scott
Yes!

---

### Post by Anubis on 2009-08-23
sudo modprobe w83627ehf force_id=0x8860
FATAL: Error inserting w83627ehf (/lib/modules/2.6.31-6-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

This does not work on 9.10 here.:confused:

---

### Post by Anubis on 2009-08-27
Anyone using KDE 4.3?

---

### Post by ikisham on 2009-10-03
Lm-sensors stopped working with some sensors (on purpose) in kernel 2.6.31 since it was conflicting with ACPI.
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

---

### Post by Anubis on 2009-10-10
> **ikisham said:**
> Lm-sensors stopped working with some sensors (on purpose) in kernel 2.6.31 since it was conflicting with ACPI.
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

"Make sure you have the asus_atk0110 driver enabled in your kernel configuration to use this. You will also need lm-sensors version 3.1.0 or later." 

From the article you linked. Does Ubuntu have this driver enabled in the kernel? And I see lm-sensors version 3.1.0 did not make it into Karmic.

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/447837](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/447837)

---

### Post by buzzin on 2009-10-21
In order for this fix to work with Karmic you need to edit your grub also. This is because the kernel which comes with Karmic is more strict on ACPI IRQS.

APPEND the following to kopt in your grub menu.lst file; 

```
acpi_enforce_resources=lax
```

e.g your modified kopt like should look like the following;

```
# kopt=root=UUID=<your drives UUID> ro acpi_enforce_resources=lax
```

DONT REMOVE the # !

then run;

```
sudo update-grub
```

See this bug for more details;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246")

---

### Post by ^_Pepe_^ on 2009-10-28
> **buzzin said:**
> In order for this fix to work with Karmic you need to edit your grub also. This is because the kernel which comes with Karmic is more strict on ACPI IRQS.

APPEND the following to kopt in your grub menu.lst file; 

```
acpi_enforce_resources=lax
```

e.g your modified kopt like should look like the following;

```
# kopt=root=UUID=<your drives UUID> ro acpi_enforce_resources=lax
```

DONT REMOVE the # !

then run;

```
sudo update-grub
```

See this bug for more details;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246")
Hi! I'm also affected here, with a M2N ASUS Mobo. Here [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31), we're told, that this fix might be dangerous, since it brings the system to the old behaviour. 

Can anybody post a howto to get the new lm-sensors functionality? Do we need to unninstall first? Shall we delete our .conf file?

Confused here! :-(

Regards
^_Pepe_^

---

### Post by buzzin on 2009-10-28
> **^_Pepe_^ said:**
> Hi! I'm also affected here, with a M2N ASUS Mobo. Here [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31), we're told, that this fix might be dangerous, since it brings the system to the old behaviour. 

Can anybody post a howto to get the new lm-sensors functionality? Do we need to unninstall first? Shall we delete our .conf file?

Confused here! :-(

Regards
^_Pepe_^

Eekkk, nice catch Pepe... While ive noticed no ill effects on the Asus P5Q with the latest BIOS, i wouldnt know how it would effect other boards.

---

### Post by ^_Pepe_^ on 2009-10-28
Hi!

I've been told by lm-sensors staff, to use the acpi_enforce_resources=lax option, because ASUS M2N MoBo, won't have fan control with asus_atk0110 driver, and will with the old one.

Soooo, I'll go for the **buzzin** option tonight.

I also have been told to blacklist asus_atk0110 driver. Did you do that?

Regards,
P.S.: (good info:[http://www.gossamer-threads.com/lists/linux/kernel/1131613](http://www.gossamer-threads.com/lists/linux/kernel/1131613))

---

### Post by Stu284 on 2009-10-30
Hi I would like to get this working here

can someone tell me how to install the latest lm-sensors v3.1 from source please?  sorry but i am new to this

and how do I enable the asus_atk0110 driver ?



Thanks

---

### Post by ^_Pepe_^ on 2009-10-30
> **Stu284 said:**
> Hi I would like to get this working here

can someone tell me how to install the latest lm-sensors v3.1 from source please?  sorry but i am new to this

and how do I enable the asus_atk0110 driver ?



Thanks

Hi!

As said above, asus_atk0110 driver is already installed. You can check with with

```
lsmod
```

Installing 3.1.1 is not very difficult.

1. Donwload it from lm-sensors.org
2. Untar it to your Desktop
3. Open terminal, go to your desktop
4. Code: sudo make all (I don't know if it's correct, but I guess it worked for me)

Anyway, new driver didn't work for me (Asus M2N), and I had to blacklist it.

Regards
^_Pepe_^

---

### Post by Stu284 on 2009-10-30
thanks pepe, seems to of worked, sensors command give me this

Adapter: ACPI interface
Vcore Voltage:       +1.44 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:       +3.43 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.03 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.52 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      3668 RPM  (min =  600 RPM)
CHASSIS FAN Speed:     0 RPM  (min =  600 RPM)
CHASSIS FAN 2 Speed:   0 RPM  (min =  600 RPM)
CPU Temperature:     +46.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:      +48.0°C  (high = +45.0°C, crit = +75.0°C)  

temps seem to be same to what the bios gives me, i am using an asus M4A78T-E board

---

### Post by ^_Pepe_^ on 2009-10-30
Sure! You're lucky. Go for pwmconfig to slow your fans...

Regards,

---

### Post by cb_rex on 2009-11-02
I'd just like to thank everyone commenting on this thread for helping me out with my sensors problem using an ASUS P5Q SE.

I was doing a clean install of Karmic and initially the sensors didn't work, so I decided to update my motherboard to the latest BIOS on the ASUS website. After doing this I could see temperatures, but not fan speeds.  

To fix this I first tried the "acpi_enforce_resources=lax" into grub menu.lst file; as described by buzzin in post 15, above, however this didn't work.  After a bit of reading round [>HERE<]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246") (post 11 was when it all made sense, thanks Stefan), I realised it was due to me having Grub 2 as I had done a clean install not an upgrade from 9.04.   Essentially its the same fix but the file is in a different place...

/etc/default/grub

Here I inserted: GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
Saved and closed then in the terminal ran: update-grub
Then rebooted.

After reboot I applied the modprobe fix exactly as I describe [>HERE<]("http://ubuntuforums.org/showthread.php?p=7210837#post7210837") (post 319), for 9.04 and it seems to be working fine again.

Thanks guys!

---

