---
title: "Problem booting beige G3MT with Acard 6280M"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by jshamlet on 2005-11-06
Hello,
I am trying to boot Ubuntu 5.10 on a beige G3 minitower. Due to the extremely slow speed of the onboard ATA controller, I installed an Acard 6280M ATA-133 controller. I am using BootX 1.2.2, and the vmlinux supplied with the install ISO.

The installer finds the ATA card just fine, and did the install - but when I try to boot, the kernel can't find the controller. I suspect that this is due to the driver not being compiled into the vmlinux image I'm booting.

I would just mount the drive on the onboard controller, but apparently Mac OS thinks that the Acard is a SCSI controller. It refuses to boot an install done on the Acard controller with the onboard controller or vice-versa. I would rather not reformat the drive and start over at this point, though I might could entertain adding a second drive to that controller.

So, at this point, I have a few questions. If the problem is that the supplied linux kernel doesn't have the acard driver compiled in, where can I get one that does have it compiled in? (Would some kind stranger possibly supply such a kernel?) ;) 

Alternately, is there a way to boot the live CD and compile a kernel I can boot from bootX. 

Thanks!

---

