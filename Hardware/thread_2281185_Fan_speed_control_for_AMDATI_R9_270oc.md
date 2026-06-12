---
title: "Fan speed control for AMD/ATI R9 270oc?"
date: 2015-06-05
forum: Hardware
---

### Post by metroedged on 2015-06-05
The thing is very loud and doesn't need to be while idle. Makes it very hard to use as silent HTPC

---

### Post by QIII on 2015-06-05
Hello!

Do you have the proprietary driver installed?

If so, then power management and fan speed should be controlled on board.  The minimum fan speed is 20%.

You can use AMD Overdrive with Linux, but it is a command line affair.

To set the fan speed manually (I don't recommend this, as you may destroy your card if you set the fan speed too low!) the command is

```
sudo amdconfig --pplib-cmd "set fanspeed <id> <percent>
```

where <id> is the adapter (it's zero-based, so if you have only one card it would be 0)

and

<percent> is the fan speed desired as a function of percent.

If you are using the open source Radeon driver, it did not work well for me when I tested the XFX R9 290x Dual Dissipation (two fans) a few months ago.  Power management has come a long way in the Radeon driver, but I don't know if the developers have caught up to the R7 and R9 series of cards.

---

