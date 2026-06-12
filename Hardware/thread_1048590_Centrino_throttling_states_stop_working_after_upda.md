---
title: "Centrino throttling states stop working after update"
date: 2009-01-23
forum: Hardware
---

### Post by Wanganui on 2009-01-23
Using Kubuntu 8.04.1  It looks like my processor is stuck in slow mode (about 600 MHz) after a recent update.  Before, it was correctly stepping up to 1.6 GHz when needed.  Power Manager was indicating the processor frequency in the taskbar icon pop-up, whereas now that is greyed out.

A few applicable excerpts from dmesg:

[   20.714470] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06

[   25.125599] ACPI: Processor [CPU1] (supports 8 throttling states)
[   25.492985] Clocksource tsc unstable (delta = -767801848 ns)

I notice at bootup that the computer is stopping for a significantly long period (maybe a minute?) between those last two messages.

Any ideas?  Anyone else with this problem? Thanks for the help.

---

