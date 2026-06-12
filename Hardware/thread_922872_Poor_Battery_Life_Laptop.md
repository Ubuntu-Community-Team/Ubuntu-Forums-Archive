---
title: "Poor Battery Life Laptop"
date: 2008-09-17
forum: Hardware
---

### Post by IMELucky on 2008-09-17
Issue: My laptop computer will achieve 3-4 hrs. of battery while running Windows XP. However, it will only get 1.5 hrs on Ubuntu. I have dimmed the backlight all the way down, but I can't seem to get longer battery life. Additionally info below

Computer: HP Compaq nc6400
OS: Windows XP, Ubuntu 8.04 (Wubi Installation)

Battery Life on Windows: 3-4 Hours
Battery Life on Ubuntu: 1.5 Max

Again, I can't think of any other items to check to increase my battery life. Also, this is the battery life I get when the system is idle, so it's not like I'm compiling software or playing games.

Any advice will be appreaced!

Regards,
IMELucky

---

### Post by RedPandaFox on 2008-09-17
> **IMELucky said:**
> Issue: My laptop computer will achieve 3-4 hrs. of battery will running Windows XP. However, it will only get 1.5 hrs on Ubuntu. I have dimmed the backlight all the way down, but I can't seem to get longer battery life. Additionally info below

Computer: HP Compaq nc6400
OS: Windows XP, Ubuntu 8.04 (Wubi Installation)

Battery Life on Windows: 3-4 Hours
Battery Life on Ubuntu: 1.5 Max

Again, I can't think of any other items to check to increase my battery life. Also, this is the battery life I get when the system is idle, so it's not like I'm compiling software or playing games.

Any advice will be appreaced!

Regards,
IMELucky

Have you tried diabaling all unused services, like bluetooth and WiFi if you have them

---

### Post by IMELucky on 2008-09-18
I don't have Blue-Tooth, and I need Wifi.

Also, wifi runs on my Windows and I still get a significantly better battery life on Windows.

Are there other services I could disable? I can't think of any off the top of my head.

---

### Post by wenuswilson on 2008-09-18
[www.lesswatts.org](www.lesswatts.org) I found that the other day. Some useful stuff.

---

### Post by kaivar on 2008-09-18
Hi, I'm experiencing the same thing. On vista the battery will last 3-something hours while it will be effectively halved on ubuntu (1hr55 mins). I tried a lot of things I found all around the Internet, that included minimizing hard disk access, lowering gpu, setting the cpu cores to run at the lowest (cpufreq powersave setting), brightness lowered as far as it can go, disabled everything else I didn't need to run ubuntu (even disabling every eyecandy from compiz) to no avail. Fully charged (like, for example, coming from a full charge 3-something hours in vista), it will say 1hr55mins.

Funny thing though, if I run acpi from terminal, it will always show more time left than gnome-power-manager...:confused: Knowing that, I set g-p-m not to do anything when battery is critical. Laptop is still running 15 minutes after it hits 0%. And acpi will report another 20 or so minutes left. 

If it's a bug, it's just an annoying bug... but I'm concerned that the capacity of the battery will get used to ubuntu's fully charged 1h55min and it will soon carry over to vista (and I keep vista around primarily because it WILL last longer than ubuntu).

Anyone know what's going on here? :confused:

---

### Post by dsm iv tr on 2008-09-18
Part of the reason g-p-m reports a different number is because it does its own power profiling. You can dig around in gconf to turn that off, I think. `acpi -V` always gives me a time at least 2 hours greater than what g-p-m says, and ACPI is always correct on my machine when I do a full discharge.

On a side note, I'm always surprised at threads like these - I get 6 hours and 45 minutes out of a full charge with whatever the high-capacity Dell battery on a Vostro 1000 is. I have the brightness down to the lowest possible, cpufreq in 'conservative', and have applied the suggestions from lesswatts and disabled services and modules I don't use. I don't say this to brag, I say this because surely if I can eke that much out of what was an estimated 3.5hr battery (new, in Windows XP with power save on), then there must be a configuration issue somewhere.

---

### Post by Nepherte on 2008-09-18
This topic should get you started: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

---

### Post by AinsleyKath on 2008-09-18
you can save the battery life by taking care of it in following ways:

Do not leave a charged battery dormant for long periods of time.  Once charged and see to that you should at least use the battery at least once every two to three weeks.

---

### Post by kaivar on 2008-09-18
> **dsm iv tr said:**
> On a side note, I'm always surprised at threads like these - I get 6 hours and 45 minutes out of a full charge with whatever the high-capacity Dell battery on a Vostro 1000 is. I have the brightness down to the lowest possible, cpufreq in 'conservative', and have applied the suggestions from lesswatts and disabled services and modules I don't use. I don't say this to brag, I say this because surely if I can eke that much out of what was an estimated 3.5hr battery (new, in Windows XP with power save on), then there must be a configuration issue somewhere.

I was hoping for the same thing, actually. Vista will report 3 hours on a full charge, probably XP will report something higher... but knowing that Ubuntu should be less of a pig than either Vista or XP when it comes to power, I'm dismayed that even after applying a lot of "power-saving" configurations (I did try lesswatts and disabling services/modules) it still comes up to about two hours.

I'll try draining and charging the battery a few times to see if that would help... I'm now on the second cycle and have gained 5mins. Still, thats nothing compared to Vista.

Such a shame, too, because I really like Ubuntu after being on M$ ever since I typed my first cd command on DOS a long time ago... :D

(Now if only the merchandise wasn't too expensive... :-k)

---

### Post by Soupcan on 2008-09-18
I only got about 1:30-1:45 on my HP dv6000. I managed to get it to 2:15 by doing 3 empty/charge cycles. Nothing I do makes it last any longer than that.

---

### Post by Leischa on 2009-01-18
I have exactly the same issue on my HP dv 2000. I get an hour and a half on Ubuntu and nothing I do makes much difference.

---

### Post by sandip26879 on 2009-01-18
Same case in my Acer Aspire One.

---

### Post by iggykoopa on 2009-01-18
you can try my power management gui here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) it's been getting good results for people and I need more people to help test it out. It has options for all the lesswatts stuff and some others.

---

### Post by happydog500 on 2009-01-18
I have a full battery in XP, when I ran the Live CD, it went into hibernate because I got a "battery low" warning. As soon as I plugged back in, I noticed it said, "100%". 
 Chris.

---

