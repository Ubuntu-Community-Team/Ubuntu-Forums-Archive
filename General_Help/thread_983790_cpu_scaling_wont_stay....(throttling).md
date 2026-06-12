---
title: "cpu scaling wont stay....(throttling)"
date: 2008-11-16
forum: General Help
---

### Post by B34ST1Y on 2008-11-16
Hey all,

I'm using cpufreq to scale my laptop cpu to max frequency (in windows, I would use RMclock to do this)....it works great!....for about 45 seconds in game....then it clocks itself back down to 800mhz (down from 1.6ghz) ....is there any way I can override that and *lock* it in at max? I tried setting the following codes respectively...and it only temporarily sets the clock, until it decides to throttle again...

```
sudo cpufreq-set -u 1.6ghz
```
```
sudo cpufreq-set -d 1.6ghz
```
```
sudo cpufreq-set -g performance
```

can anyone help me please?

---

### Post by B34ST1Y on 2008-11-16
bump....does anyone even know what i'm talking about?

---

### Post by B34ST1Y on 2008-11-16
like...


whenever it gets under stress, it will just bump itself back down...and then come back up...and then back down. Almost like it's a heat problem...but in windows, I could force it to stay up anyway..

---

