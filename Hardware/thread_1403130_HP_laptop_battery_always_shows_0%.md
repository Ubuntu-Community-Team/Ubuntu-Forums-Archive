---
title: "HP laptop battery always shows 0%"
date: 2010-02-09
forum: Hardware
---

### Post by emackey3k on 2010-02-09
I have a HP Pavillion dv6000 with Ubuntu 9.10 installed.  The battery icon in the notification area always shows 0%.  The battery works and I am able to work with it on battery power I just don't have any indication of when it will turn off.  Any help would be appreciated.  

Below is the contents of /proc/acpi/battery/BAT0/info:
present:                 yes
design capacity:         6000 mAh
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     150 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

Below is the contents of /proc/acpi/battery/BAT0/state while on battery power.
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      3808 mAh
present voltage:         10356 mV

Below is the contents of /proc/acpi/battery/BAT0/state while plugged in.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         10134 mV

---

