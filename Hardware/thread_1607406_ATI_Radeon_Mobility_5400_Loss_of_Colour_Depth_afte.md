---
title: "ATI Radeon Mobility 5400 Loss of Colour Depth after Maverick install"
date: 2010-10-27
forum: Hardware
---

### Post by JerecDrak2 on 2010-10-27
Hey Guys,

Since installing Maverick I've noticed that my colour depth is a lot lower than it was on Lucid. There's severe banding everywhere and I can't see any settings in the Catalyst Control Center that affect this issue. I'm dual booting Windows 7 and everything displays correctly there so I can be sure it's not a screen/hardware fault.

Has anyone else experienced this or found a solution? Any help is much appreciated.

---

### Post by JerecDrak2 on 2010-11-04
I've also just noticed that the colour depth is fine when the laptop boots up, and degradation only occurs after the screensaver (in my case a blank screen) activates. Has no one else experienced this issue?

---

### Post by Zuseppe on 2010-11-15
I noticed exactly the same problem on my Acer 5024wlmi with ATI X700 Mobile, on Ubuntu 10.10 Maverick.

---

### Post by axeldamage on 2010-11-24
I have the same problem in my Sony vaio VPCEB1Z1E with radeon HD 5600

---

### Post by sivael on 2011-03-25
Ati Radeon HD 6370M, i3 2 core Ubuntu 10.10, latest kernel update,
Tried different settings in /etc/default/acpi-support and none worked.
Actually I don't know if they would anyway because Ubuntu 10.10 is using the gnome-power-manager daemon and that sets the flag in /etc/acpi/lid.sh and sleep.sh and so on, that disables the scripts(they actually don't do anything)
So... How to change that and where to look? Sources of the gnome-power-manager?
Does it use scripts to do the things it does or is it hard-coded?
If scripts, where are they?
in /usr/share/gnome-power-manager/ is only the bugreporting script.
```
Distro version:       DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Kernel version:       2.6.35-28-generic
g-p-m version:        2.32.0
HAL version:          ./gnome-power-bugreport: 49: lshal: not found
System manufacturer:  missing
System version:       missing
System product:       missing
AC adapter present:   ./gnome-power-bugreport: 59: hal-find-by-capability: not found
no
Battery present:      ./gnome-power-bugreport: 62: hal-find-by-capability: not found
no
Laptop panel present: ./gnome-power-bugreport: 65: hal-find-by-capability: not found
no
CPU scaling present:  ./gnome-power-bugreport: 68: hal-find-by-capability: not found
no
Battery Information:
./gnome-power-bugreport: 71: lshal: not found
UPower data:
Device: /org/freedesktop/UPower/devices/line_power_AC0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/ACPI0003:00/power_supply/AC0
  power supply:         yes
  updated:              Fri Mar 25 10:11:07 2011 (812 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0A:00/power_supply/BAT0
  vendor:               ASUSTek
  model:                K72J-44
  power supply:         yes
  updated:              Fri Mar 25 10:24:13 2011 (26 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              47.278 Wh
    energy-empty:        0 Wh
    energy-full:         48.389 Wh
    energy-full-design:  48.4 Wh
    energy-rate:         0 W
    voltage:             12.466 V
    percentage:          97.704%
    capacity:            99.9773%
    technology:          lithium-ion

Daemon:
  daemon-version:  0.9.5
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes
GNOME Power Manager Process Information:
sivael    1973  0.0  0.2 307188 12324 ?        Sl   10:11   0:00              \_ gnome-power-manager
HAL Process Information:

```

it's weird how the hal-find-by-cap... doesn't return the capabilities that are actually there.

Going to sleep and waking the comp up fixes the color depth.
Hibernating as well (and yes, I had to fix those b/c the laptop didn't go to sleep properly :/)

So.... any ideas? I frequently leave my laptop for downloading over night(it's not as loud as my main comp with UPS and stuff) and I close the lid. Also, when I move my laptop I close the lid and don't want the system to go to sleep but just turn off the panel.

thanks.

---

### Post by sachinr on 2011-05-19
*bump* 

Anyone figured out this problem?

---

