---
title: "New HP dv6 laptop APIC livecd issues"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by sesheron on 2009-04-14
Ubuntu 8.10. I don't have an exact hardware list on me atm, but if the issue needs it I can get it.But the basics are intel core 2, ati graphics card, 4gb ram.  Basically, I try to boot the livecd and after a while of the loading screen I get a
```

[float number] IO APIC resources could not be allocated
Loading

"Bootsyby" or whatever the little Ubuntu loader is called
[float number] Complaints about logic drive error
[float number] more complaints about logic drive errors

```
And it will do those last few for a bit then stop and just sit.
I did a search and saw that I might need the acpi=off option.
But that didn't change anything.

---

### Post by imbjr on 2009-04-15
I get that

> **sesheron said:**
> IO APIC resources could not be allocated
Loading

when running Jaunty Beta in VirtualBox. Turning off ACPI had no effect, but in either case no obvious detriment to the system was seen.

---

### Post by sesheron on 2009-04-17
Sadly enough, I went back and checked the CD.  It was bad.
Poweriso is fail...I'm going back to Nero

---

