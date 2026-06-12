---
title: "help with powertop"
date: 2011-05-03
forum: Hardware
---

### Post by oldmankit on 2011-05-03
Hello,

I sometimes use my laptop on battery where I use only one program: lyx, and possibly evince.  I don't need any networking.

Powertop is a great program, but I need a bit of help with it.  

I see this suggestion often:
```
Suggestion: Enable the CONFIG_PM_ADVANCED_DEBUG kernel configuration option.
This option will allow PowerTOP to collect runtime power management statistics.
```I've just seen a new one:
```

Suggestion: Enable the CONFIG_INOTIFY kernel configuration option.
This option allows programs to wait for changes in files and directories
instead of having to poll for these changes

```Does this mean I have to compile a kernel myself?  Since I've never done that before, would it be worth learning how to do that...would the benefits be significant?

Also, some of it's suggestions like 'A - turn audio powersave on' don't display any commands I can copy and paste into a terminal.  I'm thinking of writing a script which will put my laptop into low power mode without having to go into powertop every time.  Is there any way to turn audio powersave on without powertop?

---

### Post by tgalati4 on 2011-05-03
My understanding is that you would have to enable the statistics collection (either through adding a module or recompiling the kernel).  Otherwise, powertop settings only apply for the session which you run it and make changes.

In practice with my Thinkpad T43p you can get about a 3-5 watts savings from 18 watts to 15 watts (for example).  It's tedious to run powertop for each session, but you can learn what devices/interrupts are poking the processor the most (and not allowing it to sleep properly).

The real test is to use a wall clock and measure the battery working time with a stock low-power setup and then using powertop.  I found that I could gain ~20 min of extra life out of a 2-hour battery.  My battery is only at 70% life, so your results would vary.  Now, 20 minutes isn't a lot.  So spend the money and get an extra battery (or larger capacity) when you really need the off-the-grid time.  Powertop won't double your working time--more like 10 to 15%.

I'm not sure what audio power saving is.  Perhaps it's turning off the audio hardware.  That can be done in BIOS, typically.  You can also turn off the parallel port, serial port, USB ports, etc to save some power.

Also realize that turning several things off can reduce the user experience such that the machine is sluggish and not acting like it normally should.

---

### Post by oldmankit on 2011-05-12
> **tgalati4 said:**
> My understanding is that you would have to enable the statistics collection (either through adding a module or recompiling the kernel).  Otherwise, powertop settings only apply for the session which you run it and make changes.

In practice with my Thinkpad T43p you can get about a 3-5 watts savings from 18 watts to 15 watts (for example).  It's tedious to run powertop for each session, but you can learn what devices/interrupts are poking the processor the most (and not allowing it to sleep properly).

The real test is to use a wall clock and measure the battery working time with a stock low-power setup and then using powertop.  I found that I could gain ~20 min of extra life out of a 2-hour battery.  My battery is only at 70% life, so your results would vary.  Now, 20 minutes isn't a lot.  So spend the money and get an extra battery (or larger capacity) when you really need the off-the-grid time.  Powertop won't double your working time--more like 10 to 15%.

I'm not sure what audio power saving is.  Perhaps it's turning off the audio hardware.  That can be done in BIOS, typically.  You can also turn off the parallel port, serial port, USB ports, etc to save some power.

Also realize that turning several things off can reduce the user experience such that the machine is sluggish and not acting like it normally should.

Thanks for that advice.  I've timed my laptop's battery life it and actually found very little improvement using powertop.  So maybe I should just use it to alert me to things that are waking up the CPU and try to disable them if I don't need them.

I noticed gwibber-service, compiz and ubuntuone daemon getting about 10 or more wakeups per second. I can use ubuntu-classic and shut-down gwibber and ubuntu one when I'm running on batteries.

Also, [extra timer interrupt], [i915] <interrupt>, kworker and [kernel scheduler] Load balancing tick, are responsible for way more (50-150 wakeups per second) than my humble usage with lyx and a keyboard.

I tried searching into what those things represent but was baffled.  It's all about kernels, and I don't know anything about kernels, so I don't think there's anything I can do.

---

### Post by Yellow Pasque on 2011-05-12
It looks like the kernel hackers are still working on it. [https://lkml.org/lkml/2011/3/29/2](https://lkml.org/lkml/2011/3/29/2)
You may want to try the 2.6.39 mainline kernel when it comes out (soon) and see if it behaves any better. I'm also looking to increase my laptop's battery life.. :\

---

