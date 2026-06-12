---
title: "HP AMD Ryzen laptop touch screen failure"
date: 2018-08-06
forum: Hardware
---

### Post by alicia4542 on 2018-08-06
I have a **HP Envy x360 13z** laptop with:

[INDENT]smpboot: CPU0: **AMD Ryzen 5 2500U** with **Radeon Vega Mobile Gfx** (family: 0x17, model: 0x11, stepping: 0x0)
[/INDENT]

running **Ubuntu 18.04** and Linux **4.15.0-29-generic** #31-Ubuntu SMP.

I have not observed any issues with the AMD graphics, but both the touch-screen and pen input do not work.

In dmesg, I noticed this:

[INDENT]amd_gpio AMDI0030:00: Failed to get gpio IRQ: -22
amd_gpio: probe of AMDI0030:00 failed with error -22
[/INDENT]

Which may be related to the touchscreen failure, but I have not found any working solution.

Any tips?  Thank you in advance.

---

### Post by cady on 2019-01-19
HI,

i have the same model like yours, but i didn't dare to install ubuntu on the machine. 
may i know something? did the battery life do good on linux?

---

