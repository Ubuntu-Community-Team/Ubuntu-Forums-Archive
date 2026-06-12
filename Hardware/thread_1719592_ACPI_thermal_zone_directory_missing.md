---
title: "ACPI thermal_zone directory missing"
date: 2011-04-02
forum: Hardware
---

### Post by dhubbard on 2011-04-02
I just updated to Natty beta. Everything is going good, but I'm missing my /proc/acpi/thermal_zone directory is missing. I did a search for something similar and found a recommendation to try the 'sudo modprobe thermal' command, with no success. I haven't found anything else similar. Right now I'm without the ability to track the temperature of my CPUs. Any assistance would be greatly appreciated.

```
lshw
*-cpu
          product: Genuine Intel(R) CPU           T2250  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical

```

```
grep ACPI /boot/config-2.6.38-7-generic 
# Power management and ACPI options
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_PROCFS=y
CONFIG_ACPI_PROCFS_POWER=y
CONFIG_ACPI_POWER_METER=m
CONFIG_ACPI_EC_DEBUGFS=m
CONFIG_ACPI_PROC_EVENT=y
CONFIG_ACPI_AC=y
CONFIG_ACPI_BATTERY=y
CONFIG_ACPI_BUTTON=y
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=y
CONFIG_ACPI_DOCK=y
CONFIG_ACPI_PROCESSOR=y
CONFIG_ACPI_IPMI=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_PROCESSOR_AGGREGATOR=m
CONFIG_ACPI_THERMAL=y
CONFIG_ACPI_CUSTOM_DSDT_FILE=""
# CONFIG_ACPI_CUSTOM_DSDT is not set
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_PCI_SLOT=y
CONFIG_ACPI_CONTAINER=y
CONFIG_ACPI_SBS=y
CONFIG_ACPI_HED=m
CONFIG_ACPI_APEI=y
CONFIG_ACPI_APEI_GHES=m
CONFIG_ACPI_APEI_EINJ=m
CONFIG_ACPI_APEI_ERST_DEBUG=m
CONFIG_X86_ACPI_CPUFREQ=y
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_PNPACPI=y
CONFIG_ATA_ACPI=y
CONFIG_PATA_ACPI=y
# ACPI drivers
# ACPI drivers
CONFIG_ACPI_QUICKSTART=m
CONFIG_THINKPAD_ACPI=m
CONFIG_THINKPAD_ACPI_ALSA_SUPPORT=y
CONFIG_THINKPAD_ACPI_DEBUGFACILITIES=y
# CONFIG_THINKPAD_ACPI_DEBUG is not set
# CONFIG_THINKPAD_ACPI_UNSAFE_LEDS is not set
CONFIG_THINKPAD_ACPI_VIDEO=y
CONFIG_THINKPAD_ACPI_HOTKEY_POLL=y
CONFIG_ACPI_WMI=y
# CONFIG_ACPI_ASUS is not set
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_CMPC=m
```

---

