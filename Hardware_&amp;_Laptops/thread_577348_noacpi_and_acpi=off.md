---
title: "noacpi and acpi=off"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by xavierthomas on 2007-10-16
Hello everybody,

I know there is a lot of forum post about that, but I dd not find one solving my problem:

With a 2.6.20 kernel (Ubuntu 7.04) I had to boot with the kernel options: noapic nolapic noacpi
but I still had acpi working (battery level, poweroof and reboot was ok)

Since I upgraded to 2.6.22 (Ubuntu 7.10) and my kernel hang with these parameters (seems like noacpi is no more a valid option) so I now boot with acpi=off but I do not have battery level anymore and I have to poweroff manually the laptop after the shutdown sequence ended.

So my question is: How can I get the same behavior as noacpi with 2.6.20 but with 2.6.22?
I tried with acpi=noirq  but no chance wiht that and the doc says pci=noacpi have the same utuility.

What else can I try?

Thank you,

Xavier

---

### Post by sethvath on 2007-10-16
The manual shut down problem is one I encountered but was solved with the latest kernel headers. 

Try "pci=routeirq" if "irqpoll" does not work

---

