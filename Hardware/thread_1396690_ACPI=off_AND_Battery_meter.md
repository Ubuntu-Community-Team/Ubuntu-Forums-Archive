---
title: "ACPI=off AND Battery meter"
date: 2010-02-02
forum: Hardware
---

### Post by grindboy on 2010-02-02
Hi Guys,

I've finally got my tablet (Motion Computing M1400) to boot Ubuntu 9.10 by using the acpi=off boot argument. This however mean that I have no battery meter info or brightness controls meaning that instead of getting about 4 hours of battery life I'm barely getting 1.5 hours and when I do run out of juice there's no warning. :-(

So my question is: Can I have ACPI=off AND a working battery meter and brightness controls or is there some other ACPI argument I could try (I've already tried force) or is there some way I can get the tablet to support ACPI (BIOS update?)

Many Thanks

Grindboy

[edit] I'm running kernel 2.6.31-17-generic in case that makes a difference.

---

### Post by grindboy on 2010-02-04
Bump

---

### Post by sarthorks on 2010-02-05
try with ```
acpi_osi="Linux"
```
especially if running ```
dmesg | grep Linux
``` prints a message where they are asking you to try this option out.

---

### Post by grindboy on 2010-02-05
Hi sarthorks

Thanks for the reply I've now discovered that ubuntu 8.10 runs on my tablet Without the need for acpi=off. I've now got brightness controls, battery meter, compiz and even cpu scaling working ootb.Any thoughts as to why 8.10 works where 9.10 failed?

Cheers

Grindboy

---

