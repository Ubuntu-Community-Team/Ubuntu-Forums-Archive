---
title: "HP nc8430 battery life"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by DonPingu on 2006-09-09
Hi,

I have recently bought a HP nc8430 laptop (Core Duo 2ghz, X1600). I normally use Slackware but I figured I'd install something more laptop-friendly on it and went with Ubuntu (Dapper with KDE Kubuntu desktop actually). I'm using the fglrx driver.

I noticed that running linux I get considerably worse battery life than when running Windows. I also noticed that my cpu is never throttled below 1 Ghz. I don't know if this is the main cause, but if it is, can this be fixed? (/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq does state 1000000 (= 1ghz))

Any other possible reasons and solutions are welcome too of course.

Thanks!

---

### Post by daller on 2006-09-14
Hi There,

Is the maximum-speed 1GHz??? (It never scales?)

You should install **powernowd** or cpufreqd (I'd prefer powernowd)

...and if it's already installed, you should look into the KDE-tool:

Right-click the battery-monitor, and choose "Configure Klaptop"

Goto the ACPI-config tab, and run the "helper-app"

Then go to the second tab, called something like "Power management"

make sure that the systemperformance is set to "Userspace" (not performance!)

---

### Post by aks_! on 2006-09-30
I have noticed a similar problem with Ubuntu (GNOME Desktop). I don't know about battery life because I haven't tested it yet, but the notebook gets hotter while I'm working with Ubuntu than while I'm working with Windows. Is there anything that I can do?

Thanks.

---

### Post by Omnios on 2006-09-30
I remember reading an article that the batery life is much improved with edgy. So hopefully in a bit things will improve

---

### Post by aks_! on 2006-10-01
That would be great. I installed Edgy today and when I'll have time, I'll test the battery life. But CPU frequency, however, still doesn't fall under 1 GHz.

---

### Post by ottuzzi on 2006-10-27
Hi,

I own the exact same notebook.
You cannot get a frequency lower than a GHz...

> cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2000000 1667000 1333000 1000000

Here you can see your available frequencies for CPU0:
2.00GHz
1.66GHz
1.33GHz
1.00GHz

My problem is that under Kubuntu EDGY I get a little more than 90 mins of autonomy but in WinXP I can get over 3Hrs :( 

Bye
Piero

---

### Post by marcog on 2006-11-19
I also get a battery life of under two hours, whereas on Windows I can easily get over three, if not four. And it gets very hot on Ubuntu, but not on Windows. The fan is always idling away even when I'm not touching it.

Here's a list of the temperatures:

```
$ cat /proc/acpi/thermal_zone/TZ*/temperature 
temperature:             65 C
temperature:             53 C
temperature:             69 C
temperature:             32 C
temperature:             80 C
```

CPU frequency scaling is working correctly and the governor is set to ondemand and when idle it sticks to 1GHz, which is the minimum.

Some details:

Core 2 Duo 2.0GHz T7200
Edgy with fglrx drivers and Beryl/Xgl
Updated to latest bios

---

### Post by David Corrales on 2006-11-19
Some of the things I've found useful with my Inspiron 9300:
* Using the ATI drivers, there's a utility called **aticonfig**. It allows you to lower the refresh rate, which gives me about 30 more minutes. The interesting options are **--lsp** to see the available states and **--set-powerstate=#** to change the refresh level.
* Make sure laptop-mode is running. It extends battery by minimizing the amount of hard drive writes, therefore spinning the drive less.
* Make sure you turn off wi-fi if you're not using it. You can check it's state via a panel icon or typing **iwconfig** and reading radio:off.
* Dim your panel at least 2 levels from the max. The screen is the most draining component of them all.
* Ensure cpu frequency is working correctly. In my case, this happened to be the case out of the box.

Things left to do:
* Turn off the wired NIC (not just disable it) like windows does. Haven't investigated about this though.

---

### Post by marcog on 2006-11-19
I've either already done those or made the changes now that you mention them. I know it's quick to turn around and judge already, but it doesn't appear to be making a significant difference.

The main problem is that this laptop just runs so HOT. And things like the wifi and the screen are not going to produce much heat. Obviosuly the heat, the noise and the battery life are all strongly related. So I would imagine that the only way to really solve the short battery life is to solve the heat problem. Agree?

---

### Post by David Corrales on 2006-11-19
I use i8kmon to control my fans but that's only for a Dell computer =/
I had to use gkrellm with the i8kmon plugin to properly adjust my thresholds for fan speeds.

---

### Post by Jukka-Pekka on 2007-08-09
Hi!

My temps are as follows:
$ cat /proc/acpi/thermal_zone/TZ*/temperature
temperature:             65 C
temperature:             58 C
temperature:             71 C
temperature:             37 C
temperature:             80 C
With room temp at about 25 C

I also get a short battery life and there is a lot more heat than under windows. And, the fan is running...
Also, the cpu only seems to switch between c-states 0 and 4, nothing in between.

Running feisty 64-bit on HP nc8430 (C2D T7200 2Ghz cpu) laptop

Does anyone have a good link to ubuntu undervolting instructions?
Or a way to get the ATI Mobility x1600 to run cooler?

Best regards,
Jukka

---

### Post by Jukka-Pekka on 2007-08-19
There is possibly something wrong-or missing- in the voltage regulation in Ubuntu?
Not lowering CPU voltage (when there is little or no load on the CPU) might be one reason for the excessive heat generation that Ubuntu users have noticed on laptops.

Excessive heat means more fan noise and a shorter battery life. So, I agree that reducing heat is key to lengthening battery life and lowering fan noise on laptops in Ubuntu. Lowering CPU voltages as part of e.g. "laptop-mode" is one solution of getting rid of the high temperatures that our laptops currently generate.

Is there a way of checking the voltages supplied to the cpu with the different workloads/GHz steppings? Or a way of controlling/adjusting these voltages?

I hope these issues will be addressed by someone knowledgeable...at least in the upcoming Gutsy (7.10) release.

Jukka

P.S. As laptops are the growth area in computer sales, getting Ubuntu to work on them should be one of the development priorities to gain "market share" - or not to lose it.

---

### Post by dj Kalma on 2007-08-19
Umm.. I'm really not sure what exactly happened, but my laptop just quieted down a notch. According to gkrellm, from the usual 70% to an unnervingly quiet 55%.. The heat seems also to have gone down a bit.

I thought I'd pull the AC plug and check if the power management alters anything and/or if the system even notices anything (BTW, it doesn't, it still thinks its on AC and all battery meters read 100% all the time).

So after pulling the plug I tried to set the machine to act accordingly, so I did the following:
```
$aticonfig --set-powerstate=1
$cpufreq-set -c 0 -g powersave
$cpufreq-set -c 1 -g powersave
```
So the display should be at its low voltage state and the CPU scaling should be set to 'powersave'. Currently both of my cores register as 1GHz.

So, while using the machine for browsing, watching Invader Zim with VLC and torrenting (is that a word?), the machine stays relatively cool & quiet. Which is nice.

Edit: Oh yeah, forgot to mention: I replugged the AC and set the display to default state with aticonfig, with no change. Still relatively cool & quiet.

Edit2: Oh snap, wrong thread. I was aiming at [this one]("http://ubuntuforums.org/showthread.php?t=525063"). Sorry.

---

### Post by Jukka-Pekka on 2007-08-19
> **dj Kalma said:**
> Umm.. I'm really not sure what exactly happened, but my laptop just quieted down a notch. According to gkrellm, from the usual 70% to an unnervingly quiet 55%.. The heat seems also to have gone down a bit.

Edit: Oh yeah, forgot to mention: I replugged the AC and set the display to default state with aticonfig, with no change. Still relatively cool & quiet.

I tried the same, and guess what... it does help in some situations, which I have not been identify yet! The aticonfig --set-powerstate=1 -command surely reduces heat but also reduces graphics performance dramatically. But often times that's o.k.

Unfortunately the search for the solution continues...:confused:

---

