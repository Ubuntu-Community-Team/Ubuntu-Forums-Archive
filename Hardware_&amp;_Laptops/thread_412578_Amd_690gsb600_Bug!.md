---
title: "Amd 690g/sb600 Bug!"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by maynoth on 2007-04-18
**This post could be related to an Ubuntu bug filed at**: bugs.launchpad.net/ubuntu/+bug/107480 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

This deals with the AMD 690G / SB600 Chipset...

There is a bug in the 2.6.20.X Kernel...   the 32bit version will lock up during hardware detection of the install CD in feisty and Edgy.... the 64bit version of feisty works however.

[http://bugzilla.kernel.org/show_bug.cgi?id=8326](http://bugzilla.kernel.org/show_bug.cgi?id=8326)

bugs.launchpad.net/ubuntu/+bug/107480

2.60.20.RC5 is known to work in 32bit mode... so the bug must have been introduced sometime after that..

Anyone who could help isolate the bug and create a fix for this in feisty, it would be much appreciated...

---

### Post by maynoth on 2007-04-19
AHA!!! FOUND A SOLUTION

HPET (High Precision Event Timer) Must be disabled in the bios for it to work... hopefully this will be addressed eventually...

---

