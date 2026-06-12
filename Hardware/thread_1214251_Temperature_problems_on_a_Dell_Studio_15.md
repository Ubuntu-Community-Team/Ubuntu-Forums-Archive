---
title: "Temperature problems on a Dell Studio 15"
date: 2009-07-15
forum: Hardware
---

### Post by neoncode on 2009-07-15
My Dell laptop has three temperature sensors in the ACPI. I presume these are on the motherboard as the CPU temperatures are listed separately. Of the three the first two (labelled TZ00 and TZ01) hover around 30 degrees C in both Kubuntu 9.04 64bit and Vista SP1 64bit. But the last one, labelled TZ02, is arround 50 degrees in Vista but is about 75 degrees in Linux!

In Vista I do have aero effects enabled, but in Linux I don't have any desktop effects turned on. Even after playing World of Warcraft for an hour in Vista the TZ02 temp doesn't go about 60.

I'm quite concerned about the temperature and what damage it could do to the laptop to run it that hot in the long term. I assume that it's the graphics chip set temperature, although I don't know that for sure.

Also in Vista the fan speed will adjust to what I'm doing. running quietly while on the desktop and only spinning up to a faster (and louder) speed when I do something intensive (such as playing World of Warcraft). But in Linux it's on full blast all the time, not matter what I'm doing.

Can anyone offer any advice?

---

### Post by neoncode on 2009-07-15
Can no-one help?

---

### Post by LepeKaname on 2009-07-15
Hi, I have no so much experience dealing with sensors, but I will try to help:

After reaching that temperature (75) in Linux, restart your system and enter to the BIOS settings (ASAP) and check the temperatures there. If those temperatures match the ones you are looking in Linux, then something is wrong. I'm not sure what the 3rd sensor you mentioned is for, but I guess it could be related to your integrated video chip. If the temperatures in your BIOS doesn't show that high temperature (maybe around 60), then its possible the lecture is wrong which I think you can just ignore it (unless you feel is really hot).

Try first that....

---

### Post by neoncode on 2009-07-19
My Dell doesn't appear to have temperature displays in the BIOS. But I have noticed previously if I run Linux for a few minutes and then switch quickly to Vista, then the TZ02 sensor in Vista is a good 60 degrees or so before dropping down to it's usual 50-ish.

However, I have solved it. By installing the binary ATi drivers from the website. The temperature cooled right down to a much less scary 52-ish degrees and the fan shut up too. (presumably because the temp wasn't as high.)

So I would assume that TZ02 is the graphics chip set and Linux's standard 'radeon' driver runs it far too hot. For reference to anyone with the same problem, I have a Radeon Mobility HD 4570 and I installed (using the 'automatic' option, not the repo version in 9.04) the Catylist Driver 9.6.

Thanks to everyone who read this thread and gave advice. =)

---

### Post by fredie007 on 2009-11-19
Wow, thanks a lot. I've spent all night figuring out why the fan would never stop. Been trying to get i8k working without any luck. Turns out an easy solution like this one ended my  misery. Luckily I came across this topic, because otherwise I would've never updated the Catalyst driver.

I guess they're right when they say that the easy solutions often turn out to be the best. 
This Ubuntu -and Linux for that matter- -noob just wanted to say thanks.

p.s. I don't hope it's allowed to bump a rather old thread, if so, my apologies.

---

### Post by Abadon125 on 2009-11-20
Yea, graphics drivers are very important.  They allow the card to run more efficiently.

What tool do you use to monitor the temperature settings?  Thanks

---

### Post by fredie007 on 2009-11-20
I'm not using anything to monitor or change those settings. With the Catalyst Driver installed, the fan acts the way it should. Prior to the driver installation, someway the GPU was running all the time (bad standard ATI-driver in Ubuntu, I suppose) and it caused a lot of heat.

---

### Post by Abadon125 on 2009-11-20
Sorry I phrased my questions wrong.  Are you using a specific program to see what the temperature of your computer is or are you just basing it on how hot the laptop makes your lap?

---

### Post by fredie007 on 2009-11-20
Both (:
There's a package called 'acpi' that returns some information about battery status and temperatures. Just install it and```
acpi -V
``` in a terminal will tell you those.

---

### Post by Abadon125 on 2009-11-20
Ah very nice, Thank you.  I also found a program called IM-Sensors that works pretty well.

Find it [Here]("http://www.bradtrupp.com/ubuntu-cpu-temperature.html")

---

### Post by Tung on 2010-11-28
I just want to say thank for the tip and confirm that it works like a charm ! 

You definitely need to install the proprietary driver from ATI/AMD instead of the default one. My dell studio 15 turn itself off while frequently recently due to overheating and replacing the driver solve the problem !

---

