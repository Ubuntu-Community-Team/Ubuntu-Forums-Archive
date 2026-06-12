---
title: "/proc/acpi/thermal_zone empty!"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by edyson on 2007-03-15
My /proc/acpi/thermal_zone directory is completely empty! I'm runnning an up-to-date dapper server on a dual opteron server. I also suspect that this may be related to my random shutdown problem I've been having. Any ideas?

```
Linux dapperserver 2.6.15-26-amd64-server #1 SMP Fri Sep 8 20:33:15 UTC 2006 x86_64 GNU/Linux
```


```

% cat /proc/acpi/processor/CPU1/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no
% cat /proc/acpi/processor/CPU2/info
processor id:            1
acpi id:                 2
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no

```

```

% grep ACPI /boot/config-2.6.15-26-amd64-server
CONFIG_X86_64_ACPI_NUMA=y
# ACPI (Advanced Configuration and Power Interface) Support
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_SLEEP_PROC_FS=y
CONFIG_ACPI_SLEEP_PROC_SLEEP=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_SBS=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_HOTKEY=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_NUMA=y
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_IBM=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_PCC=m
CONFIG_ACPI_SONY=m
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_ACPI_CONTAINER=m
CONFIG_ACPI_TC1100=m
CONFIG_ACPI_INITRD=y
CONFIG_ACPI_DEV=m
CONFIG_X86_POWERNOW_K8_ACPI=y
CONFIG_X86_SPEEDSTEP_CENTRINO_ACPI=y
CONFIG_X86_ACPI_CPUFREQ=m
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_PNPACPI=y
CONFIG_BLK_DEV_IDEACPI=y
CONFIG_SCSI_SATA_ACPI=y
# CONFIG_SERIAL_8250_ACPI is not set
```

---

### Post by Azilla on 2007-03-16
1) From the *info* output on both processors, it would seem they don't support the feature.

2) CONFIG_ACPI_THERMAL=m     <<- That means it was compiled as a module in the kernel, in which case you just need to type the command below to load the module.

```
# sudo modprobe thermal
```

---

### Post by edyson on 2007-03-16
Should opterons support thermal? I ran that command but still nothing.

---

### Post by toganet on 2007-05-10
I am having the same problem with a p4 3.2Ghz running edgy.  Nothing in the thermal_zone directory at all.  Only noticed it after a temperature-related shutdown yesterday while recording two shows and watching a third with mythtv.

---

### Post by Dr.Ninethousand on 2008-03-08
any news on this?.   having the same problem..

---

