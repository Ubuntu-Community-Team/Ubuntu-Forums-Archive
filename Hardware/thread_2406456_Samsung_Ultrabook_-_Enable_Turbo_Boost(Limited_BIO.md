---
title: "Samsung Ultrabook - Enable Turbo Boost(Limited BIOS)"
date: 2018-11-21
forum: Hardware
---

### Post by peetyo on 2018-11-21
Hello everyone,
I have the following issue with my Samsung 7 series Ultrabook - NP740-U3E. It has been very slow ever since I got it I believe but recently I found the issue and found a way to partially solve the problem in Windows 10. Basically, the performance of the Intel Core i5-3337U @ 1.80GHz with a Turbo Boost to 2.7Ghz was limited. The Turbo Boost never started and even basic activities like browsing the web and chatting were unpleasant. I found out that my processor is not performing well by using UserBenchmark and comparing with similar configurations to mine. 
I started looking for solutions on how to enable the turbo boost. I'm aware that there's a setting in the BIOS but in the BIOS of my machine there isn't. It's an ultrabook and I only get a few options there. The only option that seemed relevant was CPU Power Saving Mode. I disabled it but it did not affect the turbo boost.
[ATTACH=CONFIG]281721[/ATTACH][ATTACH=CONFIG]281720[/ATTACH]

In Windows 10 I found a quick and easy solution to override this Turbo Boost BIOS setting. I use RealTemGT a monitoring app when I start the machine. The settings in there allow me to enable Turbo Boost and the laptop starts to work like a charm. (This has to be done every time I start windows...)
[ATTACH=CONFIG]281722[/ATTACH]
Yesterday I installed Ubuntu 18.04 LTS and I've been trying to enable the turbo boost. The OS is lighter and runs better without the turbo boost than Win 10 but it still gets laggy.
I wanted to know if there's an app similar to RealTemp with such a Turbo Boost setting or another quick way to manipulate the system. I don't think I'm ready to hack my BIOS to get full configuration settings since I'm new to the topic.
In the Ubuntu terminal I ran a few commands following this answer in StackExchange:
[ATTACH=CONFIG]281723[/ATTACH]
I got the highlighted response(Example 1) "Operation not permitted".
I would be grateful if someone tries to help. I want to start using Ubuntu but I can't do it if the ultrabook is running slow and laggy. Thank you!

---

### Post by Doug S on 2018-11-21
The simplest and most primitive way to do what you are attempting is via your last example, which does suggest that your issue is a BIOS setting. I'll leave it to others to comment on other tools, that I never use.

I would suggest to checkout some basics, such as which CPU frequency scaling driver and governor you are using. I suspect intel_pstate and powersave, but lets check:

```
doug@s15:~/temp$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_driver[/COLOR]
/sys/devices/system/cpu/cpufreq/policy0/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy1/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy2/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy3/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy4/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy5/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy6/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy7/scaling_driver:intel_pstate
doug@s15:~/temp$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpufreq/policy0/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy1/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy2/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy3/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy4/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy5/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy6/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy7/scaling_governor:powersave

```And without any real reason, let's look at your intel_pstate settings:
```
doug@s15:~/temp$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:42
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:23
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:18

```

---

