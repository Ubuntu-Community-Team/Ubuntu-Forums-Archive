---
title: "how can i install touch driver for chuwi hi8 air ?"
date: 2018-12-18
forum: Hardware
---

### Post by furkan161 on 2018-12-18
[COLOR=#242729][FONT=Arial][FONT=inherit]hello i am trying to install touch driver for my chuwi hi8 air tablet here is the links i am using : [https://github.com/onitake/gslx680-acpi](https://github.com/onitake/gslx680-acpi)[/FONT]
[FONT=inherit]i clone the git then i write make command after that i write this to the terminal sudo insmod ./gslx680_ts_acpi.ko but when i check to the dmesg it writes this error : [  257.261030] gslx680_ts_acpi: loading out-of-tree module taints kernel.[  257.261193] gslx680_ts_acpi: module verification failed: signature and/or required key missing - tainting kernel[  257.272214] gslx680 i2c-MSSL1680:01: gsl_ts_probe: got a device named MSSL1680:01 at address 0x40, IRQ 184, flags 0x0[  257.272304] gslx680 i2c-MSSL1680:01: Direct firmware load for silead_ts.fw failed with error -2[  257.272309] gslx680 i2c-MSSL1680:01: gsl_ts_probe: failed to load firmware: -2[  257.286110] gslx680: probe of i2c-MSSL1680:01 failed with error -2[/FONT]
[FONT=inherit]can some one can explain with steps, how can i install this touch driver ? thanks.[/FONT]
[FONT=inherit]oh and my ubuntu version is: Ubuntu 16.04.3 LTS[/FONT]


[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][/FONT][/COLOR]

---

