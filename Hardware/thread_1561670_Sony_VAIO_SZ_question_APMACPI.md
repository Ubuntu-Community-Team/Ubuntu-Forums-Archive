---
title: "Sony VAIO SZ question APM/ACPI"
date: 2010-08-26
forum: Hardware
---

### Post by zong1 on 2010-08-26
Dear all,
  
  I won't go into the details why, but in order to make use of the second core in an Intel Core Duo CPU on the Sony Vaio SZ series, one has to disable ACPI.  With ACPI enabled the second core will be disabled.  kernel option in grub acpi=off.   Fact. 
Now onto the problem:-

Sending a poweroff event via (shutdown etali) on Ubuntu 10.04 causes the notebook to halt (in the true sense of the word), instead of doing an init 6/ power off.  The result is that after the halt, one has to hold the power button down until it actually shuts down.

I think that the BIOS supports APM, but do not know if this would help, nor how well APM was implemented in the BIOS, even if it was.

Even with ACPI disabled, there are some things left over in /sys and maybe some things related to power, which I am unsure what.  I cannot see anything for APM, but do not know exactly what I am looking for.  I seem to remember Ubuntu 7 did not have this problem, so perhaps APM was removed from the kernel because some legacy support was undesired - Does anyone know if there is a module for APM for me to play with?

Regards, z

ACPI:
/sys/bus/pci/drivers/pata_acpi
/sys/bus/pci/drivers/pata_acpi/uevent
/sys/bus/pci/drivers/pata_acpi/unbind
/sys/bus/pci/drivers/pata_acpi/bind
/sys/bus/pci/drivers/pata_acpi/new_id
/sys/bus/pci/drivers/pata_acpi/remove_id
/sys/module/acpi_cpufreq
/sys/module/acpi_cpufreq/parameters
/sys/module/acpi_cpufreq/parameters/acpi_pstate_strict
/sys/module/powernow_k7/parameters/acpi_force
/sys/module/longhaul/parameters/disable_acpi_c3
/sys/module/pci_hotplug/parameters/debug_acpi
/sys/module/acpi
/sys/module/acpi/parameters
/sys/module/acpi/parameters/immediate_undock
/sys/module/acpi/parameters/acpica_version
/sys/module/acpi/parameters/bfs
/sys/module/acpi/parameters/gts
/sys/module/libata/parameters/noacpi
/sys/module/libata/parameters/acpi_gtf_filter
/proc/sys/kernel/acpi_video_flags

POWER:
/sys/power
/sys/power/state
/sys/power/pm_trace
/sys/power/pm_test
/sys/power/disk
/sys/power/resume
/sys/power/image_size
/sys/module/powernow_k7
/sys/module/powernow_k7/parameters
/sys/module/powernow_k7/parameters/acpi_force
/sys/module/snd_hda_intel/parameters/power_save_controller
/sys/module/snd_hda_intel/parameters/power_save

---

### Post by zong1 on 2010-08-26
The apmd and xapm are in the repos, and I installed these, but neither of these provide the apm module, which is a shame:
```

# modprobe apm
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
FATAL: Error inserting apm (/lib/modules/2.6.32-24-generic/kernel/arch/x86/kernel/apm.ko): No such device

```

And obviously:
```

# xapm
No APM support in kernel

```

---

### Post by zong1 on 2010-08-26
OK, the modules are there in Ubuntu:
# find /lib/modules/|grep apm
/lib/modules/2.6.32-24-generic/kernel/arch/x86/kernel/apm.ko
/lib/modules/2.6.32-24-generic/kernel/drivers/net/arcnet/capmode.ko
/lib/modules/2.6.32-21-generic/kernel/arch/x86/kernel/apm.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/net/arcnet/capmode.ko
/lib/modules/2.6.32-22-generic/kernel/arch/x86/kernel/apm.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/net/arcnet/capmode.ko
/lib/modules/2.6.32-23-generic/kernel/arch/x86/kernel/apm.ko
/lib/modules/2.6.32-23-generic/kernel/drivers/net/arcnet/capmode.ko


but it looks like APM is disabled in the BIOS.  Just some strangly implemented ACPI (cheers Sony). 

I'll report back if/ when I find a way out of this puzzle.

---

