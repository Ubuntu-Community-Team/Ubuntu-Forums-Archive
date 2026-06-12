---
title: "computer temperature + cpu frequency"
date: 2008-11-27
forum: General Help
---

### Post by Th3Professor on 2008-11-27
Hello world.

I installed:
"Computer Temperature Monitor 0.9.6.1"
and
"CPU Frequency Scaling Monitor 2.24.1"

...neither are working.

Any ideas on how to get them (or alternatives) to work?

I'd like to be able to monitor my computer's temperature, including CPU temperature, and I'd like to be able to monitor my CPU frequencies.

Even better, I'd like to be able to control the fan speeds and adjust the clock on the CPU.

Thank you.

:)

---

### Post by prshah on 2008-11-27
> **Th3Professor said:**
> 
"Computer Temperature Monitor 0.9.6.1"
"CPU Frequency Scaling Monitor 2.24.1"
...neither are working.


Both are applets; did you add them to the gnome panel? Right click an empty area in the taskbar, and select the relevant applets, and Add them.

---

### Post by Th3Professor on 2008-11-27
> **prshah said:**
> Both are applets; did you add them to the gnome panel?

Yep.

---

### Post by cariboo on 2008-11-27
If you install lm-sensors and sensors-applet you should be able to monitor the various temp sensors of your motherbaord.

Lm-sensors and sensors-applet are in the repositories and you can use Sysnaptic Package Manager or the command line to install them.

You will have to set up lm-sensors once you have installed the packages. In a Applications-->Accessories-->Terminal type:

```
sudo sensors-detect
```

and answer yes o all the questions. Once the sensors have been detected, you will have to reboot in order to installed the needed modules. Once you are back at the desktop righnt click on the upper panel and select Add to Panel then scroll down and select Hardware Sensor Monitor, then click the add button. Right click on the sensors to set your preferences.

See attached screenshot.

Jim

---

### Post by frankleeee on 2008-11-27
I have been using GkrellM, I am not sure it does everything your looking for though. This just reads the sensors so you have to install first, but you can set fan speeds and temps among other things.

---

### Post by Th3Professor on 2008-11-27
> **cariboo907 said:**
> If you install lm-sensors and sensors-applet you should be able to monitor the various temp sensors of your motherbaord.

Lm-sensors and sensors-applet are in the repositories and you can use Sysnaptic Package Manager or the command line to install them.

You will have to set up lm-sensors once you have installed the packages. In a Applications-->Accessories-->Terminal type:

```
sudo sensors-detect
```and answer yes o all the questions. Once the sensors have been detected, you will have to reboot in order to installed the needed modules. Once you are back at the desktop righnt click on the upper panel and select Add to Panel then scroll down and select Hardware Sensor Monitor, then click the add button. Right click on the sensors to set your preferences.

See attached screenshot.

Jim



Does that work with quad core?

---

### Post by Th3Professor on 2008-11-28
**_CPU frequency monitoring:_**

GKrellM appears to be showing CPU0,1,2,3 usage. It shows readings like 9%, 12%, 10%, 5%. The %s are updating.

However, the "CPU Frequency Scaling Monitor 2.24.1" applet is not functioning.
:confused:

How do I get that applet to work?

I'd rather use an applet than gkrellm, unless torsmo works without any hitches, or an application similar to torsmo (or if gkrellm is capable of displaying info like torsmo).

Is there a way to monitor GPU frequency?

_** CPU (and GPU) temperature monitoring:**_

Almost none of the applets are working with the temperatures. They are not showing correct temperatures. I booted into Vista and compared numbers, which presented much more realistic ranges.

The GPU temperature monitoring in applets and gkrellm appear to be working fine, displaying core temp around 50C and ambient around 47C. However, that temperature never changes, so I don't know if it truly is working.

None of the CPU temperature monitoring in the applets are working.

The "Computer Temperatues Monitor 0.9.6.1" applet reads all 4 CPU cores as 40C with no changes.

The "sensors-applet 2.2.1" applet also displays no changes in temperatures. The displays include "CPU" (always 40C), "temp1" (always 40C), another "temp1" (always 52C), "temp2" (always 39C), and "temp3" (always **84C**). That cannot be right, I am positive of it. It *better not be* for that 84 number! <scary!>

How do I get either of those 2 applets to correctly read/update CPU temperatures?

**_ Monitoring fan speeds:_**

I have 3 case fans connected to one source on the mobo;
another 3 case fans are connected to another source on the mobo;
the CPU fan is connected to another source on the mobo;

...and I'm assuming the PSU and GPU fans are separate from the rest (at least, I'm presently unable to monitor/control them in *nix).

I see 3 sources of fans in the monitors (applets and gkrellm), which I'm guessing are for the 3 combined sources of fans.

I don't know which display refers to which set of fans.

I see an average 4200RPM, which I'm guessing is CPU fan;
an average 980RPM, which is one set of 3-fans (I don't know which);
and an average 1030RPM, which is another set of 3-fans (I don't know which).

I see 2 extra fan displays in the monitors, each showing 0RPM.

Is there a way to monitor PSU fan and GPU fan?

**_ Hard drive & RAM monitoring:_**

I see that gkrellm can monitor activity on the hard drives, though is there an applet that does this?

Likewise with RAM and swap, is there an applet that monitors these?

**_ Manually adjusting frequencies/clocks and fan speeds:_**

How do I control (manually) fan speeds?

How do I overclock CPU and GPU via *nix?

(Both are capable of overclocking, the CPU is unlocked and enabled via BIOS, the GPU is unlocked too, and both can be altered via Vista but I don't know how within *nix.)

Here's a screenshot of the applets, it's just testing them all out (I won't be using all of them once I get something working).

---

### Post by TMachado on 2008-12-16
Frequency Scaling monitor does not work properly for me too. Whether I have my laptop running battery or no, my applet is always "On Demand".

I'me always putting it in "performance" all the time, its very annoying. There's any solution?

---

### Post by prshah on 2008-12-17
> **TMachado said:**
> Frequency Scaling monitor does not work properly for me too. Whether I have my laptop running battery or no, my applet is always "On Demand".

I'me always putting it in "performance" all the time, its very annoying. 

Frequency scaling only works with OnDemand; depending on processor usage requirement, onDemand either slows the processor down or speeds it to maximum. When the processor is slowed down, it uses less power, and also generates less heat.

If you put it on performance, the processor will always be clocked to the maximum, even when idle. This is not a recommended setting unless you have a specific reason for it.

Post back if you still want to set scaling to performance, permanently.

---

### Post by Arup on 2008-12-17
Frequency scaling applet as well as GkrellM works fine with my dual quad core here. I did the usual isntall lm-sensors and sudo sensors-detect, I also installed hddtemp and GkrellM shows hdd temp as well.

---

### Post by wangsacl on 2008-12-17
Have you tried this code?
```
sudo dpkg-reconfigure gnome-applets
```
Answer OK, and then Yes. You could click on the CPU Frequency Monitor, and set up the speed of your CPU.

---

