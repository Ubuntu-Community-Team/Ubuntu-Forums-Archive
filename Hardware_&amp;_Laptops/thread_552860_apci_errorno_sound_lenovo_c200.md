---
title: "apci error/no sound: lenovo c200"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by jasc on 2007-09-17
Hi, I have no idea what's wrong. here's the output from dmesg | grep acpi

[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   25.284791] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.287721] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   21.228000] ibm_acpi: ec object not found
[   21.268000] pcc_acpi: loading...
[  322.292000] ACPI Exception (acpi_battery-0207): AE_NOT_FOUND, Evaluating _BST [20060707]
[  412.344000] ACPI Exception (acpi_battery-0207): AE_NOT_FOUND, Evaluating _BST [20060707]


I've been trying to fix the sound on my computer (Lenovo C200) by following the howto at [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG), but there are errors in the compilation of the alsa-lib and alsa-utils, it says "nothing to do for install-exec-am" and "nothing to do for install-data-am" several times for both. Any ideas?

Thanks for any help.

---

### Post by jasc on 2007-09-18
also, it no longer finds any soundcard.

---

