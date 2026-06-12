---
title: "Battery Reportingd As &quot;Fully Charged&quot; While AC's Attached"
date: 2009-12-26
forum: Hardware
---

### Post by stew721 on 2009-12-26
I've replaced my old battery with a bigger one and it charged fine the first (and only) time, but now I'm getting told by GPM that the battery's fully charged while the AC's plugged in.  However, if I remove the AC, GPM reports the correct percentage.  Therefore, it refuses to charge.  The first time I charged the battery was while the computer was turned off; I didn't turn it on until the battery was fully charged.

With AC attached:
```
$ cat /proc/acpi/battery/BAT0/alarm
alarm:                   unsupported
``````
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6600 mAh
last full capacity:      6600 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 660 mAh
design capacity low:     200 mAh
capacity granularity 1:  66 mAh
capacity granularity 2:  66 mAh
model number:            DELL 00
serial number:           10000
battery type:            LION
OEM info:
``````
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      2886 mAh
present voltage:         11311 mV
``````
$ devkit-power -d
Device: /org/freedesktop/DeviceKit/Power/devices/line_power_AC
  native-path:          /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC
  power supply:         yes
  updated:              Sat Dec 26 22:06:49 2009 (819 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/DeviceKit/Power/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  model:                DELL 00
  serial:               10000
  power supply:         yes
  updated:              Sat Dec 26 22:20:23 2009 (5 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              32.0346 Wh
    energy-empty:        0 Wh
    energy-full:         73.26 Wh
    energy-full-design:  73.26 Wh
    energy-rate:         0.0111 W
    voltage:             11.303 V
    percentage:          43.7273%
    capacity:            100%
    technology:          lithium-ion

Daemon:
  daemon-version:  011
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes
```With AC removed:
```
$ cat /proc/acpi/battery/BAT0/alarm
alarm:                   unsupported
``````
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6600 mAh
last full capacity:      6600 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 660 mAh
design capacity low:     200 mAh
capacity granularity 1:  66 mAh
capacity granularity 2:  66 mAh
model number:            DELL 00
serial number:           10000
battery type:            LION
OEM info:
``````
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1751 mA
remaining capacity:      2867 mAh
present voltage:         11042 mV
``````
$ devkit-power -d
Device: /org/freedesktop/DeviceKit/Power/devices/line_power_AC
  native-path:          /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC
  power supply:         yes
  updated:              Sat Dec 26 22:20:54 2009 (96 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             no

Device: /org/freedesktop/DeviceKit/Power/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  model:                DELL 00
  serial:               10000
  power supply:         yes
  updated:              Sat Dec 26 22:22:28 2009 (2 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              31.5573 Wh
    energy-empty:        0 Wh
    energy-full:         73.26 Wh
    energy-full-design:  73.26 Wh
    energy-rate:         19.4361 W
    voltage:             11.066 V
    time to empty:       1.6 hours
    percentage:          43.0758%
    capacity:            100%
    technology:          lithium-ion
  History (charge):
    1261884148    43.076    discharging
    1261884118    43.333    discharging
    1261884088    43.561    discharging
  History (rate):
    1261884118    19.436    discharging
    1261884088    12.954    discharging

Daemon:
  daemon-version:  011
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes
```

---

### Post by stew721 on 2009-12-27
Hmm...  :confused:

While I had Win7 loaded in VirtualBox, I decided to try uninstalling "ACPI-Compliant Control Method Battery" and rescanning for changs; as well as removing/connecting the AC.  After a couple of times, the battery started charging.  Having shut down the virtual machine, the battery's still charging and GPM is reporting 46.7% and 01h45 until charged.

---

