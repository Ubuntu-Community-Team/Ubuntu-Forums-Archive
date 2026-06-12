---
title: "laptop switches off abruptly and randomly on battery power but not on mains power"
date: 2017-10-07
forum: Hardware
---

### Post by desconocido on 2017-10-07
I'm not sure whether this is a purely hardware issue or whether software or Linux is involved.

I have had this Toshiba Satellite C50D-A-11Q running without problems under Ubuntu 12.04 since 2013.
More recently the battery got old and I ran it connected to mains power nearly all the time.

This summer I bought a new battery and installed Ubuntu Mate 16.04.

Now, randomly, but at least once between disconnecting the power cable when the battery is fully charged and when the battery becomes empty, the computer will abruptly turn off (as if both the battery and mains power had been removed). This is inconvenient because I lose work. The computer will always restart on pressing the ON button.

Here are some data after the last occurence:

I installed psensor with logging.
In the 30 seconds before it switched off, cpu etc temperatures were
51.5, 51.5 and 50.0 degrees C
Battery was probably around 33.7 degrees C

And another graph of typical temperatures:
[ATTACH=CONFIG]277014[/ATTACH]

Here is a screenshot of the Power Statistics window after restart:
[ATTACH=CONFIG]277013[/ATTACH]
Is there anything odd about those temperatures and charges?

Is there anything known about Ubuntu in connection with this?

---

### Post by efflandt on 2017-10-07
Maybe that battery was not the deal you thought it was. Note that maximum charge of your battery is only 71.1% of its original rated capacity and voltage is down to 10.6V. I forget what minimum voltage is for li-ion batteries, but nominal (rated) voltage is 3.7V/cell (11.1V for 3-cell) and fully charged voltage should be about 4.2V/cell. This is an example of a recently charged 3-cell battery in a low end HP laptop (about 1 yr old not used much), without as much rated capacity, but energy-full still 98.9% of energy-full-design.```
~$ upower -i /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               COMPAL
  model:                PABAS0241231
  serial:               41167
  power supply:         yes
  updated:              Sat 07 Oct 2017 03:35:09 PM CDT (53 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              26.5647 Wh
    energy-empty:        0 Wh
    energy-full:         30.868 Wh
    energy-full-design:  31.2075 Wh
    energy-rate:         7.71975 W
    voltage:             11.724 V
    time to empty:       3.4 hours
    percentage:          86%
    capacity:            98.9123%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
```Note that you should not leave a device with li-ion battery plugged in all of the time, and should minimize time fully discharged, other than occasionally briefly running it down on battery power while not doing anything essential to keep battery meter in the OS calibrated, so it can accurately tell you when about to lose power (should charge the battery soon after that). Li-ion batteries actually last longer at half charge than long periods fully charged or fully discharged (something you learn when using similar, but soft cased lithium-polymer batteries in R/C aircraft).

I know that some AMD cpus do not like to see over 60C temperature, but that one is rated for 100C max.

---

