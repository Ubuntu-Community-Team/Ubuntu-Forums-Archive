---
title: "ThinkPad P50 &amp; ubuntu 22.04 don't wake up anymore"
date: 2022-04-07
forum: Hardware
---

### Post by michal.fita on 2022-04-07
I upgraded to Ubuntu 22.04 on the ThinkPad P50 and cannot wake up the machine after suspend any more. Just after installation there was some offering for the firmware update that I did, but now pressing the power button when it slowly flashes after going to sleep doesn't work. The only thing I can do is to press it over five seconds to turn the computer off.

The funny part I've noticed yesterday is that as I set up [FONT=courier new]systemd[/FONT] to use [FONT=courier new]sleep-then-hibernate[/FONT], turning it off (5 sec pressing power) then turning it on actually in one case restored it from hibernation. So the part I wanted to get to work to save battery when I put the computer away for longer seem to do the job, but I can't wake it up from the original suspension, for example after closing the lid.

I can't find any BIOS obvious options who would infer with the behaviour on this model.

Any advice very welcome.

---

