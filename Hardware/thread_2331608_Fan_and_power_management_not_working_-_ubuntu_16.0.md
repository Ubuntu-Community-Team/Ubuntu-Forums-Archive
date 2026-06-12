---
title: "Fan and power management not working - ubuntu 16.04"
date: 2016-07-23
forum: Hardware
---

### Post by olly3 on 2016-07-23
I'm running ubuntu-mate 16.04 (64-bit) on a Lenovo Ideapad, with dual core i3-5005U CPU. Over the last couple of days, I have noticed that the fan no longer works. Specifically it never switches on, no matter how hot the computer gets. I also sometimes get an error message telling me that mate-power-manager has crashed. 

When I first installed ubuntu-mate, about a month ago, the fan **did** work - so this is a new development. 

I have tried to search the forums, but have found nothing up to date. Most forum discussions on this topic seem to involve installing lm-sensors, which I have done. The output from the command "sensors" is:

```
coretemp-isa-0000Adapter: ISA adapter
Physical id 0:  +39.0°C  (high = +105.0°C, crit = +105.0°C)
Core 0:         +39.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:         +38.0°C  (high = +105.0°C, crit = +105.0°C)


thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM

```

Obviously the temperatures here are not high, but even at much higher temps the fan still remains at 0 RPM. I have tried updating grub and rebooting and shutting down the laptop, but that doesn't help. I tried running the command "lm-sensors-detect" and selected "yes" for all of the options it gave me, but it did not help. 

I don't know how to proceed and would appreciate any help. I would rather not reinstall the OS all over again, because it took me quite a while to get everything just how I like it.

Thanks!

---

### Post by TheFu on 2016-07-24
Perhaps the fan is broken? Fans do fail.
Boot off a liveCD/flash drive and cause the system to get hot enough where the fan turns on. If it never turns on, you have a fan HW issue. Replace the fan.

---

