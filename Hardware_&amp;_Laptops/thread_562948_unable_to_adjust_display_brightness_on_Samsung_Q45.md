---
title: "unable to adjust display brightness on Samsung Q45 &quot;Duke&quot;"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by lepidopteraphobiac on 2007-09-29
Hello guys,

I just got myself a Samsung Q45 Damali and installed Feisty 64bit on it.
Problem is: quite unlike the LaptopTestingTeam at [https://wiki.kubuntu.com/LaptopTestingTeam/SamsungQ45?highlight=%28CategoryLaptop%29]("https://wiki.kubuntu.com/LaptopTestingTeam/SamsungQ45?highlight=%28CategoryLaptop%29")
I couldn't get the function keys to adjust the display brightness.
The laptop has a nvidia 8400M and I installed the drivers using envy.

I wonder if the problem could be ACPI-related because *dmesg|grep acpi *returns ```
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   47.774666] ACPI Exception (acpi_video-1564): UNKNOWN_STATUS_CODE, Cant attach device [20060707]
[   48.031581] ibm_acpi: ec object not found
[   48.073918] pcc_acpi: loading...

```.
please help!

-lepidopteraphobiac

---

