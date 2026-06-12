---
title: "Post your powertop power usage estimate"
date: 2009-02-26
forum: Hardware
---

### Post by avilella on 2009-02-26
Hi all,

Can I ask people to report their powertop power usage estimate
on normal conditions, that is, at the moment of reading this?

I'll start with mine:

Sony Vaio SZ1XP -- 17W

---

### Post by TwiceOver on 2009-02-26
Lenovo Ideapad S10e - no ACPI power usage estimate available.

:(

---

### Post by herophuong on 2010-06-23
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 2,2%)         2,17 Ghz     1,2%
polling           0,0ms ( 0,0%)         1,67 Ghz     0,0%
C1 mwait          0,1ms ( 0,0%)         1333 Mhz     0,0%
C3 mwait          6,0ms (97,8%)         1000 Mhz    98,8%


Wakeups-from-idle per second : 164,5    interval: 2,0s
Power usage (5 minute ACPI estimate) :   1,4 W (3,1 hours left)

Top causes for wakeups:
  28,0% ( 62,5)   [kernel scheduler] Load balancing tick
  20,6% ( 46,0)   docky
   9,0% ( 20,0)   [ehci_hcd:usb1, uhci_hcd:usb7, eth1] <interrupt>
   8,7% ( 19,5)   desktopcouch-se
   6,3% ( 14,0)   [kernel core] hrtimer_start (tick_sched_timer)
   4,7% ( 10,5)   [ahci] <interrupt>

"Hp Compaq cq40"

---

### Post by IcarusR on 2010-06-24
Toshiba Equium A100-306 running Intrepid 8.10

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (12.5%)         1.67 Ghz     6.6%
C0                0.0ms ( 0.0%)         1333 Mhz     0.2%
C1                0.0ms ( 0.0%)         1000 Mhz    93.2%
C2                0.1ms ( 0.0%)
C4                5.2ms (87.5%)

Wakeups-from-idle per second : 170.3    interval: 15.0s
Power usage (ACPI estimate): 19.3W (2.2 hours) (long term: 40.0W,/1.1h)

---

