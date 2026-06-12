---
title: "Wired battery behaviour on Ubuntu 14.04 with Toshiba Satellite Z830-10J"
date: 2014-09-12
forum: Hardware
---

### Post by chrstump on 2014-09-12
I am experiencing some issues with my brand new battery (7 days old) in a Toshiba Satellite Z830-10J running Ubuntu 14.04:

When I charged it the first time, it went up to 95% of the designed full energy. But whenever I run on battery the first few days, after some time (say 1.5 - 2h), the battery percentage dropped drastically (e.g., from 40% to 2% or similar behaviour). I have tracked this behaviour also in the battery statistics history.

I then observed also drastic drops in the full energy rate. It now went down to 45% of the designed full energy, see below the current output of upower.

Does that sound like I have bought a damaged battery (which sounds unlikely since it was at a major German vendor in a still closed original Toshiba box) ? Any ideas of how to proceed tracking down the issue?

Thanks a lot for your help, Christian

stumpc5@stumpc5:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  model:                G71C000CH310
  serial:               0000001706
  power supply:         yes
  updated:              Fri 12 Sep 2014 03:43:06 PM CEST (3 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              15.452 Wh
    energy-empty:        0 Wh
    energy-full:         21.062 Wh
    energy-full-design:  46.472 Wh
    energy-rate:         9.933 W
    voltage:             15.12 V
    time to empty:       1.6 hours
    percentage:          73%
    capacity:            45.3219%
    technology:          lithium-ion
  History (charge):
    1410529354    73.000    discharging
  History (rate):
    1410529386    9.933    discharging
    1410529370    9.797    discharging
    1410529354    9.933    discharging
    1410529338    10.326    discharging
    1410529322    10.825    discharging
    1410529306    12.080    discharging
    1410529290    10.825    discharging

---

