---
title: "ACPI Battery issue"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by lexilinux on 2006-01-21
Hi
I have a gateway laptop and have had acpi working in other distrobutions such as xandros with no extra work.

but in kubuntu my battery will not charge.

here is the output
> lexi@lexilinux:/proc/acpi$ cat battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mA
remaining capacity:      0 mAh
present voltage:         45184 mV

lexi@lexilinux:/proc/acpi$ cat battery/BAT1/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      506 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     100 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            OAL4$1
serial number:
battery type:            LION
OEM info:                SANYO




so now when i unplug the power shuts off imediatly.

any ideas?????????????

---

