---
title: "Battery not charging"
date: 2015-02-09
forum: Hardware
---

### Post by kmast1212 on 2015-02-09
Hi all,

I've recently formatted my Medion e1312 netbook which was running Xubuntu and installed Lubuntu (currently running 14.10)
After installing Lubuntu, my laptops battery has stopped charging eventhough it was perfect while running xubuntu, which leads me to believe it is not the battery.
Also, I am using a universal charger which charges my second laptop fine, so I dont think its the charger either..
I've been searching constantly for a solution but cant seem to find anything that works.
The only things I havent yet tried are running another OS (which I will try later on) and updating the BIOS, but even then I cant seem to find a updated BIOS for my netbook.

Here is the upower -d results:
[HR][/HR]Device: /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Mon 09 Feb 2015 10:10:34 GMT (8982 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               HTE-SDI220F
  model:                BTY-S14
  power supply:         yes
  updated:              Mon 09 Feb 2015 12:40:11 GMT (5 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         15.0627 Wh
    energy-full-design:  48.84 Wh
    energy-rate:         0 W
    voltage:             7.333 V
    percentage:          0%
    capacity:            30.8409%

Daemon:
  daemon-version:  0.9.23
  can-suspend:     yes
  can-hibernate:   yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  yes
  is-docked:       no

[HR][/HR]


Screenshots of my xfce power manager
[ATTACH=CONFIG]259855[/ATTACH][ATTACH=CONFIG]259856[/ATTACH]

Any help would be HUGELY appreciated :)

---

### Post by weatherman2 on 2015-02-09
The operating system has little or (probably) nothing to do with whether your laptop charges the battery. It may incorrectly detect whether it is really charging or by how much but not whether it charges or not.

Your laptop should charge the battery even when not booted into an operating system - when powered off for example.  Are you saying the laptop charges the battery correctly only when not booted into Lubuntu?

Your battery may have failed.  This is quite common after a couple of years.  Laptop batteries don't last forever.

---

### Post by nathanlesko on 2015-09-03
I have the same exact issue where the battery does not charge periodically but will charge if booted into bios instead. 2 different laptops experienced same issue. Definitely not a hardware problem. Replaced ac adapters & motherboards at first and was perplexed when issue kept reoccurring. When the issue occurred on a new Dell Latitude i knew it was something with the latest Kernel.

---

