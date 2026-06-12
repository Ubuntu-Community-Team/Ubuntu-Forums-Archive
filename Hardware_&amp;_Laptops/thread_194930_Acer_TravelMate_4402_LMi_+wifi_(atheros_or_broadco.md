---
title: "Acer TravelMate 4402 LMi +wifi (atheros or broadcom)"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by awgan on 2006-06-12
I've installed brand new Dapper on my laptop with ACPI support. But when it comes to wireless ( no matter if it is an original bcm43xx+firmware or atheros 5212A )  some software ( if I recall wpa_gui ) says, that I should turn this adapter on by pushing button on my laptop. In dmesg is a part that says everything is fine with wireless, eth0/ath0 is present, iwconfig shows adapter, but &#8220;iwlist eth0/ath0 scan&#8221; says this device don't support scanning or something similar. Pushing wireless button gives no effect, led is always off and nothing changes in dmesg/iwconfig/ifconfig/iwlist. I&#8217;ve also tried Suse 10.1 with the same result. Is this an ACPI problem (should I turn it off during install), buggy laptop (bios 1.20) or should I recompile kernel? Or maybe some other suggestions. 
Anyone has any success running wireless on TravelMate 4402 with any Linux? 

Thanx

---
EDITED
---
acer_acpi lot of google and it works.

---

