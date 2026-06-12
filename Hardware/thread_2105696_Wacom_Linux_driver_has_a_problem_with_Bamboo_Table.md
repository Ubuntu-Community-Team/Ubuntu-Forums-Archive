---
title: "Wacom Linux driver has a problem with Bamboo Tablets"
date: 2013-01-16
forum: Hardware
---

### Post by Bao2 on 2013-01-16
The wacom linux driver has a problem with Bamboo tablets: instead giving out a pen pressure value in the range 0 to 2047, gives out a value in the range 0 to 1023.

So in a program like gimp you can paint a line with a big brush and Dynamics off and compare with Dynamics on using same brush: at maximum pressure it never will go to same width.

The Bamboo series is a tablet that has 1024 levels of pressure, the driver would map it to the 2048 levels and output that to the applications, as it says in some page I have read. Instead the bug is that this mapping is not being done and with Bamboo tablets the value output to the applications is in the range 0 to 1023. So at maximum pressure in your Bamboo tablet, the application thinks you are applying half pressure.

Please someone that reports this bug. I was unable to do.

---

