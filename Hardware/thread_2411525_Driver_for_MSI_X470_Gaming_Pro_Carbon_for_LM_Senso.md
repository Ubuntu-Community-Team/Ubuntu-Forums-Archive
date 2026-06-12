---
title: "Driver for MSI X470 Gaming Pro Carbon for LM Sensors"
date: 2019-01-31
forum: Hardware
---

### Post by shag00 on 2019-01-31
I seem to have identified the hardware monitor for this board [https://www.inet.se/files/pdf/1901191_0.pdf](https://www.inet.se/files/pdf/1901191_0.pdf)

Which clearly states it's a NUVOTON NCT6795 Controller Chip. So following on from some information obtained in a post regarding another system I recently built, I used that to invoke  NCT6775 (NCT6795 is supported by this driver), see here:
[https://ubuntuforums.org/newthread.php?do=newthread&f=332](https://ubuntuforums.org/newthread.php?do=newthread&f=332)
[https://www.kernel.org/doc/Documentation/hwmon/nct6775](https://www.kernel.org/doc/Documentation/hwmon/nct6775)

I am able to get some data from this driver but it is not accurate (1 fan spins up to 67,000 RPM). I also think I need the driver for the processor, a Ryzon 2600X (CPU fan and core temps), I cannot find any information on this.

So feeling completely out of my depth, I was wondering if anyone could point me in the right direction.

---

