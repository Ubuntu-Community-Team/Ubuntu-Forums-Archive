---
title: "Battery state incorrect when resuming - 16.04"
date: 2016-11-12
forum: Hardware
---

### Post by keithspg on 2016-11-12
There is a closed thread on this from 2010 or so. Running 16.04

I just got a new Asus X55VX. Nice computer after I replaced the spinn-y hard drive with an SSD. All works great except the battery indication after a resume. This is our community laptop at home and it suspends when not in use. The touchpad 'works' but I prefer a mouse. I find this giant touchpad awkward.

If I remove the battery, disconnect the power supply and hold the power button to discharge it, on next boot it reports battery status correctly. All is well until it suspends. When I resume it, the battery is always discharging and it does not detect a charger connected nor that it is 'fully charged'.

This is the upower after a resume. It is physically connected to the power supply and the battery is fully charged. I have tried letting it fully discharge and then recharging it. It works fine until it suspends. Any suggetions?

```
upower --dump
Device: /org/freedesktop/UPower/devices/line_power_AC0
  native-path:          AC0
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:35:36 PM CST (346 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUSTeK
  model:                ASUS Battery
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:39:36 PM CST (106 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              42.345 Wh
    energy-empty:        0 Wh
    energy-full:         42.525 Wh
    energy-full-design:  45 Wh
    energy-rate:         3.72 W
    voltage:             15 V
    time to empty:       11.4 hours
    percentage:          100%
    capacity:            94.5%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'

Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Fx0002
  native-path:          /sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:046D:C52F.0002
  vendor:               Logitech, Inc.
  model:                Wireless Mouse
  serial:               1398F1C8
  power supply:         no
  updated:              Sat 12 Nov 2016 06:39:41 PM CST (101 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               unknown
    warning-level:       none
    percentage:          0%
    icon-name:          'battery-missing-symbolic'

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:37:36 PM CST (226 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               discharging
    warning-level:       none
    energy:              42.345 Wh
    energy-full:         42.525 Wh
    energy-rate:         3.72 W
    time to empty:       11.4 hours
    percentage:          100%
    icon-name:          'battery-full-symbolic'

Daemon:
  daemon-version:  0.99.4
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep
```

When I disconnect the power supply it is this
```
sudo upower --dump
Device: /org/freedesktop/UPower/devices/line_power_AC0
  native-path:          AC0
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:43:02 PM CST (2 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              no
    icon-name:          'ac-adapter-symbolic'

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUSTeK
  model:                ASUS Battery
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:43:02 PM CST (2 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              42.345 Wh
    energy-empty:        0 Wh
    energy-full:         42.525 Wh
    energy-full-design:  45 Wh
    energy-rate:         4.23 W
    voltage:             15 V
    time to empty:       10.0 hours
    percentage:          100%
    capacity:            94.5%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (rate):
    1478997782    4.230    discharging

Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Fx0002
  native-path:          /sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:046D:C52F.0002
  vendor:               Logitech, Inc.
  model:                Wireless Mouse
  serial:               1398F1C8
  power supply:         no
  updated:              Sat 12 Nov 2016 06:41:41 PM CST (83 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               unknown
    warning-level:       none
    percentage:          0%
    icon-name:          'battery-missing-symbolic'

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Sat 12 Nov 2016 06:43:02 PM CST (2 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               discharging
    warning-level:       none
    energy:              42.345 Wh
    energy-full:         42.525 Wh
    energy-rate:         4.23 W
    time to empty:       10.0 hours
    percentage:          100%
    icon-name:          'battery-full-symbolic'

Daemon:
  daemon-version:  0.99.4
  on-battery:      yes
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep

```

---

### Post by keithspg on 2016-11-18
Nobody else having this problem? This is the sole issue I have with this laptop.

---

