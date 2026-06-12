---
title: "Syslog ERROR: ACPI-0423, ACPI-0508, ACPI-0171 ... any ideas on how to fix?"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by stein on 2006-04-19
Hey everyone,

I performed a Breezy Server Install.

The following errors appear in syslog during system boot:

```
Apr 18 16:39:23 localhost kernel: [   23.997756] PCI: Using ACPI for IRQ routing
Apr 18 16:39:23 localhost kernel: [   23.997763] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 18 16:39:23 localhost kernel: [   23.997857] PCI-DMA: Disabling IOMMU.
Apr 18 16:39:23 localhost kernel: [   23.998083]     ACPI-0423: *** Error: Handler for [SystemMemory] returned AE_AML_ALIGNMENT
Apr 18 16:39:23 localhost kernel: [   23.998090]     ACPI-0508: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff81003ce22dc0), AE_AML_ALIGNMENT
Apr 18 16:39:23 localhost kernel: [   23.998167]     ACPI-0171: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff81003ce22dc0), AE_AML_ALIGNMENT
```

I ran apt-get update and apt-get upgrade but no change.
The errors still show up on reboot.

Any ideas on what they refer to, whether they are dangerous, inhibiting system functionality, and/or how to get rid of them?

thanks a million in advance,

Stein

---

### Post by ranf on 2006-04-20
It looks like the DSDT table of the ACPI-BIOS is somewhat broken.

[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
[http://acpi.sf.net/](http://acpi.sf.net/)

---

