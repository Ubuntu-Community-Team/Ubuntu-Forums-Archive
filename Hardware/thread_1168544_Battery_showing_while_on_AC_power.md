---
title: "Battery showing while on AC power"
date: 2009-05-24
forum: Hardware
---

### Post by thofke on 2009-05-24
I've looked for some solution but found none. My NEC Versa P550 laptop (from 2005 or something) is showing a battery while on AC power. The GNOME power manager is displaying the message that the battery is decharging, but also that the computer is using AC power.

These are the contents of /proc/acpi/battery/BAT1/state:

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      3718 mAh
present voltage:         18900 mV

What is causing the problem?

---

### Post by Macchi on 2009-06-03
Get some more information with the command:
```
cat /proc/acpi/battery/BAT1/info
```
Some systems have it at /proc/acpi/BAT0/info or /proc/acpi/battery/BAT0/state.




PS: By the way I am experiencing problems with very inaccurate reports of battery "last full capacity". It is always erroneous on the two EEE models running 9.04 that we have in the family.

---

