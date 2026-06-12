---
title: "Help with Rocketraid 3120 and Kernel 2.6.31"
date: 2009-12-12
forum: Hardware
---

### Post by SuluOnBoard on 2009-12-12
I upgraded to Ubuntu 9.10 and the latest kernel, which includes the hptiop driver for the Rocketraid 3120. Everything seems okay, as the hptiop driver is loaded and the two disks are seen as a single disk by the OS.  However, the Highpoint management software does not work.  The HPT server that interfaces with the hptiop driver will not install.  It fails looking for the hptiop driver and defaults to a hmptv6 driver.  Because of this, the command line interface does not work at all and says it cannot connect to the array.  The Highpoint open source driver won't compile under 2.6.31.  Any help is appreciated.

---

