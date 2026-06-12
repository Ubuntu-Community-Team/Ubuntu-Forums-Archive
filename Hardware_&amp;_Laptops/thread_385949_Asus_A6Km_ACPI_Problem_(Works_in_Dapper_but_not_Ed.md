---
title: "Asus A6Km ACPI Problem (Works in Dapper but not Edgy)"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by mar29 on 2007-03-16
Hi

I have looked at many sites and seen this problem mentioned all over the place but no solution.

I have the latest Asus A6Km bios installed and cannot get ACPI to work on Edgy.
I previously had Dapper installed and ACPI worked fine, but now it doesn't.

I looked in System Services and found acpid was not on.
I tried restarting the acpid to see if that is the cause and it won't work.
dmesg outputs: 

> [17180354.588000] ibm_acpi: ec object not found


It seems to be something to do with the kernel, apparently downgrading the kernel to 2.6.15 works... but that seems a waste of upgrading to Edgy.

I also have problems running the BCM4318 wireless chipset as although Edgy detects and installs everything it cannot see any networks, whereas in Dapper it could. (Using Ndiswrapper in both cases)

Please can someone help :D

Cheers

Mark

---

