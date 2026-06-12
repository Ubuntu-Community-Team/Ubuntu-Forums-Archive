---
title: "Frequency Scaling problem with Ubuntu &gt;= 6.10 on Vaio VGN-FS215M"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by novaWizo on 2007-02-04
Hi to everyone,

I have got a Sony Vaio VGN-FS215M currently with 6.06 LTS Dapper; everything works fine, both CPU frequency scaling and LCD brightness control through gnome-power-manager.

But when I tryed Ubuntu Edgy 6.10,  frequency scaling didn't work and I found this error in logs (honestly I have several other regression bugs in Ubuntu Edgy 6.10  but they are another story):

```

[17179572.556000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.556000] ACPI: Processor [CPU0] (Support 8 throttling states)
[17179572.556000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.556000] ACPI: Getting cpuindex for acpiid 0x1

```

Same thing in Festy Herd 3:

```

[   45.043832] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   45.044019] ACPI: Processor [CPU0] (supports 8 throttling states)
[   45.044166] ACPI Exception (acpi_processor-0680): AE_NOT_FOUND, Processor Device is not present [20060707]
[   45.044325] ACPI: Getting cpuindex for acpiid 0x1

```

All test were made with Desktop LiveCD.

There is a solution or I must make a segnalation on launchpad?

---

### Post by novaWizo on 2007-02-05
up

---

### Post by novaWizo on 2007-02-09
up

---

