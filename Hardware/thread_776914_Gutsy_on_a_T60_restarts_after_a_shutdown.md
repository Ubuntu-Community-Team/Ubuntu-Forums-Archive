---
title: "Gutsy on a T60 restarts after a shutdown"
date: 2008-05-01
forum: Hardware
---

### Post by pwozney on 2008-05-01
$ uname -a
Linux WE-HO-LAP01 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux

Whenever I shutdown the system, it powers down completely, the drives spin down...and then after a few seconds it restarts again.

This is different behavior from a restart, which brings the system to POST but never actually turns off the machine.

I replicated this behavior from my desktop, from the login screen menu, and from pressing the power button (which starts the shutdown process).

Here is a recent change history (from memory):
[LIST]
[*]downgraded to 2.6.20-16 (for the SLAB kernel)
[*]installed autofsck (now uninstalled, no change in behavior)
[/LIST]

Any ideas on where I could start troubleshooting?

pw

---

