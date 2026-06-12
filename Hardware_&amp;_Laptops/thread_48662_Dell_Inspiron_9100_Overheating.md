---
title: "Dell Inspiron 9100 Overheating"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by delltony on 2005-07-13
I have question in regard to overheating with Linux. I'm not sure if anything can be done but if it can be I would like to hear about it. Here is the issue.
I have ubuntu/kubuntu 5.04 installed on my system and when I had first installed it everything was great ran fast and what have you. Well now It runs fast but then after a while it degrades and I have looked at top and the cpu/memory % and the load % are fine very low actually. I then run i8kmon and notice my cpu is running at 75C I think 82 is shutdown. My fans appear to be running full throttle they are set to 2 and I can hear them running all the time. Is there something in terms of a kernal extention that can scale the cpu down so it can cool off? I heard of cpufreqd but it doesn't appear to be supported with a standard p4 processor.

Any suggestions would be great. And hold the comments in regard to Dell sucks and all that. I could say the same for other pcs but thats not the issue at hand.

---

### Post by varunus on 2005-07-13
Do you have a so-called "Mobile Intel Pentium 4?"  If you do, you can use frequency scaling by entering

```
sudo modprobe p4_clockmod
``` 

into a terminal.  Frequency scaling should start working.  To control it, add the CPU Frequency Scaler applet to your gnome panel from the right-click menu.

To make this module load every time you boot up, add "p4_clockmod" to the end of /etc/modules.

Its kind of strange that your laptop is overheating...

Good luck.

---

### Post by delltony on 2005-07-14
[QUOTE=varunus]Do you have a so-called "Mobile Intel Pentium 4?"  If you do, you can use frequency scaling by entering

```
sudo modprobe p4_clockmod
``` 

into a terminal.  Frequency scaling should start working.  To control it, add the CPU Frequency Scaler applet to your gnome panel from the right-click menu.

To make this module load every time you boot up, add "p4_clockmod" to the end of /etc/modules.

Its kind of strange that your laptop is overheating...

Good luck.[/QUOTE]

I found the following information and it solved the problem when i lowered the frequency it went from 75 to 55. As i seen and this user had stated my pc is set to un at highspeed always of 2.8 which is not so good it never has time to cool down.

This is a problem that I had with my laptop for awhile. If your computer can't even last long enough to get through compiling the kernel (understandable), then this may help. If it works it will slow down your CPU so that hopefully it lasts longer before overheating.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

If this returns performance, then your CPU is running full speed all the time. With a P4 2.5, it probably isn't supposed to be doing that. If it returns userspace, it may also be set to run full speed.

next:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

If this ONLY returns performance, then this isn't going to work for you. However, if there are other options, this might help. My computer only has performance and userspace, so I'll give you directions based on what I do. I'm not completely sure what the other choices may be, but I believe there is something like powersave, which would run you at the lowest possible frequency, and ondemand, which would ratchet up the cpu speed as it is needed. (I think ondemand is just for AMD processors, but there must be something similar for newer pentiums.) Anyway, here are the directions...

If userspace showed up in the last space, this may work.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
this will show you the frequencies your cpu can run at in kilohertz

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
this will show you the speed your cpu is running at now

you need root priveledges for the next steps so:

su
enter your root password

echo -n "userspace" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

that replaces performance with userspace which basically is a manual mode of control

in the next line, replace somefrequency with one of the frequencies that you got when you looked at scaling_available_frequencies, it should be one that is lower than your current frequency, this will make your processor much less likely to overheat for awhile, it'll also use less power

echo -n "somefrequency" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed

If this DOES work for you, I made my computer boot up to a lower speed by basically adding some of these lines to the end of the file:

/etc/rc.d/rc.local

Then I added in some alias commands so now I can easily change my speed manually by going into a terminal and typing freq2 or something like that. Anyway, hope that helps.

---

### Post by delltony on 2005-07-16
Is there an issue with cpufreq and Ubuntu and the latest kernal that uses smp? I honestly don't know if its my computer itself or what. But it stays at 75C and when i scale it down using the method i posted the lowest it gets is like 69 then it shoots back up. It use to run nice and smooth when i first installed ubuntu on here so I'm wondering if its something to do with the kernal. Cause when I run powernowd It tells me that frequency scaling is intentially disabled. I have no idea why one would want such a thing. I figured that you would want the computer to run at slow speed when idle then when you do something kick it up a knotch. Let me know guys. I know i'm not the only one out there with a dell computer (laptop) that is having heat issues.  Help would be appreciated I'm counting on you :)

---

### Post by delltony on 2005-07-17
UPDATE:
 Problem resolved. Something that owners of the Dell laptops should take note of. You must at some point open up the case of this thing and clean the insides of it. The heatsink commonly gets dust on it causing it to overheat and the fans appear to be clean on the outside but when i checked them it looked like the lint trap from my dryer. OUCH! I went from running a constant 75+C temp to running at 52C constant. Big difference and the speed is better too cause the cpu is not overheating causing a processor scale down.
I feel like i have a new computer haha

---

### Post by doranchak on 2006-04-01
I have been wrestling with my Inspiron 9100 + Ubuntu for about a month now with its performance issues.  It was getting progressively slower.  First I thought it was a video card problem.  Then I thought it was the HD.  Then the wifi.  Only after many aggravating weeks did I read your suggestion to clean the fans.  And, same as yours, my Inspiron's fans were covered with a nice thick coat of dryer lint.  :)

I dusted the hell out of the fans and then restarted the machine.  HUUUUUGE difference.  THANKS SO MUCH for your post!

I came very close today to scraping the HD and re-installing ubuntu, thinking it was something I had done wrong to some configurations.  Good think I read your post - it saved me TONS of time!

---

### Post by maraschin on 2006-08-16
I've tried everything and it will not install Ubuntu! I've not tried any other distro...

It just freezes in the middle of the installation process or even when the system is booting! It does it every single time in a different point.

I've clean the fans first thing before try to install...
it has plenty of air flowing...

The strange thing is that I did have it installed before, I'd the test version and it was working even after the upgrade but than I decided to reinstall it... NOP, it will not work at all... it just freezes!

I'm using a CD printed by Ubuntu and I've run a check on it, so no errors there too...

BTW, it does work with windows without any problems!
I even found an update for the BIOS but it still the same..

Anyone have any idea?!

---

### Post by maraschin on 2006-08-16
Here is how did I manage to overtake the heating problem and install Ubuntu...

I got the alternative CD and did a text installation... that was all!
The normal live CD will just not install and I couldn't even run it normally. It would keep hanging...

Well, I manage to install ubuntu but as soon i get into X it will soon have the temperature above 72deg and crash!

---

