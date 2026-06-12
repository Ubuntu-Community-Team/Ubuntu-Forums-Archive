---
title: "Random Shutdowns and it's Not Heat, Badram or Voltages"
date: 2014-05-28
forum: Hardware
---

### Post by AR_Kozz on 2014-05-28
This is an old desktop, ubuntu 12.04 on

an HP d330 mobo with a hyperthreading 3.0ghz P4 Northwood
1024mb of pc3200 DDR
an Nvidia 7600gs gpu
a 60gb SATA hdd (laptop)
dvd-rw (IDE)

Occasionally - every few days or so - it resets randomly for no reason that I can trace. It's not due to heat, for example 2 minutes before the last reset psensor-daemon recorded in syslog

```
May 28 02:49:31 frankenstein sensord: sensord started
May 28 02:49:31 frankenstein sensord: Sensor alarm: Chip adt7463-i2c-0-2e: M/B Temp: 39.8 C (min = 20.0 C, max = 54.0 C) [ALARM]
May 28 02:49:31 frankenstein sensord: Chip: adt7463-i2c-0-2e
May 28 02:49:31 frankenstein sensord: Adapter: SMBus I801 adapter at fc00
May 28 02:49:31 frankenstein sensord:   Vcore: +1.30 V (min = +0.00 V, max = +2.99 V)
May 28 02:49:31 frankenstein sensord:   +3.3V: +3.26 V (min = +2.97 V, max = +3.63 V)
May 28 02:49:31 frankenstein sensord:   +5V: +5.08 V (min = +4.50 V, max = +5.50 V)
May 28 02:49:31 frankenstein sensord:   +12V: +0.12 V (min = +0.00 V, max = +15.94 V)
May 28 02:49:31 frankenstein sensord:   fan1: 0 RPM (min = 0 RPM)
May 28 02:49:31 frankenstein sensord:   fan2: 0 RPM (min = 0 RPM)
May 28 02:49:31 frankenstein sensord:   fan3: 0 RPM (min = 0 RPM)
May 28 02:49:31 frankenstein sensord:   fan4: 0 RPM (min = 0 RPM)
May 28 02:49:31 frankenstein sensord:   temp1: 29.5 C (min = 15.0 C, max = 45.0 C)
May 28 02:49:31 frankenstein sensord:   M/B Temp: 39.8 C (min = 20.0 C, max = 54.0 C) [ALARM]
May 28 02:49:31 frankenstein sensord:   temp3: 55.5 C (min = 20.0 C, max = 80.0 C)
May 28 02:49:31 frankenstein sensord:   cpu0_vid: +1.388 V
```

It doesn't appear to be software, as syslog records nothing before shutdown that it doesn't record during shutdown-free sessions as well. The M/B temp "alarm" is a calibration issue and means nothing. temp 3 is cpu, and temp1 is chassis. 

About 1 week ago, memtest86 reported failure of test 3 at several addresses and test 6 at 1 address. I removed and reseated the modules and they have passed many complete tests with no errors since then. Disk errors were found at bootup at around the same time and repaired with fsck.

The resets have occured with two different power supplies - one 300W, one 400W. They are not new but the voltages are reliable. The resets tend to occur in spurts, and I was watching Xsensor when the last one happened: 1.34, 3.27, 5.07 and 12 at that precise instant, each within 2 percent of optimal. Temp sensors were normal at the time as well. The PSU is plugged into a surge protector. Both PSU's are well-cooled and never warm to the touch.

All I can think of besides these usual suspects is that both the PSU's are somehow maintaining a constant voltage but with low power, forcing them to reduce current when more devices draw power, tripping their undercurrent limiters, assuming they have them. But the pattern of resets doesn't fit. The shutdowns happen during both heavy and light power usage. And I doubt this would happen to both PSU's at once or so sporadically. I don't know a whole lot about PSU's but they seem fine to me.

Then there's MB damage - what could be damaged so lightly as to work perfectly except for resets? 

I know this is a long shot on this forum, but maybe someone has an idea.

---

