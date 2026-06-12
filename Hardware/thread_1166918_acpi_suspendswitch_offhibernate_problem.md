---
title: "acpi suspend/switch off/hibernate problem"
date: 2009-05-22
forum: Hardware
---

### Post by Big_Croc7 on 2009-05-22
Hi,
I've just installed Kubuntu 9.04. It won't shut down, hibernate or suspend to ram, and I'm guessing it's an acpi problem. With all 3, the system appears to shut down and the screen goes black, but the system stays powered on (for hours at least) and will only turn off with a hard shutdown (i.e. pressing the power button for more than 4 seconds), and when it's turned back on it thinks it's crashed. I've added acpi=force to the boot line, otherwise it doesn't give the suspend to ram option at all, and has usb errors on boot. I don't really know where to start looking - here's the output of dmesg | grep 'acpi'
```

[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

```

---

### Post by Big_Croc7 on 2009-05-22
After trial and error, the problem is my usb wireless adaptor... how do I fix it?

---

### Post by Big_Croc7 on 2009-05-23
Fixed, mostly, by unloading the wireless modules before suspending.

---

