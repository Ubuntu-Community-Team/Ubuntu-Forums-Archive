---
title: "What do the Ubuntu Live CD F6 Other Options mean?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2009-08-27
Hi.
When the Ubuntu Live CD is booted from you get many more options at the end of the screen.

Under '**F6 Other Options**'
acpi=off
noapic
nolapic
edd=on
Free software only

The 'Free software only' option is obvious but what do the other options mean exactly?

Thanks.

---

### Post by presence1960 on 2009-08-27
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

These options in Boot Options are for machines that don't have support for acpi, apic or lapic.

without these appropriate options being selected the install will likely not succeed, if it can even begin in the first place.

---

### Post by Rytron on 2009-08-27
> **presence1960 said:**
> [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

These options in Boot Options are for machines that don't have support for acpi, apic or lapic.

without these appropriate options being selected the install will likely not succeed, if it can even begin in the first place.

Thank you presence1960. That is a comprehensive answer.

---

