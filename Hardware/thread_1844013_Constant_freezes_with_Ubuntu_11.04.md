---
title: "Constant freezes with Ubuntu 11.04"
date: 2011-09-14
forum: Hardware
---

### Post by dyous87 on 2011-09-14
I have a Dell Studio XPS 16 that constantly freezes from time to time in which I need to do a hard reboot just to shut it down and start it back up.

This has been happening through several fresh reinstalls so I now its not a problem isolated to my installation. 

Recently I had a SMART error notifying me that my hard drive was spiking in heat and would be failing soon. I swapped out the hard drive for a new one and hadn't had a freeze for quite some time until today. I had thought that the constant freezes I was getting had to do with the failing hard drive but apparently something else is causing it.

Is there anyway I can find out through some logs or with some type of Utility what is causing these lock ups. I'd like to know if it is a hardware failure or if its some type of software confliction.

The full specs of my machine are as follows:

[LIST]
[*]Intel Core i7
[*]6 Gb DDR3 Ram
[*]500 GB HDD
[*]ATI Mobility Radeon (Not USING Restricted Drivers as they do not seem to work as well as the ones that came preinstalled on installation)
[/LIST]
Any help would be greatly appreciated.

David

---

### Post by 2F4U on 2011-09-14
If the first hard drive died due to heat problems and you didn't change anything towards that problem, you may still have these issues. Is this a laptop or desktop machine? If it is a desktop machine, you could open the case and see if this makes things better. If it fixes the problem you may need to do something to get the heat out of the machine, for example install additional fans.

---

### Post by diasf on 2011-09-14
Yeah, overheating is a good first bet. Monitor the temperatures (lm-sensors, sensors).  Check if your fans are really working, etc etc. And no point swapping hardware without finding the problem :)

---

### Post by dyous87 on 2011-09-14
Overheating isn't the issue. At first before I changed the hard drive I thought it may be. The hard drive it turned out was causing the over heating as it was bringing the system close 100 95-100 degrees Celsius. Since I changed it my system temperature and processor core temperatures have not gone above 65.

---

### Post by diasf on 2011-09-14
One quick way of knowing if it is hardware os software is to work a while on a liveCD. Maybe cpuburn for a while...

But tbh, I'm starting to think memory problem. Have you tried to run a memtest? Not the whole deal, just the few N tests (I really do not remember, but i'm sure google knows :P).

---

### Post by dyous87 on 2011-09-14
I was beginning to think that. I'm going to run a memory test right now to see if any of my ram strips are damage or something.

I'll let you guys know, thanks!

---

