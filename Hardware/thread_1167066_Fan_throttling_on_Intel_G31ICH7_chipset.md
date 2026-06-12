---
title: "Fan throttling on Intel G31/ICH7 chipset?"
date: 2009-05-22
forum: Hardware
---

### Post by SatanzJudge on 2009-05-22
I would like to control the CPU fan speed (in userspace) since the fan is very loud when running at max. The mainboard is a [MSI G31M2 V2]("http://www.msi.com/index.php?func=prodmbspec&maincat_no=1&cat2_no=170&cat3_no=&prod_no=1294") with an Intel G31/ICH7 chipset. The CPU is a Celeron 440. I know that the Celeron doesn't have Speedstep (CPU scaling) but it should be possible to adjust the fan speed or read the CPU temperature at least.

The folder /proc/acpi/thermal_zone is empty so I guess that a required kernel module is missing (not loaded)? Kernel is vanilla 2.6.29.3.

Thanks for any help!

---

