---
title: "Problem with detecting acpi events on Vaio SZ650"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by arjunrc on 2008-02-15
Hello, I am running ubuntu 7.10 on a vaio sz650. I can't seem to detect any acpi events when I run acpi_listen and press the power button 

My dmesg log for acpi:
```

arjun@arjun-ubuntu:~$ dmesg | grep acpi
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   15.950070] ACPI: Please test with "acpi_osi=!Linux"
[   15.950071] Please send dmidecode to linux-acpi@vger.kernel.org
or any Fn+key combo

```

lsmod:
```
lsmod | grep acpi
sony_acpi               6412  0 

```

I know my fn keys work because when I hit fn+f2 volume decreases etc. All except my brightness works (as reported by many in other threads)

I want to enable acpi because I want to customize events.

thanks

---

### Post by arjunrc on 2008-02-17
hello, any help on this?

---

