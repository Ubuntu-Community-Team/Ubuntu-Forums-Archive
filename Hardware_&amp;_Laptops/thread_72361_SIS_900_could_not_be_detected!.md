---
title: "SIS 900 could not be detected!"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by cantor on 2005-10-06
Can anybody tell me whether Ubuntu 5.04 support onboard SIS 900 ethernet adapter? when i install Ubuntu 5.04 from iso on hard disk, the installation said no ethernet adapter found. And the official SIS.com only provide the driver for kernel 2.4. What shoul I do?

---

### Post by jasmuz on 2005-10-06
The SiS Onboard Ethernet adapter is recognized by Ubuntu, as it has worked for me.

---

### Post by ranf on 2005-10-07
[QUOTE=cantor]Can anybody tell me whether Ubuntu 5.04 support onboard SIS 900 ethernet adapter? when i install Ubuntu 5.04 from iso on hard disk, the installation said no ethernet adapter found. And the official SIS.com only provide the driver for kernel 2.4. What shoul I do?[/QUOTE]

It works here as well.

First check if the hardware is found:
```
lspci | grep 900
```

---

