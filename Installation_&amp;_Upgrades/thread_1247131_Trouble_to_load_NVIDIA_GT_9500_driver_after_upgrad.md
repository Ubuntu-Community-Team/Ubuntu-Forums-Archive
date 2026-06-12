---
title: "Trouble to load NVIDIA GT 9500 driver after upgrade to kernel 2.6.28-15"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by pcpain on 2009-08-22
Today I upgraded kernel 2.6.28-14 to 2.6.28-15. After the upgrade the driver for NVIDIA 9500 GT failed to load properly with the following message:

Ubuntu is running in low-graphics mode. The following errors encountered:
 (EE) NVIDIA: Failed to load NVIDIA kernel module. Please check your
 (EE) NVIDIA: system's kernel log for additional messages.
 (EE) Failed to load model "nvidia" (module specific error, 0)
 (EE) No driver available.

So I have to go back to the old boot option - using Kernel 2.6.28-14.

Any solutions will be appreciated.

---

### Post by darco on 2009-08-22
You need to re-install your drivers...

darco

---

### Post by pcpain on 2009-08-23
[SIZE=2]Darko,

Thanks for the suggestion that I implemented to my satisfaction.
[/SIZE]

---

### Post by RJARRRPCGP on 2009-08-23
> **darco said:**
> You need to re-install your drivers...

darco

You normally are not required to reinstall them yourself! 

It's a F-up, likely by jockey.

---

