---
title: "SYNA3602 Touchpad not working"
date: 2019-10-12
forum: Hardware
---

### Post by ea123 on 2019-10-12
Hi,

I have a non-working SYNA3602 touchpad on a Trekstor Prime book C11B notebook.
I am on Xubuntu 19.04.

There are a few threads on problems with this touchpad on different forums (most threads from 2018) and a patch available under the following link:
[https://github.com/brotfessor/sipodev](https://github.com/brotfessor/sipodev)

Though, the patch should be included in the mainline Kernel since Linux v4.19 and I have tried different Kernels from 5.0 upwards. Currently I am running 5.2.0-050200-generic.

dmesg | grep -i i2c-syna gives me the follwing output:
```

[    3.039251] i2c_hid i2c-SYNA3602:00: i2c-SYNA3602:00 supply vdd not found, using dummy regulator
[    3.039281] i2c_hid i2c-SYNA3602:00: i2c-SYNA3602:00 supply vddl not found, using dummy regulator
[    3.045751] i2c_hid i2c-SYNA3602:00: unexpected HID descriptor bcdVersion (0x00ff)

```

Is anybody able to help me ?

Thank you in advance!
ea

---

