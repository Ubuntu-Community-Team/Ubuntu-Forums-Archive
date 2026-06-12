---
title: "Zip100 Parallel Port Disk ppa question"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by jnorthr on 2007-07-23
Other HowTo guides here suggest adding a line in /etc/modules to include a module known as ppa.
Another guide also suggests using the SG module - to provide generic scsi support for the ppa module. Which one should be loaded first ?

I just cannot get my zip drive recognised on the parallel  port (which has NO printer) even with or without the cups printer service and lp0. I know dmesg shows parport0 recognition at boot time. I feel like i've tried most every combination of modules and +/- lp0 none of which even touches the zip drive.  

My dmesg shows ppa version 2.07 loading as user space module but does not provide any 'scsi found' or any other config. details.:confused:

---

