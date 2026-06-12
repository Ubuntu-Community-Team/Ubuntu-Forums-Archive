---
title: "Excessive battery consumption in sleep mode"
date: 2021-11-30
forum: Hardware
---

### Post by bradhaack on 2021-11-30
Dell Vostro 15 7510 laptop.  Xubuntu 21.04.
Pretty new laptop with clean Xubuntu installation.  It uses about 38% of the battery per hour while in suspend/sleep mode.  It is going into deep sleep mode.  One of the last entries in the syslog is:   ```
kernel: [10448.944851] PM: suspend entry (deep)
```
Hibernate does not appear to be an option available?
What could be causing this?    How to debug?

---

### Post by Autodave on 2021-12-01
Since no one else has jumped in.....and this has worked before......disconnect any USB hub, especially powered one(s), and see if that helps.

---

### Post by bradhaack on 2021-12-01
I don't have any USB hubs connected

---

### Post by bradhaack on 2021-12-08
Updating the OS to 21.10, update the bios (1.3.0) to the latest, and setting the sleep mode to s2idle has hopefully fixed my suspend issues.
Summary:
New lapttop, intalled Xubuntu LTS 20.04
I had issues with battery consumption.
Updated the Bios to 1.2.1 (the latest at the time)
Updated the OS to Xubuntu 21.04
Changed the sleep mode to deep (was s2idle)
Installed tlp
Updated the OS to Xubuntu 21.10 & the Bios to 1.3.0
I did all of the above changes incrementally and still had issues.
Change sleep mode back to s2idle

After a couple of days testing I haven't had any reboots when waking, or excessive batt consumption when suspended.
Hopefully problem solved.

---

