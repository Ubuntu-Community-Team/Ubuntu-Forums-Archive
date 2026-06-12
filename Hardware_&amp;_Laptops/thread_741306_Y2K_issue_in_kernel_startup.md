---
title: "Y2K issue in kernel startup?"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by ranbo on 2008-03-31
When I run "dmesg", I'm seeing what appears to be a Y2K issue, at least in the formatting of a date:

...
[   14.631199] Measured 1269191 cycles TSC warp between CPUs, turning off TSC clock.
[    0.464000] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.468000] Brought up 2 CPUs
[    0.568000] migration_cost=8000
[    0.568000] Booting paravirtualized kernel on bare hardware
[    0.568000] Time: 10:08:03  Date: 02/31/108
[    0.568000] NET: Registered protocol family 16
[    0.568000] EISA bus registered
...

Note the date is reported as "2/31/108".  That would appear to be "February 31, 2008", which is wrong both in that February doesn't have 31 days; and in that "2008" is being abbreviated as "108".

I doubt this is hurting anything, but it does appear to be wrong.

---

