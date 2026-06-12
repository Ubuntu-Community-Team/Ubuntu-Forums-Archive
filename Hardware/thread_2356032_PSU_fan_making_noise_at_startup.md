---
title: "PSU fan making noise at startup?"
date: 2017-03-19
forum: Hardware
---

### Post by lysander6662 on 2017-03-19
I've had this build since 2010 now and it performs excellently. However, one glitch has been consistent pretty much since 2011 - whenever I turn the computer on one of the fans makes a dreadful whirring noise for about 5 mins before I can hear it quieten down. I then have to give the computer a slight bash and the whirring noise shuts up. This is a routine that has been going on every day for years.

I was never sure which fan it was, I always assumed it was a case fan - I was too lazy to open it up at startup. Today I decided to run inxi -F a few times at startup. Turns out it is most likely the PSU fan. Here are a few outputs:

On startup:

```
Sensors:   SystemTemperatures: cpu: 26.0C mobo: 22.0C gpu: 29.0
FanSpeeds (in rpm): cpu: 1795 psu: 1222 sys-1: 0
Info: Processes: 240 Uptime: 0 min Memory: 781.7/4958.6MB
```

I checked a few more times and the speed was consistent. 

And then, it started to quieten down, at which point I did another check:


```
Sensors:   System Temperatures: cpu: 32.5C mobo: 32.0C gpu: 40.0
Fan Speeds (in rpm): cpu: 1795 psu: 1406 sys-1: 0
Info: Processes: 236 Uptime: 7 min Memory: 1467.2/4958.6MB

```
Then after its ritual bash:

```
Sensors:   System Temperatures: cpu: 33.0C mobo: 32.0C gpu: 39.5
Fan Speeds (in rpm): cpu: 1834 psu: 1875 sys-1: 0
Info: Processes: 236 Uptime: 7 min Memory: 1467.4/4958.6MB

```
It then remains consistent at this speed.

So it turns out that when it is quiet it is up to the right speed. I thought it was the opposite and that it was too fast at startup. 

So would anyone be in agreement that it is the PSU fan - and what could be causing this? Secondly, should I be at all concerned and has anyone else had anything like this?

---

### Post by Autodave on 2017-03-19
Sure sounds like a bad fan to me. Have you ever tried clearing the dust off of it?  Probably too late now. I have replaced many power supplies and / or fans for that problem.

I am assuming that this is a desktop unit: why don't you just replace the power supply? They are nor expensive: $25 or so on line.

---

### Post by lysander6662 on 2017-03-20
> **Autodave said:**
> Sure sounds like a bad fan to me. Have you ever tried clearing the dust off of it?  Probably too late now. I have replaced many power supplies and / or fans for that problem.

I am assuming that this is a desktop unit: why don't you just replace the power supply? They are nor expensive: $25 or so on line.

I could I suppose, but I don't know if I really need to? I think at this point I may just leave it. As long as there's no danger to the system. I wouldn't skimp on one, I think the half decent ones are more in the £50 area.

---

### Post by poorguy on 2017-03-20
Have to agree with Autodave on this one Bad Fan and eventually the fan will stop working and can cause a problem.

I have had my share of crappy fans having the bushings dry out and either squeal or freeze up.

When you bang the case the fan quiets and the whirring noise stops tells that the bushing has worn out due to lack of lubrication. 

When replacing the fan look for one that has ball bearings instead of bushings.

---

### Post by lysander6662 on 2017-03-20
It's been this way for many years but may be worth doing. Thanks for the advice. May be better to get a new one rather than just have the thing conk out at some point.

---

