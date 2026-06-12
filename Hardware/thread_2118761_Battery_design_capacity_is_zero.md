---
title: "Battery design capacity is zero"
date: 2013-02-22
forum: Hardware
---

### Post by christophes on 2013-02-22
Hi,

I've a Lenovo unit for which the battery design capacity is reported as zero. This is a brand new unit.

In /sys/class/power_supply/BAT1 I can find the following information:

POWER_SUPPLY_NAME=BAT1
POWER_SUPPLY_STATUS=Charging
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Unknown
POWER_SUPPLY_CYCLE_COUNT=1491
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=1000
POWER_SUPPLY_VOLTAGE_NOW=11820000
POWER_SUPPLY_POWER_NOW=635500000
[COLOR="Red"]POWER_SUPPLY_ENERGY_FULL_DESIGN=0[/COLOR]
POWER_SUPPLY_ENERGY_FULL=47520000
POWER_SUPPLY_ENERGY_NOW=36350000
POWER_SUPPLY_MODEL_NAME=
POWER_SUPPLY_MANUFACTURER=Li-Ion
POWER_SUPPLY_SERIAL_NUMBER=PABAS0241231

At first, I thought that this was a battery issue, but when I use Windows based battery tools, I get good values for the 3 capacity values:
- design capacity
- last full charged capacity
- current capacity

These 3 values are different in windows, so it's not that one of the capacity values is reused for one of the other values.

Any idea what the problem can be? Is this a Ubuntu defect?

Thanks.

---

### Post by christophes on 2013-02-25
Fyi: the unit type is [COLOR=#222222][FONT=arial]Lenovo G780.

Does anyone have this problem as well?
[/FONT][/COLOR]

---

