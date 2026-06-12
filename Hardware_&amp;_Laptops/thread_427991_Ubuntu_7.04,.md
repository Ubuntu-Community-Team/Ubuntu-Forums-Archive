---
title: "Ubuntu 7.04,"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by jgcamp99 on 2007-04-29
behaves so much like OS X on a notebook, it's just incredible. I've always liked having lmsensors for pre-feisty Ubuntu, that when gnome sensors applet worked out of the box on my Dell L400 (P III 700 Mhz), I can now compare it directly with idle and load with my Apple Powerbook 867 Mhz with Tiger. Both are close to 48-50* C at idle once warmed up after a few minutes. Once you start using them, they both get into the lower to upper 50's web surfing. Updates and more intensive loads, easily get them into the low 60's. From my observations, neither Ubuntu or OS X on the notebooks ever got above 63* C.

On my AMD desktop, a 3200+ XP @ 2.2 Ghz, it runs more like Windows XP, idling around 36-39* C and under heavier loads low 40's.

---

### Post by Richard Kut on 2007-04-30
That is interesting. My laptop used to operate in that range too. However, I found some documentation on the web about how to clean the dust out of the heat sinks near the ventilation fans, and that made the temperature drop by 12 degrees Celsius.

---

### Post by jgcamp99 on 2007-05-01
> **Richard Kut said:**
> That is interesting. My laptop used to operate in that range too. However, I found some documentation on the web about how to clean the dust out of the heat sinks near the ventilation fans, and that made the temperature drop by 12 degrees Celsius.

I'm willing to try/go that route, if that is what it takes, kinda hate to take the notebook apart though. The Ubuntu install defaulted with powerd (2.6.* kernel), doesn't support scaling the cpu with that, but the fan seems to behave normally, that is stays off and doesn't come on until it gets into the low to mid 60's. When I tried/went to cpudyn or cpufreqd, it uninstalled powerd and the fans ran constantly and temps hovered around 50* C. I couldn't put up with that, even though the cpu temp was lower, as it was not only noisier, but the hdd temps were constantly 47 and above. Right now, when I let it idle prolonged, cpu drops to 48* C, It's at 54-57* C now and the hdd never gets over 43/44* C. We're looking at a P III mobile 700 Coppermine, that Intel says can take 100* C, This one never gets past 70* C, so it's got some headroom, but I figure that's too hot for a 700 Mhz P III mobile even. The notebook is a slim ultralite/ultraportable with the 12.1 lcd. That in and of itself is going to make for a warmer blooded notebook. But 700 Mhz, to me that's speedstepped down for today's notebooks and I would think it would be cool running, even if it is the highest speed this notebook is rated for. Windows XP ran like that on a K6-III+ @ 550 Mhz, I figured it was because it was at the low end of the minimum requirements for XP.

---

### Post by jgcamp99 on 2007-05-04
Well, I tried a new approach to this, The Dell L400 requires periodic battery calibration in the bios. I ran it last night and temps are mid 40's (momentary high of 46* C) for the cpu and mid to upper 30's (momentary high of 40* C) for the hdd. I never calibrated the battery for Edgy or Feisty as a freshly or upgraded OS installation and it ran absurdly hot. This is very live-able in comparison to pre-calibration operation.

So perhaps the bios power management was never right and that's why it was cooking itself and shutting itself down over the past couple days to avoid frying itself. It never did that under Edgy, started doing it the last few days under Feisty. It's never run this cool under either OS version prior to battery calibration.

---

### Post by Richard Kut on 2007-05-04
Hello jgcamp99! That is great news. Thanks for sharing your discovery. I am sure that many other people had that same question, and now they will also have the answer! :)

---

### Post by kaede on 2007-05-05
i do currently running ubuntu around 60 - 70 . even last night it reaches 77 . OMG

after that all application seems a little bit lagging. seems like this version ubuntu can't get work out with my notebook ACPI. anyone know how to deal with this. i do clean up the dust behind the fan. it helped actually (when im running windows) but doesn't make any effect when im on ubuntu. :(

---

### Post by jgcamp99 on 2007-05-06
Well, that was a bit premature. The battery calibration worked for a few battery cycles, but I wanted to thoroughly test and investigate it. The notebook ran better until the 3rd battery cycle charge to discharge. Now it's back in the 60* C range for the cpu, especially when updating. And the past couple of charge cycles it was running right at 48-51* C.

The fan only comes on around 63* C. I would say it's OS X like, but with my Powerbook, (867 12" model) the fan comes on and shuts off around 50* C telling me that it's power management works and there is some fan control. I think whatever fan control in the 60+* C range is more attributable to Intel cpu's having a shutdown feature built into them. I think if I had an older AMD notebook system, it would've fried itself by now ? I'm going to have to do more research. This problem is back again and unresolved.

---

