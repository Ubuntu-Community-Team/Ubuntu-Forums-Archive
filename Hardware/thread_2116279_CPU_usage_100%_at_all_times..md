---
title: "CPU usage 100% at all times."
date: 2013-02-15
forum: Hardware
---

### Post by gunnerbob101 on 2013-02-15
Installed Ubuntu 12.10 x64 on my second HDD, chose sdb, created partions,  everything went right.
But as soon as I boot into the desktop, fans on my PC go crazy and using the system monitor I see that CPU usage is 100%.
PC has Athlon II x4 640, 4GB DDR3, GB GA870A-USB3, and ATI HD 5770.
I have read that the problem is probably caused by AMD drivers, but when I try to install AMD drivers for linux the progress bar is so slow, even for a 100 mb file. Is there a way to roll back to some generic-VGA driver on Ubuntu, as is on Windows?
Though if you have any better advice then let me know.

---

### Post by QIII on 2013-02-15
Would you please post back the results of the following command in the terminal?```
top
```

Press CNTL+Shift to stop updating, highlight the text and press CNTL+Shift+c

---

### Post by Mark Phelps on 2013-02-15
> **gunnerbob101 said:**
> ...
I have read that the problem is probably caused by AMD drivers, 
I'm running the default Radeon driver and am experiencing none of this.
> but when I try to install AMD drivers for linux the progress bar is so slow, even for a 100 mb file. Is there a way to roll back to some generic-VGA driver on Ubuntu, as is on Windows?
Unless you completed the restricted AMD driver installation, you're still running on the default open-source Radeon driver. I'm using that and my multi-core AMD CPU shows no more than 4% utilization -- unless I'm specifically running something CPU-demanding.

---

