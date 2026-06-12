---
title: "Linux CPU frequency scaling governor"
date: 2014-08-27
forum: Hardware
---

### Post by HugoNotte on 2014-08-27
Recently I started making DVDs from loads of AVI video files, series I downloaded over the past few years, using DeVeDe. I noticed that making a DVD with 3 episodes on 14.04 takes around 49 minutes. On the same computer under Windows 7 DeVeDe only needs around 42 minutes.
So I started searching for what might cause this. The computer got an AMD FX8320 processor and I thought, that linux in general being better with multi threaded computing, it should be at least as fast, as Windows 7, which isn't all that great with processor scheduling on the AMD Bulldozer architecture.


To my surprise I found out, that under linux the processor cores run nowhere near the maximum frequency, but only at partial frequencies between 1.4 - 2.9 GHz, despite the CPU being busy at around 40%. Even when cores spike to over 50% usage, the frequency doesn't necessarily come up all the way to the (overclocked) 4 GHz. But even on stock speeds, the cores seem to get "stuck" at frequencies well below 3.5 GHz.
When running Windows 7, the CPU is very quick to sprint up to maximum frequencies with very little load applied and runs constantly at 3.5 GHz (or 4 GHz overclocked) when DeVeDe is running.


I read up on it and found that /sys/devices/system/cpu/cpufreq/ondemand/up_threshold is set to 95%, meaning that only when a CPU core gets to 95% load, it's frequency is stepped up. Quite a few people have complained, that their laptops / PCs seem oddly sluggish under Linux.
Unfortunately, one can not easily change that value in the up_threshold configuration file. I changed it with gedit to a value of 40%, which made the CPU a lot more lively and DeVeDe all of a sudden worked as fast under Ubuntu as it does under Win7, but first of all one gets a bunch of error messages when trying to change the value in up_threshold and secondly after each reboot it's back to 95%.


I thenchanged the CPU governor from "ondemand" to "performance", which then means all 8 cores run at max frequency all the time, which is again, not necessary as it uses more power when the CPU is idle.


The only way seems to be a script to be executed at system start, setting a new value for the ondemand governor.


In order to make sure this was not an AMD specific issue, I checked on my Ivybridge i5 laptop, the results were the same.


My question is, how come does Linux (this issue seems to be a general Linux kernel issue, as it occurs on all kinds of different distros, not only Debian based ones) hold back the CPU for such a long time, making the computer perform noticeably slower ( almost 20%) under partial load than what it could be? Since I get pretty much the same battery life on my laptop whether I run Windows 7 or Linux, it can't be a major power saving issue either.


Can't the Ubuntu developers please include either an option under settings or preferences, where one can choose the up_threshold value or simply set the value to something like 40% right from the start?


At the moment, the available governors are pretty static: powersave (locks at lowest CPU freq.), performance (locks at highest CPU freq.) and ondemand (variable CPU freq. but sluggish to step up).


Not everybody is up to writing a script to modify the setting. But I think if Linux wants to keep up with Windows, it should offer similar performance, what about people playing games and doing other stuff apart from web surfing and reading e-mails? Haven't they noticed this yet?

---

### Post by Doug S on 2014-08-28
This is a very complicated subject. And finding a universal solution is not easy, as optimal settings for one application might be non-optimal for another.
 The recent trend has been towards energy savings, while at the same time trying to minimize impact on performance.> **HugoNotte said:**
> I then changed the CPU governor from "ondemand" to "performance", which then means all 8 cores run at max frequency all the time, which is again, not necessary as it uses more power when the CPU is idle.If the CPU goes into a high enough C state, then the power is minimal. For your application I would be tempted to use performance mode.
 
> **HugoNotte said:**
> My question is, how come does Linux (this issue seems to be a general Linux kernel issue, as it occurs on all kinds of different distros, not only Debian based ones) hold back the CPU for such a long time, making the computer perform noticeably slower ( almost 20%) under partial load than what it could be? Since I get pretty much the same battery life on my laptop whether I run Windows 7 or Linux, it can't be a major power saving issue either.Because there is no need to up the CPU p state until the CPU needs it, and as long as the CPU is not fully utilized it thinks it doesn't need it. For at lot of applications and periodic tasks this approach gives a pretty good energy / performance tradeoff.
 
Now, along comes "DeVeDe" (which I am not familiar with) and it might have some strange tradeoffs between threads and CPU that doesn't behave well. I know for sure that the ffmpeg test in the phoronix test suite has some very bizzare stuff going on, such that the frequency governors don't behave well with it. I assume "DeVeDe" is similar.
 
Anyway, in kernel 3.17RC1 (I think it was) there was a change made to acpi-cpufreq such that the load response curve has shifted somewhat. See [1]. (I don't know which frequency governor you are using). The intel_pstate frequency driver has been under pressure to shift its response curve more towards saving more energy, and it probably will sometime in the 3.17 cycle.
 
> **HugoNotte said:**
> Can't the Ubuntu developers please include either an option under settings or preferences, where one can choose the up_threshold value or simply set the value to something like 40% right from the start?This is an upstream issue, not an Ubuntu issue.
 
> **HugoNotte said:**
> At the moment, the available governors are pretty static: powersave (locks at lowest CPU freq.), performance (locks at highest CPU freq.) and ondemand (variable CPU freq. but sluggish to step up).Note: I can only speak knowledgeably about intel processors. Actually performance mode does NOT lock the highest CPU frequency, the processors internal governor can back off the frequency. However the load frequency response curve is indeed very fast. See [2] this.

[1] [https://docs.google.com/spreadsheets/d/16kDBh5lyc6YvBnoS1hUa1t2O38z0xrWvaEj5XtJ8auw/edit?pli=1#gid=2072493052](https://docs.google.com/spreadsheets/d/16kDBh5lyc6YvBnoS1hUa1t2O38z0xrWvaEj5XtJ8auw/edit?pli=1#gid=2072493052)
[2] [https://bugzilla.kernel.org/attachment.cgi?id=137641](https://bugzilla.kernel.org/attachment.cgi?id=137641)

---

### Post by HugoNotte on 2014-08-30
> **Doug S said:**
> This is a very complicated subject. And finding a universal solution is not easy, as optimal settings for one application might be non-optimal for another.
 The recent trend has been towards energy savings, while at the same time trying to minimize impact on performance.If the CPU goes into a high enough C state, then the power is minimal. For your application I would be tempted to use performance mode.
 
Because there is no need to up the CPU p state until the CPU needs it, and as long as the CPU is not fully utilized it thinks it doesn't need it. For at lot of applications and periodic tasks this approach gives a pretty good energy / performance tradeoff.
 
Now, along comes "DeVeDe" (which I am not familiar with) and it might have some strange tradeoffs between threads and CPU that doesn't behave well. I know for sure that the ffmpeg test in the phoronix test suite has some very bizzare stuff going on, such that the frequency governors don't behave well with it. I assume "DeVeDe" is similar.
 
Anyway, in kernel 3.17RC1 (I think it was) there was a change made to acpi-cpufreq such that the load response curve has shifted somewhat. See [1]. (I don't know which frequency governor you are using). The intel_pstate frequency driver has been under pressure to shift its response curve more towards saving more energy, and it probably will sometime in the 3.17 cycle.
 
This is an upstream issue, not an Ubuntu issue.
 
Note: I can only speak knowledgeably about intel processors. Actually performance mode does NOT lock the highest CPU frequency, the processors internal governor can back off the frequency. However the load frequency response curve is indeed very fast. See [2] this.

[1] [https://docs.google.com/spreadsheets/d/16kDBh5lyc6YvBnoS1hUa1t2O38z0xrWvaEj5XtJ8auw/edit?pli=1#gid=2072493052](https://docs.google.com/spreadsheets/d/16kDBh5lyc6YvBnoS1hUa1t2O38z0xrWvaEj5XtJ8auw/edit?pli=1#gid=2072493052)
[2] [https://bugzilla.kernel.org/attachment.cgi?id=137641](https://bugzilla.kernel.org/attachment.cgi?id=137641)

Thanks for your reply. At the moment I am using the [COLOR=#333333][FONT=Lucida Grande]It's 3.13.0-24-generic kernel. I will try and upgrade to the 3.17 kernel, once it gets released.
I am just wondering, that Windows seems to be able to find a much better balance between power saving and offering power, when necessary. I have noticed, that under Linux some programs manage to step up the CPU core speeds much better, than others. As to the "performance" governor, it does seem to keep all cores at max frequency on both, the Intel i5 mobile and the AMD FX8320.[/FONT][/COLOR]

---

### Post by Doug S on 2014-08-30
> **HugoNotte said:**
> [COLOR=#333333][FONT=Lucida Grande]As to the "performance" governor, it does seem to keep all cores at max frequency on both, the Intel i5 mobile and the AMD FX8320.[/FONT][/COLOR]The AMD, I don't know. The i5, the processor itself can backoff the clock frequency. Note that if the acpi-cpufreq governor is being used, it doesn't report actual frequency but rather requested Pstate converted to frequency, which may be incorrect. If the intel_pstate governor is being used, it reports actual frequency.

---

