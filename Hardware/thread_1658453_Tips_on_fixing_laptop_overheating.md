---
title: "Tips on fixing laptop overheating?"
date: 2011-01-02
forum: Hardware
---

### Post by Rave Gloves on 2011-01-02
I have a samsung R610, it used to run without getting to warm but now it seems after 15mins of use my fan is just spewing out burning hot air. My system monitor tells me it's at 80°C.

i was considering dismantling and adding a new fan. Although ive also heard it could be the graphics chip that is getting so hot, ive got no idea what i would do about that.

Has anyone tried this on a laptop? what do you recommend ?

---

### Post by IcarusR on 2011-01-02
If it used to run cool & now gets hot I suspect dust is clogging the air vents inside it.
Get an air duster aerosol & with it switched off blow air in through the air vent. This should clear any dust out.

> i was considering dismantling and adding a new fan

I seriously doubt there will be any space to do this.

You could get a cooling pad like [_*this*_]("http://www.belkin.com/IWCatProductPage.process?Product_Id=472610"), the downside is they use USB power so decrease battery life.

---

### Post by PsxMeUP on 2011-01-02
The fan cleaning suggestion always gets on my nerves. Do you think somebody who messes around with Linux hasn't thought of checking the fan as a first recourse?

Anyway... I have an HP nx9420, Intel Centrino Duo T2500 2GHz, Radeon Mobility x1600. It overheats with all Ubuntus. Doesn't do it with Win XP/7. It's not dust. Opened the laptop and it's clean as a whistle (as it should; I vacuum it once a week). I used to think it was the video card but it's a CPU issue because the CPU area of the laptop (middle) gets super hot, not the left side (vid card) - logical since my ATI drivers are emulated by the CPU. I tried doing all sorts of tweaks, as stated by the countless forums/sites online, to no avail. I guess that's just a reality of Linux and my model. I only use Ubuntu in extreme cases when Win messes up and I don't have the time to restore my Win image. Unfortunately it's the one thing that's keeping me from completely switching to Linux.

For anybody out there that might be in the same boat as me, I did the following as suggested by others (hope it works for you):

**Added the following to /etc/modules file**
powernowd
cpufreq_ondemand
cpufreq_powersave
cpufreq_performance
cpufreq_conservative
cpufreq-userspace
battery
ac
processor
thermal
acpi-cpufreq

**In terminal**
sudo apt-get install cpufrequtils
cpufreq-info
sudo cpufreq-set -d 1000000
sudo cpufreq-set -u 1000000

**Added CPU temp monitoring screenlet by first installing**
sudo apt-get install lm-sensors
sudo sensors-detect
install whatever CPU temp monitoring screenlet catches your fancy

None of it helped. The screenlets don't seem to show the right info because the laptop is never THAT hot while in Win, even though the idle temp displayed in Linux is similar to Windows. My guess is the graphics card emulation doesn't include "Save Battery Life" mode, since that's the key ingredient in windows that cools the laptop down.

---

### Post by fluorescentblack on 2011-01-03
I would suggest to check your software and hardware 

[LIST=1]
[*]Software - OS and any other running programs - just in case you have an app that eats up CPU.
[*]Hardware -
[/LIST]
[INDENT]
[LIST]
[*]cooling fins  - are they still clean? i just removed a "carpet" from my 1.5 year old dell e5400. only 1/3 of the hole was still open.
[*]cooling fan - dust that accumulate in the blades make the fan less efficient.
[/LIST]
[/INDENT]A laptop cooler is only effective to a certain degree. it does cool the surface and a little of the parts inside. this is what i have. [http://www.coolermaster.com/product.php?product_id=6612](http://www.coolermaster.com/product.php?product_id=6612). 

Adding an additional fan isnt practical or elegant. 

Should you want to purse a DIY cleaning, i would suggest you research on the steps on how to tear you system apart. you may also need to look into the tools you'll need. i did mine using a screwdriver set, thermal paste, toothbrush, soap and water (last 3 items is for the heatsink when its removed. just to make sure there's no oil or grease). 

Some blogs warn about Vacuum Cleaners. they say that it may create too much static electricity that may damage electronic parts. 

pressurized air may help if there's only a bit of dust around. however, i think it wouldnt help much if youre trying to clean "carpetting".

---

### Post by ekjsim on 2011-01-03
Laptop overheating is almost always due to the fan clogged up with dust. On the contary, I believe running Ubuntu would actually lower the overall temperature of the machine as it uses up less resources. Less CPU processing, less energy lost.

I suggest that you clean up up your vents with something that blows pressurised air into your computer air-vents.

EDIT: Oh yeah, the vacuum cleaner works on mine. Just make sure the fan don't fall off from all the vacuuming!

---

### Post by alexwang32 on 2011-01-03
Well, it's probably due to your cpu. My notebook is using Intel Pentium M, and everything is fine. I used to use another one... which name escapes me, anyway, my computer used to be so hot in a few minutes, so the fan is always on.

---

### Post by aytech on 2011-01-03
If you had no problems before, its likely the cooling problem. I had this on my old Dell laptop, when I run some CPU-intensive task, its (CPU) temperature reached 90ºC ! 
 
I dismantled the ntb, cleared the dust off the fan, reapplied thermal paste on CPU (the old one was completely dried!), the temperature dropped 20 degrees under the same load.

---

### Post by IcarusR on 2011-01-03
PsxMeUP

> The fan cleaning suggestion always gets on my nerves. Do you think somebody who messes around with Linux hasn't thought of checking the fan as a first recourse?

Doesn't matter if it gets on your nerves ! OP asked for ideas & if you search forum you will find that this solution has been suggested to people who had not thought of this & it resolved their issue !!

---

### Post by cascade9 on 2011-01-03
> **IcarusR said:**
> I seriously doubt there will be any space to do this.

You could get a cooling pad like [_*this*_]("http://www.belkin.com/IWCatProductPage.process?Product_Id=472610"), the downside is they use USB power so decrease battery life.

+1 on 'no space for a new fan' 

There are passive laptop coolers as well, eg- 

[http://www.indiamart.com/industrialresearch/koolex-cooler-pad.html](http://www.indiamart.com/industrialresearch/koolex-cooler-pad.html)

I've run a n overheating laptop on some huge x-telco heatsinks as well. 

> **PsxMeUP said:**
> The fan cleaning suggestion always gets on my nerves. Do you think somebody who messes around with Linux hasn't thought of checking the fan as a first recourse?

So, just because you know that you can clean out the fans/grills means that somebody shouldnt sugest it? I dont think so.

---

### Post by IcarusR on 2011-01-03
cascade9

> So, just because you know that you can clean out the fans/grills means that somebody shouldnt sugest it? I dont think so.

Thank you !

---

### Post by bludgard on 2011-01-03
:lolflag:


Have you opened System Monitor and checked Processes tab to nail down what is eating your CPU?

There is also Hardware Sensors Monitor in the repository.To monitor temperature on all supported hardware (with sensors).

CPU Frequency Scaling Monitor is a nice tool as well.You can choose to cap the CPU clockspeed (limited)
among other options.

I use a cooling pad but am rarely mobile with my laptop.It is USB powered however I power it by a Universal AC/DC adaptor.By changing the voltage output on the adaptor (ranging from 1.4V-12V) I change my fan speed.I obviously don't run it at 12V.It's pretty convenient and doesn't tap the lappy.Keeps it 5-15*C cooler depending on setting.

Make sure there are no issues with clogged or blocked vents.

One

---

### Post by Yellow Pasque on 2011-01-03
> The fan cleaning suggestion always gets on my nerves. Do you think somebody who messes around with Linux hasn't thought of checking the fan as a first recourse?
I suggest you grow some thicker skin and/or expect less ignorance from the masses. Reading (and responding to queries in) these forums is good practice for both.

---

