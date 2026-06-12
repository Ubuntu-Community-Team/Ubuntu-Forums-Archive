---
title: "Laptop battery not charging"
date: 2017-10-06
forum: Hardware
---

### Post by junaidmalikpk14 on 2017-10-06
Hello Guys,

I installed new battery and it is not charging it and showing it is Full charged, i searched the forum and could not find any satisfactory answer. Below are the details of my system, Ubuntu version and commands that show batter status. I have also restarted the system multiple 2/3times.


**Battery details:**
  voltage: 11.1V 
  capacity: 4400mAh
 On battery box it is written "Replacement Laptop Battery for Inspiron n5010"


**System:**
  DISTRIB_ID=Ubuntu 
  DISTRIB_RELEASE=16.04 
  DISTRIB_CODENAME=xenial 
  DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"

**Laptop Model: ** Dell Vostro 3550

```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  model:                DELL 7XFJJA2
  serial:               19183
  power supply:         yes
  updated:              &#1608; 11:42:56 PKT &#1578; 06 &#1575;&#1603;&#1578;&#1608;&#1576;&#1585; 2017 (18 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              48.84 Wh
    energy-empty:        0 Wh
    energy-full:         48.84 Wh
    energy-full-design:  48.84 Wh
    energy-rate:         0.0111 W
    voltage:             8.828 V
    percentage:          100%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'
```


```
cat /sys/class/power_supply/BAT0/status
Full
```



Regards,
Junaid

---

### Post by Autodave on 2017-10-06
Probably got a defective battery. Or your charger is no good.  I just went through that: got 3 bad batteries in a row: none would charge. Gave up on that company and went to a different company. That one worked first try.

The "computer" (microprocessor) that controls battery charging is part of the battery itself. That is usually what is no good on "new" batteries.

---

### Post by Bucky Ball on 2017-10-06
Welcome. If it is showing fully charged and you have the computer plugged in to power it would not be charging it, so I have a stupid question: I presume you have unplugged the computer and tried running from the battery and the computer won't start?

Autodave is correct. They can occasionally be DOA (dead on arrival) or die without warning (I've had one do just that).

---

### Post by efflandt on 2017-10-07
If you had trouble turning the laptop on without power supply connected, and still do when the new battery is fully charged, you might have some other issue (possibly not making proper contact).

You say 11.1V, but upower shows 8.828 V (2-cell battery?). Either it is wrong battery or defective. This is an example of 3-cell battery in low end HP laptop (note 12.576 V fully charged):```
~$ upower -i /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               COMPAL
  model:                PABAS0241231
  serial:               41167
  power supply:         yes
  updated:              Fri 06 Oct 2017 11:03:50 PM CDT (15 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              31.1199 Wh
    energy-empty:        0 Wh
    energy-full:         31.1528 Wh
    energy-full-design:  31.2075 Wh
    energy-rate:         0.40515 W
    voltage:             12.576 V
    percentage:          100%
    capacity:            99.8246%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'
  History (charge):
    1507349029    100.000    fully-charged
  History (rate):
    1507349029    0.405    fully-charged
    1507348934    0.558    charging
```Li-ion batteries are nominally rated at 3.7V per cell (3.7 x 3 = 11.1), but fully charged are about 4.2V (x 3 ~= 12.6V). So your battery may actually be overcharged (or almost dead cell).

---

