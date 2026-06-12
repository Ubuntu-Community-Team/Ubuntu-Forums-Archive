---
title: "Asus Q200E Laptop Touch Screen Digitizer Malfunctioning; Had to be manually disabled"
date: 2014-10-20
forum: Hardware
---

### Post by sjeon on 2014-10-20
**The box**
Asus Q200E Touchscreen Laptop
Ubuntu 14.04 LTS 64 bit

**The problem**
The digitizer is running amok, registering random clicks. Hard to use the mouse at all while it's doing that, plus it's clicking on things on its own, which is, in this case, not a desired feature.

**My temporary solution**
# Figured out which device looked to be the digitizer from this list:
xinput --list
# Turned off the digitizer with this command:
xinput set-prop 'Atmel Atmel maXTouch Digitizer' 'Device Enabled' 0

**Thoughts**
+ Oughta be doable in System Settings. Doesn't appear to be (?)
+ Laptop closing oughta turn off the touchscreen digitizer. Doesn't.

---

