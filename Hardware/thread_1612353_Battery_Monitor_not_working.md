---
title: "Battery Monitor not working"
date: 2010-11-03
forum: Hardware
---

### Post by archithcr on 2010-11-03
Hi all  I have an HP DV6 3143 and am running ubuntu 10.10 64 bit on it. i am having a problem with the battery monitor. I installed ubuntu two weeks ago and since then, the battery monitor never tells me how much time i have left when i unplug my laptop.  It seems to be stuck in " Laptop Battery (Estimating". When i click on it, it is able to give me info on total capacity, discharging rate and so on, but not how much time i have before battery drains completely.  Does anyone have any suggestions? :)  Thanks

---

### Post by P4man on 2010-11-03
Its only when you unplug the power cord? Is the unplugging detected (you should get a popup) ? In the detailed battery info does it show percentage and time to empty, or just one or neither?

BTW, you can already try this; press alt+f2 and run

```
gconf-editor
```

and browse to 

/apps/gnome-power-manager/general/use_time_for_policy

uncheck it. I think it requires logging out and in, maybe even a reboot to take effect.

---

### Post by archithcr on 2010-11-04
hi  i tried the tip you gave, but doesn't seem to work. In the detailed statistics page, i get information on Percentage remaining, but under time to full and time to drain, it says 0 seconds.  Help :(

---

### Post by P4man on 2010-11-04
Can you post the output of
```
upower --dump
```

preferably with a nearly full charge and one a bit later, so the battery has drained a bit?

---

### Post by archithcr on 2010-11-05
```


at full charge

Device: /org/freedesktop/UPower/devices/line_power_ACAD
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/ACPI0003:00/power_supply/ACAD
  power supply:         yes
  updated:              Fri Nov  5 08:58:03 2010 (34 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             no

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0
  vendor:               Hewlett-Packard
  model:                Primary
  power supply:         yes
  updated:              Fri Nov  5 08:58:09 2010 (28 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              54.2592 Wh
    energy-empty:        0 Wh
    energy-full:         54.2592 Wh
    energy-full-design:  55.08 Wh
    energy-rate:         0.0108 W
    voltage:             12.166 V
    percentage:          100%
    capacity:            97.8824%
    technology:          lithium-ion

Daemon:
  daemon-version:  0.9.5
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

Half an hour later

Device: /org/freedesktop/UPower/devices/line_power_ACAD
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/ACPI0003:00/power_supply/ACAD
  power supply:         yes
  updated:              Fri Nov  5 08:58:03 2010 (2997 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             no

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0
  vendor:               Hewlett-Packard
  model:                Primary
  power supply:         yes
  updated:              Fri Nov  5 09:47:41 2010 (19 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              33.8688 Wh
    energy-empty:        0 Wh
    energy-full:         54.2592 Wh
    energy-full-design:  55.08 Wh
    energy-rate:         0.0108 W
    voltage:             11.104 V
    percentage:          62.4204%
    capacity:            97.8824%
    technology:          lithium-ion
  History (charge):
    1288936031    62.420    discharging
    1288936001    63.057    discharging
    1288935971    63.694    discharging

Daemon:
  daemon-version:  0.9.5
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes



```

---

### Post by P4man on 2010-11-05
That all looks perfectly fine. I dont know why its not showing the time then, must be a bug. As a workaround check this thread:
[http://ubuntuforums.org/showthread.php?t=1601974&page=2](http://ubuntuforums.org/showthread.php?t=1601974&page=2)

Where the last poster basically installs the battery applet from 10.04 to workaround it.

---

