---
title: "laptop battery &quot;full,&quot; not delivering power!"
date: 2015-09-02
forum: Hardware
---

### Post by Zestie Bumwhig on 2015-09-02
According to my on-screen info, my battery is 100%. But if I pull out the power cord, the laptop shuts off immediately.

I'm using LXLE 12.10.05. I also tried live-booting with a few different distro CDRs (Crunchbang & KXStudio), but they gave the same weird battery behaviour. It seems to me that the laptop sees the battery, but won't charge it, and won't draw power from it.

I just bought a new battery, thinking there was a really good chance the old one was kaput. No luck - same issue (but 68%). My guess is, something is irrevocably fouled up in the laptop now (it's quite old, and there had been a weird/bad connection in the AC plug-in jack). Also, note that my /proc/acpi/battery says "non-rechargeable"!

BIOS doesn't seem to offer any battery options. This is a 2006 Sony Vaio PCG-792L, if anyone's curious.

Thanks. I'd love to get any feedback at all!

Some info:

scuttlebutt@gormenghast:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0
  vendor:               Sony Corp.
  power supply:         yes
  updated:              Tue 01 Sep 2015 12:14:31 AM PDT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              10 Wh
    energy-empty:        0 Wh
    energy-full:         10 Wh
    energy-full-design:  10 Wh
    energy-rate:         0 W
    percentage:          100%
    capacity:            100%
    technology:          lithium-ion
  History (charge):
    1441091671    0.000    unknown
  History (rate):
    1441091671    0.000    unknown


proc/acpi/battery/BAT0 is:

present:                 yes
design capacity:         10000 mWh
last full capacity:      10000 mWh
battery technology:      non-rechargeable
design voltage:          unknown
design capacity warning: 1000 mWh
design capacity low:     400 mWh
cycle count:          0
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.


$ acpi -b
Battery 0: Discharging, 100%, rate information unavailable

---

