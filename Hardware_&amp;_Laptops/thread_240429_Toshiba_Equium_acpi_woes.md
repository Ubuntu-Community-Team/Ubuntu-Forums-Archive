---
title: "Toshiba Equium acpi woes"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by bobalot on 2006-08-20
My new lappy is a Toshiba Equium M50, and suprisingly, everything seems to work, the wifi and sound worked from boot, the ati card, the radeon Xpress 200M, which only has support witht the drivers from the ati.com site and not the repos, is running fine, with Xgl + Quinn Compiz. My only problem is when trying to use the toshiba tools, they moan about the toshiba(-acpi) module being missing, and sure enough it is. and when i try to modprobe it

```
root@bob-laptop:/home/bob# modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.15-26-686/kernel/drivers/char/toshiba.ko): No such device

```

:o 

```
root@bob-laptop:/home/bob# lsmod | grep "toshiba"
root@bob-laptop:/home/bob# lsmod | grep "acpi"
sony_acpi               5580  0 
pcc_acpi               12416  0 
dev_acpi               11236  0 
acpi_sbs               20172  0 
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
root@bob-laptop:/home/bob# 

```

and theres some sony acpi instead, the fan is set to automatic when i use dapper, spinning up when it has to, but id like to use the toshutils to set it to full on for the extra cool...
any help would be greatly apreciated, and thank you in advance

---

