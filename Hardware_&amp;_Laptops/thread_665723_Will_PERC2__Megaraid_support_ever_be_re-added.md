---
title: "Will PERC2 / Megaraid support ever be re-added?"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by bkann on 2008-01-12
Hi all -

All of my research indicates that the PERC2 / Megaraid drivers were removed in the 2.6 kernel.  I do not have the skills just yet or the patience to compile the drivers and kernel as suggested in several forums, so I'm stuck with quite a bit of unusable hardware if I want to run the newest distributions.

As I have run across a ton of people who are having the same problem as me, I'm led to the following two questions:

a) Why were the drivers removed, and
b) Does anyone know if there are plans to re-add them to the kernel?

I can't seem to find either a rationale for why they would have been removed given their widespread use, nor have I come across a roadmap for Linux driver development.

Any help would be appreciated.  This will assist me in determining whether or not I need to buy a new RAID card.

Thanks in advance!

---

### Post by kidders on 2008-01-13
Hi there,

You'd have to ask the guys at kernel.org why support for your hardware has been removed, and what their future plans are.

A quick Google search suggests LSI have rewritten their drivers and dropped support for some older versions of their own hardware. Since the Linux kernel only seems to incorporate the newest driver at present, support for your hardware may never return. Having said that, the kernel development community & distros' own kernel dev teams may intend to allow the old drivers to be built alongside the new ones at some point. You may want to check, before replacing any hardware.

---

