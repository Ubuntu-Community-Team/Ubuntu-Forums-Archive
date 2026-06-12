---
title: "resume failure"
date: 2012-02-02
forum: Hardware
---

### Post by sebqas on 2012-02-02
I cant resume my PC (not a laptop) after suspension to RAM (command: pm-suspend).
Previously I was able to susped and hibernate easily, for some weeks not. 
Why ? I didn't change anything in the kernel or in the hardware.

The PC behaves as follows:
After pressing the button it tries to start  for a few seconds and than go to sleep again, and goes on without the end.

To know what is blocking the system  I used pm_trace 
according to the advice [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend):
The script is :
```

#!/bin/bash
sync
echo 1 > /sys/power/pm_trace
echo mem >/sys/power/state

```and then after reboot  I look at the demsg or kernel.log,
but they show nothing:

```

[    0.612616] PM: Resume from disk failed.
[    0.612625] registered taskstats version 1
[    0.612930]   Magic number: 0:695:71
[    0.612991] rtc_cmos 00:04: setting system clock to 2012-02-02 10:03:50 UTC (1328177030)

```any ideas?

---

### Post by sebqas on 2012-02-03
I forgot to mention that resume after hibernate is OK. 
Isn't it strange?

---

