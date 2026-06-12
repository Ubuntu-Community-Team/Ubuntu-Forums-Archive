---
title: "Ubuntu reduced 50% of battery life"
date: 2009-03-05
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-05
At first I thought it was my delusion to think that my battery life drained so much faster than I was in Windows. I just used a clamp meter to measure to current and to my surprise Ubuntu draws 52W during idle and Windows draws only 35W, with the same configuration: lowest brightness, wifi off, usb on, speakers muted, cd rom idle. That explains why when I was in library Ubuntu only allowed me no more than 1 hour but Windows can run more than 1 hour and 45 minutes. 

I know my method of the measuring is not so accurate, but one thing is for sure, Ubuntu draws much more power than Windows. 

I have already enabled laptop-mode. It doesn't help a lot (maybe 2W less). 1 hour is really too short for me! If I need to run Ubuntu then I may buy another battery. Or should I use Windows when I am outside and Ubuntu at home? [Perhaps that's the point of dual boot... heh] 

My cpu supports EIST (speedstep) but the BIOS doesn't. So there's no way to turn it on either in Windows or Ubuntu. But Windows still draws much less power than Ubuntu when idle. 

Any one who knows how to prolong the battery life please feel free to tell me! Thanks!

--------------------------------------------------------------------
Other interesting results: 
Both Ubuntu and Windows draw around 63W during stress
WiFi on 			1.54W
WiFi connected and busy		3W
Harddisk Busy 			2w
dvd rom busy 			4.4-6.6W
speaker volume max		1W
USB mouse			0.5W (this 0.5W reading is quite accurate, the power rating of the mouse is 5V 100mA)

---

### Post by Squid Spectre on 2009-03-05
Are you using compiz? The overhead on the desktop effects could have an impact. I would also check to make sure bluetooth is off, normally whe nyou see that signifigant of a drop in battery life bluetooth is the culprit.

---

### Post by afeasfaerw23231233 on 2009-03-06
It doesn't have a bluetooth and I can't even get a 3D driver. Therefore no compiz too. But I just found out using the argument idle=mwait instead of idle=poll reduces the discharging rate from 3000mA to 2200mA. And the cpu produces less heat too! I think the problem is solved. 

Here's the link about the kernel parameters. [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
[B]776		idle=		[X86]
777				Format: idle=poll or idle=mwait
778				Poll forces a polling idle loop that can slightly improves the performance
779				of waking up a idle CPU, but will use a lot of power and make the system
780				run hot. Not recommended.
781				idle=mwait. On systems which support MONITOR/MWAIT but the kernel chose
782				to not use it because it doesn't save as much power as a normal idle
783				loop use the MONITOR/MWAIT idle loop anyways. Performance should be the same
784				as idle=poll.[/B]

But I cannot find the definition of apicmaintimer and noapictimer. So my now only has this argument [idle=mwait] and everything seems working fine.

---

### Post by Jekshadow on 2009-03-06
Some steps:
[LIST]
[*]Turn off any wireless you don't need
[*]try not to charge other gadgets (like ipods)
[*]Hibernate when not using
[/LIST]

What might be causing it:
[LIST]
[*]Transparent graphics
[*]background applications
[*]Screen Brightness
[/LIST]

Also try turning off widgets and stuff you dont need. Also reduce display, as ubuntu might keep it brighter than windows.

---

### Post by sdennie on 2009-03-06
You may be able to diagnose more of the problem with the powertop tool:

```

sudo apt-get install powertop
sudo powertop

```

Also check [www.lesswatts.org](www.lesswatts.org) for more battery saving information on linux.

---

### Post by rapachooie on 2009-03-06
I installed 8.10 and I get probably an extra 30-45 minutes charge from my Toshiba notebook, no extras added like Powertop added or anything...

Thats better power management than Vista in my eyes.

---

