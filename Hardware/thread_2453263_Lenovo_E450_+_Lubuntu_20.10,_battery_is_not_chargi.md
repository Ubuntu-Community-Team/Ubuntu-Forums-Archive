---
title: "Lenovo E450 + Lubuntu 20.10, battery is not charging"
date: 2020-11-06
forum: Hardware
---

### Post by wugubee on 2020-11-06
I have Lenovo E450 and Lubuntu 20.10,
I did try use "Suspend" option,
I guess after that, I finally noticed that my battery is not charging anymore,

So I thought it was dead battery, so I buy new one, replace it, but found out it still have not resolved, 

So I browse around, and found out my situation is not unique, some people experience it with Linux,

Now Im quite sure this is not hardware problem, it just related to software, any suggestions? Thank you,

below is my upower

```

~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               LGC
  model:                LNV-45N1
  serial:               13659
  power supply:         yes
  updated:              Jum 06 Nov 2020 07:33:30  (16 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               pending-charge
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         44,28 Wh
    energy-full-design:  44,49 Wh
    energy-rate:         0 W
    voltage:             8,576 V
    percentage:          0%
    capacity:            99,528%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'
```

---

