---
title: "Each core has different ACPI capabilities (??)"
date: 2011-01-15
forum: Hardware
---

### Post by travisl_10 on 2011-01-15
Hello, I have noticed something strange concerning ACPI on my laptop and desktop (both are running dual-core AMD processors, Turion and Athlon respectively)

When I view the files in /proc/acpi/processor/CPU<0,1>/ they look like this:

CPU0:
```

::::::::::::::
/proc/acpi/processor/CPU0/info
::::::::::::::
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      yes
limit interface:         yes
::::::::::::::
/proc/acpi/processor/CPU0/limit
::::::::::::::
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
::::::::::::::
/proc/acpi/processor/CPU0/power
::::::::::::::
active state:            C0
max_cstate:              C8
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]
::::::::::::::
/proc/acpi/processor/CPU0/throttling
::::::::::::::
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

CPU1:
```

::::::::::::::
/proc/acpi/processor/CPU1/info
::::::::::::::
processor id:            1
acpi id:                 2
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
::::::::::::::
/proc/acpi/processor/CPU1/limit
::::::::::::::
<not supported>
::::::::::::::
/proc/acpi/processor/CPU1/power
::::::::::::::
active state:            C0
max_cstate:              C8
maximum allowed latency: 2000000000 usec
states:
::::::::::::::
/proc/acpi/processor/CPU1/throttling
::::::::::::::
<not supported>

```

It appears that CPU0 supports 'throttling control' and 'limit interface' and CPU1 does not. I haven't observed any difference between cores for Intel dual-core processors (but I only checked a few machines). 

Does anyone know the reason for this?

---

