---
title: "Rescale upower battery% for rechargeable mouse batteries?"
date: 2015-04-26
forum: Hardware
---

### Post by efflandt on 2015-04-26
It is nice that there is a **Power Statistics** gui to indicate battery power of devices now, so I can tell when batteries in my wireless mouse are getting low and it is not a complete surprise when they run down. But I wonder if there is some way to expand the % scale when using NiMH rechargeable batteries which have lower voltage than alkaline batteries (which it would eat through too quickly when gaming even if I remember to turn it off when not in use). Fully charged batteries show about 60% charge. They currently seem to drop out if at around 10% for any period of time (~0.95 volt each).
```
efflandt@XPS-8100-1404:~$ upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0006
  native-path:          /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2/0003:046D:C52B.0005/0003:046D:C52B.0006
  vendor:               Logitech, Inc.
  model:                Anywhere MX
  serial:               E929FF1E
  power supply:         no
  updated:              Sun 26 Apr 2015 07:38:35 AM CDT (43 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          60%

Daemon:
  daemon-version:  0.9.23
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no
```And I found this in /lib/udev/rules.d/95-upower-csr.rules```
ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52b", DRIVER=="logitech-djdevice", ENV{UPOWER_BATTERY_TYPE}="unifying"
```But where would the data or configuration be for battery % charge if I wanted to change that scale for the lower voltage rechargeable batteries?

---

