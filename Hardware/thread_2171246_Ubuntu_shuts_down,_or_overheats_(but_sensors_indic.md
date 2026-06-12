---
title: "Ubuntu shuts down, or overheats (but sensors indicate max ~50c), windows does not..."
date: 2013-08-29
forum: Hardware
---

### Post by manje2 on 2013-08-29
Hi everyone,

My debut on these forums: 

I have been using ubuntu for some time now and mostly on an old pc for multimedia purposes (so that's my main experience). I also run a dual boot (win7/ubuntu12.04) setup on my laptop which is a Fujitsu Siemens, Amilo Pi 2530. However, ubuntu has not been working well on my laptop. During the last year my laptop had serious CPU-overheating issues in both windows and ubuntu. I am no expert on hardware, so a friend offered to show how to properly remove dust from the fan and replaced the heat-transfer paste on the motherboard. After this, my max temperature during a regular session went down from 85c (peak) to <50c.

When running windows everything is great. I still check the temp regularly and it stays well below 50 mostly. In Ubuntu I use the lm-sensors package to monitor the cpu, which provides similar values (maybe 3 degrees higher on average). It also works very well - no lagging, or slowing down - until however the laptop just shuts down instantly. I rebooted a couple of times with the same consequence and the temperature going up a little everytime until it was mostly 50c. When I decided to reboot into windows directly after this it was incredibly slow and the fan was not working properly (stopping and restarting). It would be my guess that this is a result of overheating, while values read from the sensors did not indicate this (50c at most is fine, right?). 

I also tried to check some error log-files, but I don't know how to access them, and I am a bit afraid to reboot into ubuntu because of damage to the CPU that might occur (?).

Does anybody have experience with something like this, or would you know how I can fix this? I would very much like to use Ubuntu as my day-to-day OS, so your help is greatly appreciated!

Cheers,
Manje

---

### Post by mörgæs on 2013-08-30
Hi, welcome to the fora.

Around 50° C is normal range. The temperature must be much higher before BIOS shuts down a processor.

Have you tried running memtest from the boot menu?

How does it behave if you try one of the 13.04 Buntus in a live boot?

---

### Post by manje2 on 2013-08-31
Thanks for the reply. I have ran memtest and there were no errors. I think however (fingers crossed) that I solved it. Windows was running fine until I was playing videos and it shut down as  it did with ubuntu, which seemed to me an indication that it was a hardware  problem. There seemed to be no proper contact between the heat sink and the units, so I applied some more thermal paste. Now both Ubuntu and Windows seem to be running fine. So, solved I hope!

---

### Post by mörgæs on 2013-08-31
Good, then please mark the thread 'solved'. 
If the problem reappears you can always remove the 'solved' flag.

---

