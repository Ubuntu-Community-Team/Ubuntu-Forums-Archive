---
title: "Dell inspirion 15 7570 fan not spinning at full speed"
date: 2019-01-27
forum: Hardware
---

### Post by vijayk008 on 2019-01-27
Hi

I have recently installed Ubuntu 18.04.1 LTS. the fan won't spin at full speed causing the system to reach 90C or above. I didn't had this problem with windows. I am also new to linux, please anyone tell me how can I fix it.

thanks
vijayk008

---

### Post by CatKiller on 2019-01-27
The fan speed is controlled by the BIOS. Adjust your settings there if you want a more aggressive fan curve.

Otherwise you can install **lm-sensors** and **fancontrol** if you want to set your own thresholds in software.

---

### Post by vijayk008 on 2019-01-28
Also the i5-8250u never goes above 2.7Ghz even on light load

---

