---
title: "HP 311 battery issues"
date: 2009-12-27
forum: Hardware
---

### Post by nrune on 2009-12-27
For Christmas I got a [HP 311 mini]("http://h10025.www1.hp.com/ewfrf/wc/product?product=4041554&lc=en&dlc=en&cc=us").  The windows install was corrupt and after a hour on the phone with some dude in India, they are shipping me an XP disk to reinstall.  So what is a geek to do but install Ubuntu Karmic netbook Remix from a thumbdrive

After some inital trouble with the install I finally got it to work and it works well. 

Problem is that when I unplug the netbook it immediately shuts off and does not fall back to battery power. It is acting as if it does not have a battery, or that the battery is dead.  

After getting everything up and running yesterday I was able to use the netbook and the battery was working well. 

The OS seems to think that it is charging the battery. 

Any ideas?> nrune@nrune-netbook:/$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         5100 mAh
last full capacity:      5024 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 2 mAh
design capacity low:     2 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            NiMH
OEM info:                Hewlett-Packard


> evice: /org/freedesktop/DeviceKit/Power/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  vendor:               Hewlett-Packard
  model:                Primary
  power supply:         yes
  updated:              Sun Dec 27 10:25:43 2009 (4 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              40.0896 Wh
    energy-empty:        0 Wh
    energy-full:         54.2592 Wh
    energy-full-design:  55.08 Wh
    energy-rate:         0.0108 W
    voltage:             11.813 V
    percentage:          73.8854%
    capacity:            98.5098%
    technology:          nickel-metal-hydride

Device: /org/freedesktop/DeviceKit/Power/devices/line_power_ACAD
  native-path:          /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD
  power supply:         yes
  updated:              Sun Dec 27 09:42:03 2009 (2624 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Daemon:
  daemon-version:  011
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes
p

Charged battery without os with computer off.  Same issue, just dies.  I suspect broken battery not sure what else to check.

---

### Post by nrune on 2010-01-01
After a reinstall of windows XP and using HP's battery check tool, discovered that the battery was faulty and covered under HP Warrenty. After 1hr 15 min on the phone with tech support they are supposed to be sending me a replacement battery.

---

