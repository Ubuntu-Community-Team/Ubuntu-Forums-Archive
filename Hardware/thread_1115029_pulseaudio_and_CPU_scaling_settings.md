---
title: "pulseaudio and CPU scaling settings"
date: 2009-04-03
forum: Hardware
---

### Post by spidermagicat on 2009-04-03
I have an AMD turion x2 2GHz processor in my laptop. I'm running jaunty AMD64 and things are working great except...

When I have cpu scaling enabled my CPU drops down to 800MHz like it should, but this means that pulseaudio lags with underruns when I minimize or move windows which is just annoying and frankly unacceptable. I would just put turn cpu scaling off but then my laptop gets hot and the fan gets pretty loud.

Is there a way to stop pulseaudio from lagging at the low CPU level, I never go above 30% CPU usage really so it's not a lack of resource, even on the lowest setting.

Or is there a way to change cpu up in time to stop the lag or what would be best, only use the minimum setting like a screensaver, so when I move the mouse it switches up to the next level

Please help :-) I just want to listen to music when I work.

---

### Post by dpsleep on 2009-05-15
> **spidermagicat said:**
> I have an AMD turion x2 2GHz processor in my laptop. I'm running jaunty AMD64 and things are working great except...

When I have cpu scaling enabled my CPU drops down to 800MHz like it should, but this means that pulseaudio lags with underruns when I minimize or move windows which is just annoying and frankly unacceptable. I would just put turn cpu scaling off but then my laptop gets hot and the fan gets pretty loud.

Is there a way to stop pulseaudio from lagging at the low CPU level, I never go above 30% CPU usage really so it's not a lack of resource, even on the lowest setting.

Or is there a way to change cpu up in time to stop the lag or what would be best, only use the minimum setting like a screensaver, so when I move the mouse it switches up to the next level

Please help :-) I just want to listen to music when I work.


you could try /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq

---

