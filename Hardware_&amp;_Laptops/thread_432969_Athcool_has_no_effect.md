---
title: "Athcool has no effect"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by Eremit on 2007-05-04
Hallo,

I use athcool under windows and it reduces my cpu temperature nearly by half but under linux it has no effect.

athcool on:
```
VIA KT133/KM133/KL133/KN133[A] (1106 0305) found
enabling 'Disconnect when STPGNT Detected' bit ...  done
        Address 0x52 : 0x0B -> 0x8B

```

Chipset is correct. I think maybe there is a problem with my acpi support.

```
root@skynet:/proc/acpi/processor/CPU0# cat *
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
<not supported>
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
<not supported>

```

> Powersaving works only if your kernel supports ACPI (APM does not work), because athcool does only (un)set the "Disconnect enable when STPGNT detected" bits in the Chipset's Northbridge. To really save power, the STPGNT signal has to be sent when the CPU is idling. This is done by the ACPI subsystem when C2 state entered.

Seems my cpu stays in C0 state.

```

root@skynet:~# cat /proc/acpi/fadt | acpitbl | grep P_LVL
P_LVL2_LAT:       90
P_LVL3_LAT:       900

```

I found some suggestions to change the ACPI_PROCESSOR_MAX_C2_LATENCY in include/acpi/processor.h but there are only vague instructions and I'm not sure.

ACPI_PROCESSOR_MAX_C2_LATENCY = 100
in the code so that should be ok with my value of 90.

---

