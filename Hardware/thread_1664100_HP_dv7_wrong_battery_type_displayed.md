---
title: "HP dv7 wrong battery type displayed"
date: 2011-01-10
forum: Hardware
---

### Post by 3602 on 2011-01-10
I have just noticed that the battery icon is about always on in the top panel. When I click on it and select Laptop Battery, it says Nickel Metal Hydride while on the battery pack itself, it says Li-Ion. Also the charge light is always "charging" (orange, fully charged is white).
Is this a Ubuntu/Gnome problem, or can this be a battery, or worse, BIOS problem?
Thank you very much.

---

### Post by 3602 on 2011-01-11
Bump.

---

### Post by 3602 on 2011-01-26
Bump.

---

### Post by 3602 on 2011-01-29
Interestingly after installing *acpi* through *apt-get*, the power light would flicker randomly even after the computer is shut down (not sleep, not hibernate) and power cord pulled. I then *apt-get purge acpi* then reboot. The problem *seems* to have disappeared.

---

### Post by 3602 on 2011-01-29
Alright. I did not test booting on battery, but upon pulling the cord (which HP explicitly warns *not* to do) the screen dims and the discharge icon comes up. The battery is not correctly identified as Li-ion, but no discharge rate info (wattage) is available. So I can only rely on the little fuel gauge that actually happens to decrease after a while.

---

