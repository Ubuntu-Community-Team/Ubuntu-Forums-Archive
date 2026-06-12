---
title: "Battery charging only 50% -- acpi strange behaviour"
date: 2009-02-25
forum: Hardware
---

### Post by JW3 on 2009-02-25
Hi, I am not sure whether the problem is acpi / Ubuntu, or whether it is the battery.

I bought a new battery for my X40 laptop. It is not an original IBM battery and in theory should run for more than four hours. At first it did, too. That was a few weeks ago and I was carefull to minimise the battery wear (no full charging except for first 3 times, no full discharges etc.)

Now the battery is behaving strangely. When I charge it, acpi shows it coming to 49%, then being stuck for a while at that level, and then suddenly going to 100%. This corresponds to the "remaining charge" from /proc/acpi/battery/BAT0/state.

When I discharge the battery, it starts at 100%, goes slowly to 50%, and then dies without warning. I have tried to "callibrate" the battery (full charge/discharge) but to no effect.

Any ideas?

j.

---

