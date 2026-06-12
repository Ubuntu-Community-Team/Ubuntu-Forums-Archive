---
title: "Acer AMD64 Overheats"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Joners on 2007-02-28
Ive got a bit of a problem with Ubuntu. Trying to install Ubuntu on my laptop Acer Aspire 1520WLMI (AMD Athlon 64 3400+, 1GB Ram) Ive managed to install it several times however I always get an overheating issue. Ive installed the 6.06LTS version 6.10, and 6.06LTS (64 Bit Version).

Each time that I use it and run a CPU intensive task the unit overheats and shuts down (when temp reaches about 50 degrees C)

Ive used windows Xp on this machine for a couple of years and run equally intensive tasks and never had a problem, still use it now as a dual boot machine.

I found a few posts that discuss adding the powernow-k8 module to the start up or disabling acpi however i dont know how to do either of these things and will they help?

Would appreciate any feedback that anyone has.

Thanks.

---

### Post by markitect on 2007-02-28
Linux's acpi is a little less robust then windows.  What chipset does the laptop run on? 
A good place to start would be to see if there is a bios update available (they shipped with old bios more often then not).  If there was a small acpi bug they may have fixed it.  you also might try installing powernowd
from the terminal you can do
```

sudo apt-get install powernowd

```

This has some advanced features that might be able to help out if the bios update isn't available or doesn't work.  I think there is also a config file that sets some of the power management features, but id have to check on my laptop later

---

### Post by Joners on 2007-02-28
Hi thanks for you answer, I checked under the services that are running and the "powernowd" service is checked and appears to be running.

There are no newer BIOS updates for my laptop, the last one was released about 12months ago and there wont be any new ones by the looks of things :(

Ive heard that there can be issues with Phoenix Bios and Ubuntu and ACPI support, this is only through going through various web pages and coming out with nothing helpful!

As per your question, the chipset is:

VIA K8M800 (Northbridge K8M800 + Southbridge VT8237 PCI Bridge (K8T800 South)

Let me know if you can think of anything else!

I really want to get this up and going, im sick of windows!

:D

---

