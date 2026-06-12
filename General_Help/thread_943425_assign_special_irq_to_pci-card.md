---
title: "assign special irq to pci-card?"
date: 2008-10-10
forum: General Help
---

### Post by freke85 on 2008-10-10
hi everybody,

I'm running a dual xeon machine with APIC enabled.

Now I would like to assign a special PCI device (e.g. a parallel port card with PCI-ID 0000:03:00.1[A]) a special IRQ (e.g. 9).

I tried it with the "pirq=" kernel parameter, but it didn't work (or at least, I couldn't make it work).

Does anybody of you have some hints about that?

Thanks a lot,

freke

---

### Post by freke85 on 2008-10-10
ok, after a few tests I got a bad result:

the 'pirq'-parameter offers 8 values in order to manipulate the IRQ routing table (if the system has 2 PCI busses).

I tried all 8 potential settings, but none of them assigned the special irq to my pci card...

is this actually the right way to solve this problem?
are there any other solutions?

thanks for your help,

Christoph

---

### Post by Titan8990 on 2008-10-10
Why not disable APIC and make this change in the BIOS (where it should be made)?

---

### Post by freke85 on 2008-10-11
Thanks for your reply, Titan.

It's not an onboard-parallel card but a PCI card - I can't change the IRQ settings of this card in BIOS (unfortunately).

---

