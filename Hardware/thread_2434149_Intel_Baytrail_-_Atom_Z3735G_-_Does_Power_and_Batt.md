---
title: "Intel Baytrail - Atom Z3735G - Does Power and Battery Work For You?"
date: 2019-12-31
forum: Hardware
---

### Post by senturion86 on 2019-12-31
I installed Ubuntu onto my Dell Venue 8 3845 tablet, which uses an Atom Z3735G processor, on the Baytrail chipset.

Everything works great except for the battery status. It is bogus - always 100%. Serial Number says "123456789" and the capacity is reported as 0. An it says the battery is a Dell BLY, and the native path from upower is reported as TIBT. 

Has anybody else gotten this to work on such a device? Or does anybody have an easy fix that doesn't involve DSDT editing? I've spent several weeks trying to figure that out. It is kind of critical to have a power status since this is a tablet device and is mostly used portable, not plugged into a dock.

Here is the battery report from upower:

Device: /org/freedesktop/UPower/devices/battery_TIBT
  native-path:          TIBT
  vendor:               DELL
  model:                BLY Battery
  serial:               123456789
  power supply:         yes
  updated:              Tue 31 Dec 2019 09:37:18 AM PST (9 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         0 Wh
    energy-full-design:  0 Wh
    energy-rate:         0 W
    percentage:          100%
    capacity:            100%
    technology:          lithium-polymer
    icon-name:          'battery-full-charged-symbolic'


Device: /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Tue 31 Dec 2019 09:17:17 AM PST (1211 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'






I've tried leaving the tablet on suspend until the battery dies, since some reports say that works... but didn't work for me.

I've tried unplugging the battery to power on with only AC, but this tablet won't power on without it plugged in as well.

I think the problem is related to an ACPI issue with my DSDT table... and I've tried dabbling into it, but can't figure out the DSDT stuff for what is wrong very easily. I have also tried compiling the kernel from source, and selecting modules that apply to this tablet, but still no such luck.



I am at the point of even considering paying for someone to help me figure out the DSDT so that I know how to better fix it later for other devices. I would like to pay it forward if possible.

---

### Post by Autodave on 2019-12-31
What version did you install?

---

### Post by senturion86 on 2020-01-01
I installed Xubuntu 18.04 originally, but then upgraded to 19.10. The first version installed was Xubuntu, but then I installed ubuntu-gnome-desktop and wayland to have the Ubuntu distro experience. Would it be better to install the Ubuntu distro instead?

---

