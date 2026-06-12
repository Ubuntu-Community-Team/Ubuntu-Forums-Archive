---
title: "Inspiron 5150 dying after battery recharge"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by airhead on 2005-04-29
I have an Inspiron 5150 that keeps dying a little while after the battery is charged (~30mins at a guess). Maybe its a coincidence, but it only ever dies when I'm not using it, and its happened about 5 or 6 times now. I've been able to stop it dying by unplugging the battery after charging.

I have reason to believe that its the ACPI in the hoary kernel as this laptop was working fine with gentoo installed (and an older kernel - 2.6.5 iirc) and I've heard lots of people having problems with ACPI in hoary. Also, ACPI support does seem a little bit flakey on this machine as it can't tell when the AC or battery are plugged/unplugged (/proc entries still exist for battery even after battery disconnected). However, it does know the battery charge level and when the battery is discharging/charging.

Any help would be appreciated. If you have the same problems or no problems at all with this model, please let me know!

---

