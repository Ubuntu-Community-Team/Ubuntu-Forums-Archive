---
title: "laptop forced suspend"
date: 2015-06-15
forum: Hardware
---

### Post by rjvbertin on 2015-06-15
Hello,

I'm maintaining Kubuntu 14.04LTS on my gf's HP G62 laptop, an older model with an AMD P320 CPU and RV710 GPU. Before moving to Kubuntu I used the proprietary fglx driver with that GPU, and it took me a while to figure out how to configure that driver so it wouldn't use the maximum power mode continuously - a mode that would cause overheating and make the BIOS cut the power.

With Kubuntu, this kind of "fatal" overheating rarely occurs (I've seen it happen while building a kernel from source). It's been used regularly to watch streaming Flash video (tv...) for hours.

The last couple of days, my gf tells me the system has been turning off because of overheating. However, when I looked this morning, its uptime is over 9 days. So this "turning off" is a much less catastrophic "putting to sleep". I cannot find any hint to the reason in the system logs; they just show the suspend and subsequent wake events.

The only events I know that put force-suspend the system to RAM are related to battery power, but apparently that cannot be the case here (which I tend to believe because the battery has become very shallow, and will empty in less than 20 minutes when watching video off the mains power).

What other events are there that could suspend the system, in particular, is there a software overheating protection that could do this? Maybe something introduced or changed in a very recent update?

Thanks,
René

---

### Post by weatherman2 on 2015-06-15
I suspect the charger may be failing and/or something is wrong with the power connector - and the battery is discharging, making the laptop go to sleep.  A slightly loose power jack could cause the charger to lose connection occasionally.  Or it could be an electronic problem with the charger.

---

### Post by rjvbertin on 2015-06-15
Yeah, I have been thinking about that too, but that would mean the battery starts charging as soon as the system gets suspended. And gets enough juice to support a long enough playback duration after waking the system again, to suggest something other than this explanation (if you see what I mean).

---

### Post by weatherman2 on 2015-06-15
If the charger is not making a reliable connection to the laptop, it could stop/start charging intermittently.  So suddenly it could stop charging and the battery would drain; it might start charging again later after the laptop has suspended.  It may not be a physical issue with a connection; it might be an electronic problem with the charger or with the laptop itself.

---

### Post by rjvbertin on 2015-06-15
hmm, yes, it's probably not impossible. The question does remain however why the system would chime an alert when we disconnect the charger manually, and not when the power is cut because of another reason ;)

---

