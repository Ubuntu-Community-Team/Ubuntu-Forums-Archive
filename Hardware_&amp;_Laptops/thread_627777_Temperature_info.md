---
title: "Temperature info"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by merike on 2007-11-30
How do you find out all temperature information possible? So far I know of acpi -t that showed processor temperature. I have lm-sensors installed as well, but I'm unsure how to use it.
Any guidance?

---

### Post by nick_h on 2007-11-30
The package gkrellm gives you a front-end to lm-sensors.  The package sensors-applet allows you to display sensors information as an applet in a panel.

There is also a package called hddtemp that lets you read hard drive temperatures.

---

