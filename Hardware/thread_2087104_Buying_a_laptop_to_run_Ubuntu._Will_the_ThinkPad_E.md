---
title: "Buying a laptop to run Ubuntu. Will the ThinkPad Edge E135 (3359-62G) do?"
date: 2012-11-22
forum: Hardware
---

### Post by mikae1 on 2012-11-22
I'm looking to buy my first dedicated laptop for running Ubuntu/Xubuntu. I have found the machine below for a very good price. I can't find (m)any Linux reports for this Lenovo and I know Radeon isn't known for its Linux compatibility. But, do you think this will work?

```

Model           Lenovo ThinkPad Edge E135 (3359-62G) NZV62MS
Processor       AMD E-Series E-300 1.3 GHz
GPU             AMD Radeon HD6310M
RAM             4 GB DDR3
HDD             320 GB, 7200 RPM
Screen          11.6" LED
Resolution      1366 x 768
```The E135 is listed here:
[http://www.ubuntu.com/certification/hardware/201206-11151/](http://www.ubuntu.com/certification/hardware/201206-11151/)
But the GPU isn't named and it has a slightly different CPU.

Thanks in advance...

---

### Post by SupaDucta on 2012-11-23
seems to work, just got one, wireless won't work out of the box (still trying to make it work) and proprietary radeon driver will crash x once activated but all that can be circumvented with a certain amount of the hours spent as I gather

---

### Post by mikae1 on 2012-11-23
> **SupaDucta said:**
> seems to work, just got one, wireless won't work out of the box (still trying to make it work) and proprietary radeon driver will crash x once activated but all that can be circumvented with a certain amount of the hours spent as I gatherThanks you for the feedback! :KS
If possible, I (and perhaps others) would be really thankful if you could post some hints on how/if you got wifi and graphics working properly. 
What wifi chipset does it have BTW, I can't see that in the product listing.

---

### Post by str0hhalm on 2012-12-05
The WIFI Chipset is from broadcom. The ubuntu packagesource contains the driver. 
But note you can only use wifi in full speed and range after installing the broadcom driver.

There are some issues using ubuntu on the e135

1. If you start the system out of suspend mode, the screen will not come back up.
2. There is an bug with the manual control of the brightness of the screen. You can reduce the brightness correctly, but on the last two steps it will switch back to full brightness.

I've buyed it last week and i'm trying to find out how to fix these two problem. 

PS: It would be nice if someone have an idea how these two problems can be fixed

---

