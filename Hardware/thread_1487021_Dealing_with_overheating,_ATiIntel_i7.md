---
title: "Dealing with overheating, ATi/Intel i7"
date: 2010-05-18
forum: Hardware
---

### Post by Infil on 2010-05-18
I'm currently running 10.04 on a Clevo W760CU laptop. It has a Intel i7 Mobile CPU and a HD4570 Mobility video card. 

I've had issues with overheating and still do but to a lesser extent. Currently I am using the xorg-edgers PPA and using kernel 2.6.34-rc7. I am booting with the parameter "radeon.dynpm=1" which seems to help somewhat. I read that the 2.6.33 kernels and newer have support for the Intel i7 CPUs, which this laptop has. 

I have a power save button which slows down the fan and supposedly clocks down something (I don't know what, the manual doesn't say). When I don't use this feature my temperature sensors read about 57 degrees C, but it rapidly gets much worse if the power save function is enabled. What is very strange is that if I leave my laptop be for some hours (power save disabled) the fan may run at lower than maximum, but as soon as I sit down and start using it, the fan speeds up again immediately, long before any temperature changes.

Is there some other parameters I need to use to enabled additional features, perhaps related to the CPU speed? Any other suggestions?

Thanks!

---

### Post by jaxxed on 2010-05-31
I have the same issue with my Dell studio xps notebook.  The machine runs really hot and periodically freezes (when running hot.  My temperatures are running higher than yours (up to 70C I think on the CPU, the other zone is in the 30s)

Are you using the mainline kernel?

The hardware is:
proc: CPU0: Intel(R) Core(TM) i7 CPU       Q 820  @ 1.73GHz stepping 05
graphics: (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 4670" (ChipID = 0x9488)


The software is: 
kubuntu lucid with most repositories enabled and the xorg-edgers enabled.
kernel: 2.6.32-22-generic
radeon driver: xserver-xorg-video-radeon 1.6.13.0-1ubuntu5 (amd64) (should I be using the hd?)
kde: 4.4-4.4.80

---

### Post by Berniebln on 2010-06-01
Hey,

had the same issue on 9.10, but it was resolved in 10.4.

The reason was that every time the computer started, the CPU was on PERFORMANCE mode. Now, if I start the computer, the CPU is in ONDEMAND mode.

Which mode is your cpu in after you start the computer? You can check using the cpufreq-applet that you can easily add to the gnome panel.

Bernhard

---

### Post by Infil on 2010-06-15
Most often it reads 1.20 GHz whether I'm using the power safe feature or not but it jumps up sometimes. The CPU is 1.73 Ghz. I have upgraded recently to kernel 2.6.34 but I haven't noticed anything different. I think it's still wierd that the fan often speeds up as soon as I return to the computer.

In any case the PC is hotter and the fan runs more often than in Windows. 

Regarding ATi, I added "options radeon modeset=1 dynpm=1" to /etc/modprobe.d/radeon-kms.conf. I don't how this is different from adding something til the kernel line i Grub, but I get the feeling that "modeset=1" helped somewhat.

---

### Post by DeBing on 2010-08-16
Hey,

wanna ask what the newest status is. Got a Studio 15 with i7 since January and its equal if i use windows 7 (64-bit) or ubuntu 9.10 (with newest kernel updates) it often overheats even though i only use a browser like firefox (without activ using of flash!). I solved the problem under windows with scaling the max-performance of the cpu to 70% but under Ubuntu i got no option to scale the cpu. The CPU Control Panel doesn't make any difference! Anyone can help?

---

### Post by samcoinc on 2010-09-01
Same problem here (lucid 64) On a dell xps 1645 i7.  No lockups but the computer runs quite a bit hotter than windows 7.  The battery charge lasts for about half the time also.  any tweeks?

sam

---

### Post by soulspit on 2010-09-23
Bump.  I'm having similar issues - I have a Dell Studio 1747 with i7 and ATI Radeon HD 4650.  It runs great in Windows 7 - cool, and the fan doesn't come on often - but in Lucid 64-bit it runs pretty hot with the fan on a lot, and battery lasts half as long.  I'm considering trying out the proprietary ATI drivers.  I don't usually see my CPU load going very high so I'm not sure if scaling that would help - perhaps the ability to scale the GPU would help?

If anyone has had any success in getting Ubuntu running better/cooler on a laptop with an i7 CPU or ATI GPU, please let us know!

---

### Post by mpnordland on 2010-10-01
@soulspit I have same laptop, I use a cooling pad, which is basically a fan that sits underneath the computer.
and, it doesn't bother that subwoofer under there, either, which when pumping tunes, it sounds awesome! By the way, I checked out that cpu-freq applet, THANKS now I can clock up my processor when I want it to go fast!

---

### Post by francisheyrman on 2011-01-04
I have a Dell studio XPS core 7i Q820. In Windows 7 it becomes really hot and I see the frequency going up from 1.73 upwards depending on the load. But in Ubuntu 10.10 the frequency starts at 1.2 and goes up only to 1.73. That's why it's less hot in Ubuntu, but I don't have the maximum performance. 
Is there a way to have it run at higher frequencies

---

### Post by PsxMeUP on 2011-01-06
(bump)

I have an HP nx9420 with Centrino Intel Core Duo T2500 with Radeon Mobility x1600 vid card. I opened and checked the fans, vents, etc. - all clean. Having the same overheating problem with every Ubuntu version. Even tried older versions when you could still use proprietary ATI drivers. Nothing helps (with propriety ATI drivers adding the extra bonus of random crashes). In Win 7 the computer cools down to a point where the fan doesn't need to run when I switch to Power Saver > Advanced > Max Battery Life mode. Laptop runs at a warm 54%c, which is great - better than running XP. 

In Ubuntu, things get wonky. Overheating is rampant. A clean install of 10.10 Gnome (without modifications) would give me scary results, with the CPU reaching shutdown temperature levels without shutting down! I would realize things are bad when I would touch the CPU area and it would be super hot. Upon reboot the computer wouldn't want to start until things cool down.

I have since then taken various measures to fix the problem, to no avail. I have lm_sensors setup and detected, cpudyn installed and cpufreq set to powersave at all times. I also have the following pasted in my /etc/modules file:

cpudyn
cpufreq_powersave
battery
ac
processor
thermal
acpi-cpufreq

Sensors show cores 0-1 as low as 57%c when idle, but to the touch it's clear that info is wrong. The Laptop's CPU area is burning hot, and the fan doesn't always kick in to cool things down because the temp indicated is low. That totally scares me. I still get the reboot problem where the computer doesn't want to start from time to time due to overheating. The screen stays black and keeps rebooting for a few minutes, I guess until the chip is out of overheating danger. Scary stuff... 

As you can see with my old laptop, the overheating CPU problem is ongoing. It's been around for years and it hasn't been fixed. What's even scarier is Canonical is plunging deeper into the Netbook/Laptop realm with the upcoming Unity interface, when it's clear many mobile hardware issues aren't resolved yet. I know better to shutdown my laptop before the cores melt, but others might not. I wouldn't like to see lawsuits filed against a non-profit organization but laptop heating issues are rampant; it might be a matter of time.

---

### Post by WinRiddance on 2011-01-09
My wife and I have identical HP 6735s laptops with integrated horrible ATI HD3200 chips. These chips truly are terrible. Both of us are using the recommended proprietary drivers. _Weird thing is that my wife's system runs as you'd expect it to_ with Ubuntu 10.04 whereas mine overheats constantly. I'm using 10.04 as well and both of us keep our systems updated. The fan never seems to drop below at least 65% usage on my system though. It gets especially bad if I view any websites with flash video, stuff like embedded YouTube videos on sites.

Sometimes during extreme application usage such as backup restorations of multi-gigabyte files the system will just shut down i.e. become totally inoperable to the point where only a hard reset remedies the situation. My cpu fan is always hot ... **always** ... even when there's nothing going on.

Today I did some checking, to see what actual differences there were between the two machines since my wife's HP 6735s seems to run so much more normal even though she spends hours every day on her machine as well. Checked out all sorts of stuff but the only real difference that I could find is the fact that I had _CUSTOM EFFECTS_ enabled and my **wife didn't**.

However, the only thing that I had enabled in the animations of the custom effects was the ring switcher and fade for closing apps., nothing else. Our powersave settings are the same too, so that can't have anything to do with the overheating either. I'll report back later on if I find out anything else that might help.

---

### Post by 3602 on 2011-01-09
I think that in some models, there is a BIOS option of Fan Always On. My current HP dv7 has that BIOS option. I played around with it, and if it's disabled (fan NOT always on) then sensors can report 57°C. If it is enabled then it's 35. Big difference. Although I do have a small cooling fan (pad).

---

### Post by WinRiddance on 2011-01-11
Alright, here's what I did and what I've been able to find out. I already had the "fan always on" disabled but double-checked that in the bios anyway. Suspecting that perhaps flash applications or compiz might have something to do with this issue, I went ahead and kept the 3D settings on, but I disabled the special custom settings. I also removed that feature from the software center. This actually helped ... when I rebooted the system my fan/cpu behaved much better.

Then I changed my screensaver/power settings and **that helped big time**. It helped big time because this actually caused everything to power down (sleep) without turning anything else off. I'll be trying the feature for spinning down that hard disks next. The screenshot below shows the current settings that I'm using ... because I use my laptop as a desktop PC with attached display, mouse, keyboard, and surround sound system.

[COLOR=DarkRed]**UPDATE**[/COLOR] - Now I'm using the option to spin down the hard disks when asleep and that seems to work fine too. I've changed the two hour duration down to only 30 minutes as it dawned on me that I'm usually not away from the computer more than 10 or 15 minutes at a time ... unless I'm not doing anything for at least a couple of hours during which I'd want to use the power save settings anyway.

.

---

### Post by WinRiddance on 2011-01-13
Well, even though the laptop is running better now, I'm still getting system crashes anytime I make heavy duty use of the computer. I can't even do a home folder backup completely without the screen going blank (crash) before the backup reaches the 50% mark. Tried it after rebooting clean too, while using NOTHING ELSE, just the default backup software that came with 10.04 ... no other apps.

Took a look at the ATI proprietary drivers from the AMD/ATI website, but after reading there, those are the same drivers as what's in the Ubuntu installation after doing the hardware drivers check. The **HD 3200 chip is just pure garbage** as far as I'm concerned ... it's worthless for video websites, 3D action games, and anything else that requires heavy processor use ... even though my system is a dual-core with 4 GB ram. Ridiculous!

Next week I'll rebuild my system from scratch with Ubuntu 10.10 ... maybe I'll get lucky and the system will be more stable.

---

