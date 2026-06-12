---
title: "Strange CPU Temperature readings"
date: 2012-02-12
forum: Hardware
---

### Post by Sagorn on 2012-02-12
I'm running Ubuntu 10.04, and a recent issue (random logouts when starting firefox or nautilus, which I still haven't figured out) led me to investigate the possibility of my computer overheating.  So, I installed lm-sensors to check on the temperature of various components, and became even more confused.

I have an AMD Phenom II X3 720 installed, and as expected, there were 3 cpu temperatures listed, helpfully labeled temp1, temp2, and temp3.  Immediately after startup, however, the temperatures listed were 28C, 39C, and 79C.  Under load (a couple minutes of rendering in blender), the temperatures listed were 28C, 55C, and 79C.  According to system monitor, all 3 cores were active.
The 39->55 result for temp2 seems reasonable enough, but the results for temp1 and temp3 seem bogus, with the 79C being rather worrying.
I installed another temperature monitoring package (computertemp), but presumably it's reading the sensors in the same way, as it gives the same temperatures.
Does anyone know if:
a) there's some trick to the labeling of the sensors that would explain this
or
b) there are other ways I could check these readings

Thanks for any assistance you can provide.

---

### Post by LinuxFan999 on 2012-02-12
> **Sagorn said:**
> I'm running Ubuntu 10.04, and a recent issue (random logouts when starting firefox or nautilus, which I still haven't figured out) led me to investigate the possibility of my computer overheating.  So, I installed lm-sensors to check on the temperature of various components, and became even more confused.

I have an AMD Phenom II X3 720 installed, and as expected, there were 3 cpu temperatures listed, helpfully labeled temp1, temp2, and temp3.  Immediately after startup, however, the temperatures listed were 28C, 39C, and 79C.  Under load (a couple minutes of rendering in blender), the temperatures listed were 28C, 55C, and 79C.  According to system monitor, all 3 cores were active.
The 39->55 result for temp2 seems reasonable enough, but the results for temp1 and temp3 seem bogus, with the 79C being rather worrying.
I installed another temperature monitoring package (computertemp), but presumably it's reading the sensors in the same way, as it gives the same temperatures.
Does anyone know if:
a) there's some trick to the labeling of the sensors that would explain this
or
b) there are other ways I could check these readings

Thanks for any assistance you can provide.
The temperature can be checked through the BIOS on most motherboards. Check there and see whether the temperatures are the same or different.

---

### Post by Sagorn on 2012-02-12
Thanks for the tip.
I've checked BIOS (for reference, I have a Gigabyte MA770T-UD3P motherboard).  It looks like temp1 (the 28C) is the "System Temperature" (and this has actually increased to 29C now, so this seems to be working), and temp2 is listed as the CPU temperature, which makes sense.  However, temp3, the 79C, is nowhere to be found in BIOS.

---

### Post by ahallubuntu on 2012-02-12
I've not had good luck with CPU temperature monitoring tools in Linux, unfortunately.  I too use the BIOS or (shudder!) Windows to check CPU temperature when debugging something like an overheating CPU.

Of course, if you fear the CPU is overheating, check your CPU fan to make sure it's spinning properly.  If the computer is a few years old, it might help to clean the dust out of the heat sink, if any.  Some BIOSes have modes to adjust the CPU fan speed "smartly" and you can play with those in BIOS Setup.

If you want to stress test your CPU, try one of the utilities on the Ultimate Boot CD to push the CPU so it gets really hot.  If you can run one of these for a half hour without a lockup, your CPU is probably cooling fine.  Doing this outside of your Ubuntu installation also rules out an Ubuntu issue.

---

### Post by Sagorn on 2012-02-13
Thanks for the suggestions

All of my computer fans seem to be spinning properly, and are only somewhat dusty.  My cpu fan is already set to spin based on temperature, and that seems to be working.

I did an hour of cpu stress-testing off of the ultimate boot cd, which managed to get my processor temp up to the high 50s.  The system temp was mid 40s.  temp3 (which remains unidentified) was still  79.  At this point, one of my hard drive sensors read as having a temperature of -1C.

As such, I'm fairly certain overheating isn't the problem, and that at least some of my temperature sensors are... unreliable.

If anyone does think of anything temp3 might indicate, please let me know, but in the meantime I'll probably be ignoring a couple of my temperature sensors while I try to track down what's causing me to log out.

---

### Post by ahallubuntu on 2012-02-13
I agree - does not sound like an overheating problem in your case.

I would just ignore those bogus temperature sensor readings.  I've seen lots of false readings on sensors over the years.  The software that is trying to decipher them for you has to guess which readings are "sensors" and sometimes it guesses wrong.  I've seen "temperatures" go over 100C (water boiling!!!) on perfectly cool-running systems.  The BIOS reading is probably the only one I'd take completely seriously.

I still use 10.04 on my laptop, but it does have some issues on certain hardware that could cause problems like you describe.  Sadly, the best solution may be upgrading to a newer version.  I've found 11.04 works great on some older machines where 10.04 does not work well - a number of 10.04 issues seem to have been fixed in the kernel it uses.  Unfortunately, 11.04 is supported only until October of 2012.  If you think you can use 11.04 through then and hope 12.04 LTS is solid by then, perhaps you could upgrade to 11.04 then 12.04.  (I'd personally avoid 11.10 myself given all the problems I've seen with it reported here, though my one test install seems to work OK.)

I don't like or use Unity desktop.  In 11.04, it will automatically revert to Gnome 2 if the hardware is too old, but even so you can tell it to login by default with Gnome 2 if you want on any hardware.  You can't do to this in 11.10, though you can install Gnome 3 if you like (I did in my test install).

If your problems happen frequently enough, it would be nice if you could do a test install of 11.04 and see if the problems go away before committing to use it for good.  I know many people don't have this luxury, but I have spare hard drives and plenty of backup drives so I can make image backups of my OS installs before upgrading and always revert back if something doesn't work out.  Maybe you can too?

---

