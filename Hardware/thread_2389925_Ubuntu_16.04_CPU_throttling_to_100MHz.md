---
title: "Ubuntu 16.04 CPU throttling to 100MHz"
date: 2018-04-23
forum: Hardware
---

### Post by boyanbratanov on 2018-04-23
I've been using an Acer ES1-132 laptop with N4200 CPU for a while now with Ubuntu 16.04 Mate and KDE. 

So far for the most part it worked great, however I've been experiencing CPU throttling below the scaling minimum.
[FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][COLOR=#000000][FONT=monospace]cpufreq-info gives the output below. It's the same for all cores.
[/FONT][/COLOR][FONT=monospace][COLOR=#000000]
[/COLOR][/FONT]> [INDENT][FONT=monospace]cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.                                                           
  hardware limits: 800 MHz - 2.50 GHz                                                            
  available cpufreq governors: performance, powersave                                            
  current policy: frequency should be within 800 MHz and 2.50 GHz.                               
                  The governor "performance" may decide which speed to use                       
                  within this range.                                                             
  current CPU frequency is 2.26 GHz.    
[/FONT][/INDENT]


According to the output above the minimum scaling frequency is 800MHz, but when throttling the CPU occasionally goes down to 100MHz for a duration of 30-60sec, which renders the system unusable for the duration. I assume the throttling is triggered by the CPU temperature rising to 72-73'C. It usually happens when I have a youtube video or stream running in the background for a long time. 

However I do not experience this issue in Windows 10. In Windows if CPU temperature is around 70, the CPU clock stays at about 1GHz until temperatures drop and the system is still usable meanwhile.

I had no luck changing the governor and disabling ondemand as suggested in this thread: [https://ubuntuforums.org/showthread.php?t=2330427](https://ubuntuforums.org/showthread.php?t=2330427)
I did the regular kernel updates in the past few months, but nothing affects the scaling.

I do not plan upgrading to 18.04 anytime soon. Any other suggestions on how to fix the scaling will be greatly appreciated.

---

### Post by Yellow Pasque on 2018-04-23
First off, clean out your vents with compressed/canned air (electronics cleaner/duster). I just did a laptop where the heatsink and exhaust vent didn't even look that bad, but the small intake vent on the bottom was clogged and that disrupted the airflow. It fixed the issues my friend was having (fan running, thermal shutdowns).

---

### Post by boyanbratanov on 2018-04-24
Thank you, but the laptop is only a couple of months old and also has no fan. That said, it handles temperatures and my workload pretty well... in Windows. 

I did some reading online, but didn't find anything for my case, so I'm really hoping that someone will give me some tips on how to configure CPU frequency scaling properly or explain if there's some other issue. Basically I want to force the minimum frequency to not go below 800MHz as it is doing now.

---

### Post by Yellow Pasque on 2018-04-24
EDIT: Nvm (sorry)

---

### Post by boyanbratanov on 2018-04-25
So it seems Chromium wasn't using hardware acceleration for video decoding. I enabled Override software rendering list in chrome://flags/ and it seems to use a lot less CPU now. 

Clock still occasionally drops to 100MHz when system is under heavier load for long periods and nothing seem to change the allowed minimum clock frequency. So it's either a bug (similar to Bug #1568610 in Launchpad) or the CPU is forcing the throttling on hardware level, or Ubuntu is still using more CPU than it should.

---

### Post by boyanbratanov on 2018-04-29
So I found these threads:

[https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1480349](https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1480349)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=815990](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=815990)
[https://askubuntu.com/questions/803933/processor-frequency-gets-reduced-and-doesnt-recover](https://askubuntu.com/questions/803933/processor-frequency-gets-reduced-and-doesnt-recover)

According to them the culprit for dropping CPU frequency under hardware limits is thermald. 

I removed the package as suggested, made sure intel-microcode is the latest version and turned off/on my pc. This seems to have resolved the issue. CPU scaling is working fine, temps and frequencies are reasonable even under load.

---

