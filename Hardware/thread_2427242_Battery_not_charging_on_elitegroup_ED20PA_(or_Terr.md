---
title: "Battery not charging on elitegroup ED20PA (or Terra 360-11 from Wortmann)"
date: 2019-09-19
forum: Hardware
---

### Post by 785utnubu on 2019-09-19
Ubuntu 19.04 worked ok on this notebook/tablet hybrid including touch functionality. However, after the battery was discarged to 0% it can now not charge anymore. It is recognized

```

upower -i /org/freedesktop/UPower/devices/battery_BAT1
```

yields

```
  native-path:          BAT1
  vendor:               Standard
  model:                ED20PA
  serial:               00001
  power supply:         yes
  updated:              Do 19 Sep 2019 20:12:43 CEST (107 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         23,7815 Wh
    energy-full-design:  37,5375 Wh
    energy-rate:         0 W
    voltage:             7,611 V
    percentage:          0%
    capacity:            63,3538%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'

```

but ```
acpi -b
``` says
```

Battery 0: Unknown, 0%
```

The usual tricks like holding powerbutton pressed until the computer shuts down and starting again do not work.

It also does not charge if the laptop is switched off.

The BIOS does not have any battery related settings either.

---

