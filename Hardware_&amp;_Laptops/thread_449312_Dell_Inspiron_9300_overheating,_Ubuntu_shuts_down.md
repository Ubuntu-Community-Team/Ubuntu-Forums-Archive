---
title: "Dell Inspiron 9300 overheating, Ubuntu shuts down"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Robert Leithe on 2007-05-20
Recently my Dell Inspiron 9300 have shut down automatically, following a warning of overheating (100 o C). The first time was after leaving the machine on for a couple of days, one of which was a rather hot day.

The last time, I switched it on in the morning. It was a cloudy day and I left the blinders down. In the afternoon (roughly seven hours later) it shut down again.

This has not been a problem earlier. Has anyone had any experiences like this one? Guess I'm putting in a call to Dell Support on Monday, as the Next Day warranty is still in effect...

Sincerely
Robert Leithe

---

### Post by Kobalt on 2007-05-20
Do you have the same problem with a different OS, possibly Windows ? 100°C is a pretty high temperature. If it can be confirmed under another OS I would highly recommend returning your laptop for repair.

---

### Post by Robert Leithe on 2007-05-20
I've only installed 7.04 on my computer, so this cannot be confirmed by another OS (as I don't want to install one just for this).

Can anyone suggest a software (desklet?) for monitoring the temperature of the various components?

---

### Post by Kobalt on 2007-05-20
You can try [ComputerTemp]("http://www.getdeb.net/app.php?name=CompTemp%20Monitor").

---

### Post by Austin_KW on 2007-05-20
Check for dust, laptops can work like vacuum cleaners and may need cleaning;
Blow air thru' the outtake and if you see cloud of dust from the intakes this may have been your problem.

---

### Post by Robert Leithe on 2007-05-21
That's exactly what I ended up doing. Used a vacuum cleaner, though. Didn't have any compressed air at hand. This however, seems to have helped. The computer is still running, and doesn't feel warm to the touch. I'll leave it on overnight and see what happens...

---

### Post by Austin_KW on 2007-05-21
I would not be surprised if this fixes the problems, I have to clean out the dust from my toshiba every few weeks. You can monitor you temperature from the command line with "cat /proc/acpi/thermal_zone/THZN/temperature", checking it is within the operating range (probably 40-60C).

Just remember you want the dust to come out the intake, if you try to force it out the outtake you will just embed it deeper.

Another trick is to raise the rear of the laptop about 1cm. The extra clearance and air-flow can win you a few degrees C.


EDIT: You should not need to leave it idle overnight, If you run something CPU intensive (mp3 encoding, code compiles etc.) it should start to heat up. You should see the temperature rise, the fan speed up, and the temperature come down a little but stay in its operating range.

---

### Post by Robert Leithe on 2007-05-22
It would apperar that my trusty old Dell is back on it's' feet :)
Case closed, thanks for your feedback!

Sincerely

---

### Post by faceoftheearth on 2007-05-22
I'm having the same issue with a Dell 9300, Pentium M 760 with a GeForce 6800 graphics card. The strange thing is that it will happen after only a short time of the CPU being pegged at 100%. In Windows XP and Vista the fan speeds are greater and the temperature doesn't get up that high.

---

### Post by michaeljb2005 on 2007-05-24
I too am having the same issue with a Dell 9300, Pentium M 760 with a GeForce 6800 graphics card.  Exact same problem as you faceoftheearth where the CPU gets up to 100% and eventually overheats.  I had to downgrade back to edgy because of it.

Anybody know of a solution to this problem?

---

### Post by Niomi on 2007-05-25
I also posted about this problem here: [http://ubuntuforums.org/showthread.php?t=438603](http://ubuntuforums.org/showthread.php?t=438603)

My husband's laptop (an inspiron 9300) has experienced the same problem since we upgraded to Fiesty. For us, it's NOT a hardware problem, as it hasn't been a problem in Edgy. We think it may be an overheating problem, the fan does not appear to run as loudly or frequently as it did in Edgy. Our guess is it has something to do with the mechanism that measures the CPU temperature and adjusts the fan accordingly. So I'm hoping someone on the ubuntuforums know some tweaks or settings I can adjust so that his fans work properly.

To fix this problem, I'm attempting to change the CPU polling frequency in ***/proc/acpi/thermal_zone/THRM/polling_frequency***. Polling is currently disabled. I'm having trouble with saving this file.

---

### Post by michaeljb2005 on 2007-05-25
> **Niomi said:**
> I also posted about this problem here: [http://ubuntuforums.org/showthread.php?t=438603](http://ubuntuforums.org/showthread.php?t=438603)

My husband's laptop (an inspiron 9300) has experienced the same problem since we upgraded to Fiesty. For us, it's NOT a hardware problem, as it hasn't been a problem in Edgy. We think it may be an overheating problem, the fan does not appear to run as loudly or frequently as it did in Edgy. Our guess is it has something to do with the mechanism that measures the CPU temperature and adjusts the fan accordingly. So I'm hoping someone on the ubuntuforums know some tweaks or settings I can adjust so that his fans work properly.

To fix this problem, I'm attempting to change the CPU polling frequency in ***/proc/acpi/thermal_zone/THRM/polling_frequency***. Polling is currently disabled. I'm having trouble with saving this file.

Will you update me on if this fixes the problem for you?  I also am aware now that part of the problem was using mail-notification on startup.  It has a bug where if it's not connected on startup it runs up the processor.  Since I disabled it the temperature stays within sane levels from the startup but it still gets higher much more quickly then it did in edgy.  I do think I agree with you about the fans.  They don't seem to be as aggressive as they were in edgy.  Hopefully your solution will work for this.

EDIT:  If changing the polling frequency doesn't work for you then automatic control of fans through a daemon called i8kmon might work.  I haven't tried it yet but you can set temperature ranges for the fans to run.  I'd still rather go with your solution though if you find it since it doesn't require installed and running another program.

---

### Post by Niomi on 2007-05-25
The polling frequency idea was from another laptop I used to own (an averatec) that expirienced a simular problem with Dapper last year. The polling frequency trick was implimented by a friend I'm no longer in contact with. The information I remembered wasn't enough for me to change the setting successfully, nor could I find any good information or help on doing so.

Since I've spent a day on this and all my attempts for fixes have turned out to be dead ends, I decided to back-up data and replace Fiesty with a fresh install of Edgy. I don't know how long it'll take me to find a fix for this issue, but a reformat will take an evening.

I'll be watching the forums and I'll upgrade to Fiesty when there seems to be a good fix for this issue. It's a shame -- I have Fiesty on my desktop and I think it's for the most part a large improvement over Edgy.

---

### Post by michaeljb2005 on 2007-05-26
> **Niomi said:**
> The polling frequency idea was from another laptop I used to own (an averatec) that expirienced a simular problem with Dapper last year. The polling frequency trick was implimented by a friend I'm no longer in contact with. The information I remembered wasn't enough for me to change the setting successfully, nor could I find any good information or help on doing so.

Since I've spent a day on this and all my attempts for fixes have turned out to be dead ends, I decided to back-up data and replace Fiesty with a fresh install of Edgy. I don't know how long it'll take me to find a fix for this issue, but a reformat will take an evening.

I'll be watching the forums and I'll upgrade to Fiesty when there seems to be a good fix for this issue. It's a shame -- I have Fiesty on my desktop and I think it's for the most part a large improvement over Edgy.

I agree with you.  I tried to make it work but for some reason the fans just can't seem to keep up with the heat.  I just downgraded back to edgy tonight.  Relieves a lot of stress since I don't have to worry about the cpu heat anymore.  Edgy has everything I need, I just wanted to have the latest and greatest.  If you find any solutions please pm me or post here.  Thanks.

---

### Post by Niomi on 2007-10-07
Does anyone know if this problem still present in Gutsy?

---

### Post by Niomi on 2007-12-04
Installed Gutsy on my husband's laptop, the Inspiron 9300-- the overheating problem is no longer present.
However, in Gusty there is a new error with this laptop where he cannot control the volume. With this latest bug, he's gotten frustrated with Ubuntu and has switched to XP for the time being.

---

