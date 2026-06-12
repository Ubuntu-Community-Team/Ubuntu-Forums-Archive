---
title: "acpi not loading sony bcg-f650"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by rolfpal on 2004-11-10
POwer management doesn't seem to work on my laptop

modprobe returns

 sudo modprobe acpi
WARNING: Error inserting processor (/lib/modules/2.6.8.1-3-686/kernel/drivers/acpi/processor.ko): No such device
FATAL: Error inserting acpi (/lib/modules/2.6.8.1-3-686/kernel/arch/i386/kernel/cpu/cpufreq/acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg returns

acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance


Any ideas?

TIA

Rolf

---

### Post by chien on 2004-11-28
I'm running on a Sony PCG-FX120 and acpi doesn't seems to work either.

what I do its boot the system with acpi=off, I guess it run acpm or whatever its called the old power manager

---

