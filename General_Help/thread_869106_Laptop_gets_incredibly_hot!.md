---
title: "Laptop gets incredibly hot!"
date: 2008-07-24
forum: General Help
---

### Post by Archimedes0212 on 2008-07-24
Hey all -

When I have my laptop on (running Hardy - happened with older versions as well) for several hours, my laptop gets incredibly hot almost as if the fan isn't working properly.  However, when I load windows (I dual boot) and leave it on for any length of time, it gets hot but nowhere's near as hot as when I'm in linux.

How can I go about fixing this??

Thanks in advance.

Oh yeah, I have an IBM Thinkpad T60 laptop

---

### Post by rossjman1 on 2008-07-24
I have the same problem - it's leading to random shutdowns. Last night my computer shut down, and I turned it back on to check the temps:
THM0: 73 C
THM1: 71 C
I also have a T60

---

### Post by loboc on 2008-07-24
The cpu stepping controls might be defaulting to high performance there a gnome-panel applet that lets you manualy contol the stepping state.  use synaptic with a search cpufreq to look at the various daemons to control cpu frequency and power settings, the gnome panel applet should be installed by default as part of the gnome panel applets package

---

### Post by Orlsend on 2008-07-24
I used to have the same Problem, I toke my laptop to the nearest toshiba center and they opened it up and showed me that the dust was causing it (They gave it a free clean up) They told me if it happens again, Just to get a empty dry waterbottle and to turn my laptop side ways and and just squeeze on the bottle to let blows of air clean my computer...(all this with the power off) It works wonders!

---

### Post by rossjman1 on 2008-07-24
> **Orlsend said:**
> I used to have the same Problem, I toke my laptop to the nearest toshiba center and they opened it up and showed me that the dust was causing it (They gave it a free clean up) They told me if it happens again, Just to get a empty dry waterbottle and to turn my laptop side ways and and just squeeze on the bottle to let blows of air clean my computer...(all this with the power off) It works wonders!
It's a problem with Ubuntu since I used to have Windows on this laptop not even a month ago and had no problems for years (although I know where you're coming from as Toshiba laptops have major problems with overheating). As for the cpu freq thing, I searched synaptic and installed cpufrequtils, but it is a command line utility. Does anyone know of a gui program that is simple and intuitive?

---

### Post by Archimedes0212 on 2008-07-24
yeah, it's definitely a problem with ubuntu, because this doesnt happen when I'm in Windows.  I'll have to give that command line utility a shot when I get home.  

thanks for the speedy responses everyone

---

### Post by rossjman1 on 2008-07-24
This is ridiculous. My temp was around 49 C, then I played Enemy Territory for **15 minutes**. When I got back to the desktop my temp was 80 C! From 15 minutes of playing a game (not even a demanding one at that)! WTF
Here is some info.
```

jeff@jeff-laptop:~$ acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 53.0 degrees C
     Thermal 2: ok, 55.0 degrees C
  AC Adapter 1: on-line
jeff@jeff-laptop:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1000 MHz and 1.83 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1000 MHz and 1.83 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

```
[IMG]http://jeffantosh.googlepages.com/temps.png[/IMG]

---

### Post by rossjman1 on 2008-07-24
bump

---

### Post by Cool Javelin on 2008-07-24
My wife has a Gateway laptop running XP. About 2 months ago, it too started getting very hot. To the point of failure.

I removed the cover over the fan, and while there was some dust in the fan, I didn't think it would be a problem. I blew it out anyway, and it is now a LOT cooler, (I guess those holes in the fan are pretty small)  but I think it is still hotter then it should be and the battery life seems to have decreased too.

I wondered about CPU voltage changing (maybe the mother board was told to use a higher voltage.) and emailed Gateway, but they said, "Pay us money, and we will look into your problem."

I want to look more into LOBOC's response about stepping.

I wasn't aware of this. Is it a way to change the performance when idle? (slow the CPU clock?) It makes sense.

Does anybody know where I might look in XP SP2 (I know this is a Linux forum, but you are the only hope I have left.:-({|= )

Mark.

---

### Post by loboc on 2008-07-25
> **Cool Javelin said:**
> My wife has a Gateway laptop running XP. About 2 months ago, it too started getting very hot. To the point of failure.

I removed the cover over the fan, and while there was some dust in the fan, I didn't think it would be a problem. I blew it out anyway, and it is now a LOT cooler, (I guess those holes in the fan are pretty small)  but I think it is still hotter then it should be and the battery life seems to have decreased too.

I wondered about CPU voltage changing (maybe the mother board was told to use a higher voltage.) and emailed Gateway, but they said, "Pay us money, and we will look into your problem."

I want to look more into LOBOC's response about stepping.

I wasn't aware of this. Is it a way to change the performance when idle? (slow the CPU clock?) It makes sense.

Does anybody know where I might look in XP SP2 (I know this is a Linux forum, but you are the only hope I have left.:-({|= )

Mark.
 
Theres a utility for XP called speedswitchxp thats free I use that for my laptop.  In UBUNTU if you right-click on the panel and select add to panel one of the default applets is the cpu frequency and scaling monitor 
both  let adjust the frequency settings with a context menu.  

FOR XP

[http://www.diefer.de/speedswitchxp/](http://www.diefer.de/speedswitchxp/)

DETAILS ON the APPLET

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by Uchiha_madara on 2008-07-25
My Laptop too you can make a fried Chicken on it, 

Listen i have this Problem and this is My Experience:

Put your Laptop on Wooden Surface not on Carpet
or on your Legs or on Cloth Surface , or any Surface keep the heat

Because the Wood Reflex the air to your laptop and reduces the heat,
if you put it on your Legs or on the carpet the heat spread surround the Laptop,so the heat still in the Laptop.

   Put on your mind the effort that your Laptop make it while Ubuntu is Working, so this is anther reason .....I solve it By Reducing the heat

So you need to Less that heat .....

This is My Experience in My Laptop When it's become hot ...  

Sincerely
madara:guitar:

---

### Post by rossjman1 on 2008-07-25
For those of us with a Lenovo Thinkpad T60, I found this article:
[http://www.kraus.tk/installnotes/T60/ThinkPad-T60.htm](http://www.kraus.tk/installnotes/T60/ThinkPad-T60.htm)
Here's the important part:
> 
One of the major problems of the T60 is a thermal issue. The procesor is quit cool (about 50 degree celsius) and also battery (about 50 degree C) and harddisk (about 40 degree C) are absolutely fine. BUT the powerful graphiccard is a problem. In idle-mode it gets quit hot, round about 75 degree C. Playing some minutes doom3 or UT2004 brings it up to 86-87 degree. Thats still no problem for that card, it get trouble when it get hotter than 110 degrees. BUT your fan of the T60 has to cool the card all the time. also in idle mode. So it's always running. It is not too loud, but good hearable. And always running parts of a computer  are fragile....

I got some mails from users that with ibm-acpi you can control the fan. That is correct. And with a current version and forcing module-load with experimental=1 you can switch on/off the fan (no more detailed control is possible right now). BUT I do not recommend to switch the fan off, becaus your graphiccard simply needs it, ALL the time ! You risk your hardware when switching it of. Keep that in your mind.

This does explain my screenshot in one of my previous posts, as my cpu, battery, and hard drive all are somewhat cool. My graphics card is the problem as it can easily reach 80 - 90 C. Infact after a cold boot my cpu temp is around 40, while my graphics card (ATI Mobility Radeon X1400) is already around 70 C!

---

### Post by VMC on 2008-07-25
This is a problem with Linux for some reason. I found an article regarding ACPI for Gentoo that might help to explain some things. It's not hard to follow and do some of the simple compile steps. My desktop has BIOS temp control but even so I found out that I have a DSDT error. I found the exact area of problem but can't go any further. Type this from a Terminal to see if you have DSDT issues:

```
 dmesg|grep DSDT
```

The Gentoo article explaining this is found here:
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

---

### Post by rossjman1 on 2008-07-25
```
jeff@jeff-laptop:~$  dmesg|grep DSDT
[    0.000000] ACPI: DSDT 3FED66E7, C690 (r1 LENOVO TP-79        1040 MSFT  100000E)
[   19.097182] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

``` What does that mean?

---

### Post by VMC on 2008-07-25
> **rossjman1 said:**
> ```
jeff@jeff-laptop:~$  dmesg|grep DSDT
[    0.000000] ACPI: DSDT 3FED66E7, C690 (r1 LENOVO TP-79        1040 MSFT  100000E)
[   19.097182] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

``` What does that mean?

Regarding the DSDT.aml not found. Read this. Not for the faint of heart:
[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

Edit: here is a ubuntu form post on this subject. A bit old but there's several references on this subject: [http://ubuntuforums.org/showthread.php?t=233684](http://ubuntuforums.org/showthread.php?t=233684)

---

### Post by rossjman1 on 2008-07-26
So that last comment in the tread:
> ok i'm going to lay this out correctly.

the kenrnel is configured to look for the file "./DSDT.aml" if one is not found then instead of reading the file the kernel will read the acpi table from your machine.

a while ago almost everything had a severly broken ACPI and to get any decient support you had to compile a DSDT.aml file yourslef. Which included fixing the asm errors. So by not reading that file your kernel reads the DSDT from the computer, If your computer has good support then don't worry about it. It is not an error!!!

if you have no acpi support, and have knowlede that it is because your machine has a broken acpi table, and want to make your own DSDT.aml file then that is beyond this post.

but even if you do have no acpi support look elesewhere first, recompiling this file should be a last resort. (as it is not even close to simple, and requires some ASM knowledege)
Almost everything that people seem to be complaining about in that thread seems to be working on my computer. So, it's not a problem?

---

