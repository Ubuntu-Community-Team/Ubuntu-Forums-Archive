---
title: "frequent kernel panics"
date: 2008-07-12
forum: General Help
---

### Post by JLahm on 2008-07-12
I am running Ubuntu Server 7.10 on an Intel DG965WH motherboard with am Intel Core Duo processor and 2GB of RAM. Since I built this system I have had frequent "kernel panic - not syncing: Fatal exception in interrupt" errors. The system has never been up for longer than 11 days at a time before crashing. I recently added an additional 2GB of memory to bring it to 4GB and now it averages a little over 1 day between crashes. I've run memory tests and they check out fine.

In general the server crashes overnight (when I'm not looking... :) ). Several times I've seen the crash log preceded by:
[LIST]
[*]cpu_idle
[*]start_kernel
[*]unknown_bootoption 0x0/0x260
[*]Code: Bad EIP Value...
[*]Kernel Panic - not syncing: Fatal exception in interrupt
[/LIST]

I've installed phpsysinfo and lm_sensors. The CPUs are usually running at 32-38C, so I'm not sure that heat is a problem.

Any ideas would be greatly appreciated. Also, is there any way to capture the crash information that appears on my server's monitor? It does not show up in any /var/log/* files.

I've tried booting with "noapic nolapic acpi=off" and "noapic irqpoll pci=routeirq" options (I had found these recommended on the net) with no luck.

Many thanks.

Jim

---

