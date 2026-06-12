---
title: "Battery issues similar to bad contacts on Dell laptop- OS says everything's fine, but"
date: 2017-10-31
forum: Hardware
---

### Post by accounts0 on 2017-10-31
The machine is a Dell Inspiron 5559 Laptop, with Ubuntu 16.04.3 (server) installed with kubuntu, etc- all up-to-date.

The LED on front will occasionally flash fast amber, which means the battery's not charging. After a reboot or 2 it goes back to solid white, sometimes completely off, which meanscharging, or charged. It's a couple years old, so I wouldn't be surprised if it needs a new battery, but it's not so used that I'd expect it.


It's almost always plugged in, & usually is off overnight. On/Off basically 12/12 hours/day. The BIOS power profile is the one called 'Always Plugged In'. Maybe 2-3x/month it doesn't see the HDD & boots straight into diagnostics, which a hard reset (by holding down the power button) will make it boot properly after.


If I pull the power adapter while it's on- instant death. So I removed & re-inserted the battery & now it survives power adapter removal. Acts totally normal in all GUI/CLI indicators. 

For example the KDE Power system tray icon is normal, as is when I check in terminal via: ```
$ upower -i /org/freedesktop/UPower/devices/battery_BAT0  
  native-path:          BAT0
  vendor:               Panasonic
  model:                DELL 78V9D62
  serial:               2194
  power supply:         yes
  updated:              Tue 31 Oct 2017 02:23:01 PM EDT (52 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              41.44 Wh
    energy-empty:        0 Wh
    energy-full:         41.44 Wh
    energy-full-design:  41.44 Wh
    energy-rate:         0.0148 W
    voltage:             16.739 V
    percentage:          100%
    capacity:            95.5714%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'
  History (charge):
    1509474181  100.000 fully-charged
  History (rate):
    1509474181  0.015   fully-charged
``` 

Thus I'm leaning toward a dirty contact-related issue rather than a battery full of a bunch of worn out cells that won't hold a charge anymore.


I took a pic of the battery [1] & found a new, exact replacement on Amazon [2] for <$40, which is far less than buying a warranty extension, or a replacement battery from Dell for >$100.


Does anyone else have similar experience who can provide feedback on this?


[1]
[https://imgur.com/a/1SClQ](https://imgur.com/a/1SClQ)


[2]
[https://www.amazon.com/dp/B01C08U77K](https://www.amazon.com/dp/B01C08U77K)

---

### Post by Autodave on 2017-10-31
You may have fixed it already. I work on a lot of laptops and when I get something weird happening all of a sudden, here is the first thing that I try:

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

Believe it or not, that will fix about 1/2 of them.

---

### Post by accounts0 on 2017-10-31
> **Autodave said:**
> 

                        1. Power down and disconnect power cord.
2. ...
3. Remove battery.
4. ...
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. ...

Yea, very similar to what I did, and it appeared to resolve the immediate issue. My concern is the unknown causative factor(s), & thus preventative measures.

My background is in electronics & when I would encounter this in the field there was this clear paste we'd apply to the contacts- like clear nail polish that would act like flux when soldering- dissolving oxidation & providing conductive surface area similar to heatsink paste. It doesn't seem ideal in this case but that's all I can think of to try. It's one of those where 'It _should_ work' but (occasionally) doesn't. Grr.

---

### Post by Autodave on 2017-10-31
Dielectric silicone paste. Used many times. I do not believe that to be your problem. Computers just do that at times.

---

### Post by accounts0 on 2017-11-05
Am I the only one with this problem?

---

