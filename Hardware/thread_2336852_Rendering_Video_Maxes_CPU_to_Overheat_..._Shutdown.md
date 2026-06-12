---
title: "Rendering Video Maxes CPU to Overheat ... Shutdown"
date: 2016-09-11
forum: Hardware
---

### Post by Rick St. George on 2016-09-11
Trying to render video with DeeVeeDee and runs up my 8 core CPU to overheat 80c Plus and shuts down.

Is this a throttling issue in BIOS? Settings are Default, No Turbo. Normally about 30-35c, and uder good load upto 60's c.

Any ideas? Also having trouble burning with Brasero (which DeeVeeDee uses to burn) with VERBATIM DVDs. This makes them worthless after partial burn. Have M-Disc LG DVD-RW.

HHHhhmmmm .. What Next?

---

### Post by mc4man on 2016-09-11
Sounds like hardware (cooling) issue. (or core scale down is too slow..

Anyway last year I was testing a system76 laptop, 1st. thing I did was some h.264 encoding & it crashed due to reaching critical temp. On some subsequent runs some cores were always flirting near critical before being scaled back  so there was no assurance any encoding would actually complete.
From there I tried setting the  max_perf_pct to 90%. That didn't affect encoding speed to any great extent & did kept the temps down enough to not threaten a critical shutdown.

I don't exactly remember how I did that, likely like this (Intel cpu, 4.x kernel
```
echo "90" | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

This setting is only good for current session, goes away after reboot. So maybe try it @ 90 or 85, ect.

(- the issue with the sys76 laptop was it was using a desktop cpu with insufficient cooling

---

### Post by Bucky Ball on 2016-09-11
What video card are you attempting to do this with?

The DVD and Brasero problem doesn't belong here as not related to your original support request and gets confusing when that's the case. Please edit out and post in another thread. Thanks.

---

### Post by howefield on 2016-09-12
Thread moved to the "*Hardware*" forum for a better fit.

---

### Post by Yellow Pasque on 2016-09-13
> **Rick St. George said:**
> Trying to render video with DeeVeeDee and runs up my 8 core CPU to overheat 80c Plus and shuts down

Most likely, your CPU cooler is simply inadequate for the job. You see it a lot more often with laptops, but it can happen on desktops too depending on the ventilation of the case.

Other possibilities:
- CPU fan plugged in wrong header
- Bad BIOS/EFI fan control (check for BIOS update)
- Inaccurate temp sensor
- Heat from GPU is not being exhausted and dumped into case

> Anyway last year I was testing a system76 laptop, 1st. thing I did was some h.264 encoding & it crashed due to reaching critical temp.

If you can't run your unmodified laptop at full load (under "normal" ambient temps), then it's defective by design. I would have been angry as heck and demanding a full refund.

---

### Post by mc4man on 2016-09-13
> **Temüjin said:**
> 



If you can't run your unmodified laptop at full load (under "normal" ambient temps), then it's defective by design. I would have been angry as heck and demanding a full refund.
It was packed up 30 min later. While it worked just fine at 90% due to the 4.2 GHz desktop cpu,  the heat coming thru the keyboard was ridiculous. I was quite surprised sys76 configured that laptop without apparently testing it in real life.

---

### Post by Rick St. George on 2016-09-18
> **Temüjin said:**
> Most likely, your CPU cooler is simply inadequate for the job. You see it a lot more often with laptops, but it can happen on desktops too depending on the ventilation of the case.

Other possibilities:
- CPU fan plugged in wrong header
- Bad BIOS/EFI fan control (check for BIOS update)
- Inaccurate temp sensor
- Heat from GPU is not being exhausted and dumped into case


It has run for over a year just fine. Built system myself and Fan control, plugin, etc. are correct. Settings are 100% speed.
Running Psensor to monitor, shows rapid cool down when it does drop. 
Have installed 3 Silenx 25 CFM fans. 1 front, 1 rear (lower section); 1 top rear and PSU exhausts in rear (top section) with 2 small fans in front Bay slot of 2 foot tall Big Tower Case. So Air is moving through at 25 cubic ft./minute. Also have a 80mm Silenx 32 CFM fan on CPU. However, Express Video slot is right below the CPU.  (see attached Pic)
Also;
> **Bucky Ball said:**
> What video card are you attempting to do this with?

ASUS GeForce GT 610, with 2GB DDR3, running dual monitors. It was silent version, but I added an old small thin CPU Fan.

I'm wondering if it is possible the silver oxide has deteriorted under the heatsink? 

Also notice, it runs a litle cooler with side cover off. That may be my clue? But don't they all ???

---

### Post by Yellow Pasque on 2016-09-18
So are you able to reproduce the overheating using anything other than devede? Tried cpuburn?

---

### Post by Rick St. George on 2016-09-20
> **Temüjin said:**
> So are you able to reproduce the overheating using anything other than devede? Tried cpuburn?

Prior to the Upgrade to v16.04 when a lot of software pkgs disappeared,  Blender; Brasero; DVD Styler; Kdenlive; Pitivi all would CRASH at the stage of rendering video. See [old thread here]("https://ubuntuforums.org/showthread.php?t=2283702").

I think it is related, that's why I mention it. So back to the problem, why is it climbing to overheat status and shutting down when attempting to Render Video? How can I throttle/limit the 8 core processor to like say 90% ???

---

### Post by Yellow Pasque on 2016-09-20
> **Rick St. George said:**
> So back to the problem, why is it climbing to overheat status and shutting down when attempting to Render Video?

Rendering video can be CPU intensive, especially if you're not getting help from the GPU. What model is the CPU?

> How can I throttle/limit the 8 core processor to like say 90% ???

Well, that's a band aid solution, but mc4man did give a suggestion for that earlier in the thread. There's also a program in repo called cpulimit that can limit problematic processes selectively.

---

### Post by QIII on 2016-09-20
Hello!

Did I miss the spec on the CPU?  "8 core" could be a number of models.

Three 25 CFM case fans is a bit anemic nowadays, particularly if your interior airflow isn't extremely clean.

A single 32 CFM fan on the CPU may simply be inadequate at 100% processor utilization.  I have an AMD FX-8350 cooled by a big Noctua with two 140mm fans.

A GPU originally designed to be silent will not be a powerhouse, so I'd be pretty confindent that the lion's share of the effort is falling on the CPU.  Your CPU cooling solution is the most likely cause of your overheating.

---

### Post by Rick St. George on 2016-09-21
SYSTEM INFO

Mobo:
MSI 990FXA-GD65 v2R

CPU:
AMD FX-8320 Vishera 8 core

RAM:
2 x 8GB Corsair Vengence 1600 Mhz

GPU:
ASUS GT610 w/2GB DDR3 Ram (running 2 monitors)

PSU:
Enermax ENP450AST 450 Watt

OS:
UbuntuStudio-64 v16.04 LTS

> **QIII said:**
> 
I have an AMD FX-8350 cooled by a big Noctua  with two 140mm fans.


I tried something similiar with 120mm fans and they would not fit. Overhang on RAM chips and too tall for width of case!
Would really like to find an alternative that would fit. Maybe! that would solve the problem.

---

### Post by QIII on 2016-09-21
Yeah.  My vote is inadequate cooling, then.  No HSF with a single 80mm fan is going to be able to keep up with that CPU running at full speed for more than a few seconds at a time.  Continuous loads for the time it takes to do video transcoding are simply going to be too much.

Either you'll have to deliberately limit the frequesncy of the the CPU (it's a shame to have it if you can't use it!) or get a more capable cooler on it and really pay attention to cable management.  Is that an old server case?

---

### Post by Rick St. George on 2016-09-21
> **QIII said:**
> Yeah.  My vote is inadequate cooling, then.  No HSF with a single 80mm fan is going to be able to keep up with that CPU running at full speed for more than a few seconds at a time.  Continuous loads for the time it takes to do video transcoding are simply going to be too much.

Either you'll have to deliberately limit the frequesncy of the the CPU (it's a shame to have it if you can't use it!) or get a more capable cooler on it and really pay attention to cable management.  Is that an old server case?

Yes, an older case. But big and can handle anything I put in it. Except for airplane engine heatsinks.

Will look at BIOS settings more carefully from MSI recommendations. Will keep this Thread open until I find a cure, and post back results.

Thanks everyone for helping make Ubuntu the best open source project on planet Earth!

---

### Post by Rick St. George on 2016-11-10
Sorry took so long to get back. Here is what I did.
Replaced stock heatsink with a Cooler Master GeminII S524 Version 2 with 5 Direct Contact Heat Pipes, then added two (1 front, 1 back) Arctic F12 120mm case fans with fluid dynamic bearings 1,350 RPM @ 12 V / Max. Airflow 74 CFM and low Noise Level: 0.3 Sone. 

Case is blowing through at 70+ CFM keeping the CPU at 28 to 48c and GeForce GT 610 at 40 to 43c.  However, I noitced that DeeVeeDee cannot handle more than 1 video to compile as it attempts to render them at the same time causing the CPU to max out overheat and a system shutdown. Am trying to learn KdenLive now. Hope I can someday manage to create and burn videos again.

Thanks everyone, hope this helps some newbie and note that I live in S. Florida and most of the year when the AC is running, we can only cool it down to 80 F inside, because outside its over 90 F. So case cooling is major concern.

Peace,
Rick

:popcorn:

---

### Post by Rick St. George on 2017-03-26
> **mc4man said:**
> Sounds like hardware (cooling) issue. (or core scale down is too slow..

Anyway last year I was testing a system76 laptop, 1st. thing I did was some h.264 encoding & it crashed due to reaching critical temp. On some subsequent runs some cores were always flirting near critical before being scaled back  so there was no assurance any encoding would actually complete.
From there I tried setting the  max_perf_pct to 90%. That didn't affect encoding speed to any great extent & did kept the temps down enough to not threaten a critical shutdown.

I don't exactly remember how I did that, likely like this (Intel cpu, 4.x kernel
```
echo "90" | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

This setting is only good for current session, goes away after reboot. So maybe try it @ 90 or 85, ect.

(- the issue with the sys76 laptop was it was using a desktop cpu with insufficient cooling

Now that I solved the cooling issue, certain programs still heat up all 8 cores to the point of shutdown.
I believe I found where the "control" is - in this file "/sys/devices/system/cpu/cpufreq/ondemand/up_threshold".
But cannot edit with sudo gedit. It shows 95 in the file, and would like to lower it to say '80'. This may help!

Any suggestions?
Thanks!

---

### Post by Doug S on 2017-03-27
> **Rick St. George said:**
> Now that I solved the cooling issue, certain programs still heat up all 8 cores to the point of shutdown.
I believe I found where the "control" is - in this file "/sys/devices/system/cpu/cpufreq/ondemand/up_threshold".
But cannot edit with sudo gedit. It shows 95 in the file, and would like to lower it to say '80'. This may help!
No, I do not think you want to adjust that number. It defines under what load the CPU will ramp up the frequency, it does not define the upper frequency limit.
Since your CPU is AMD, you would not be using the intel_pstate driver. I think you would set your maximum frequency the acpi-cpufreq way. Via:
```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq
3400000
3400000
```And you would get available frequencies to use via:```
~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
3400000 2400000
3400000 2400000

```But first check which CPU frequency scaling driver and governor you are using (as I have just assumed):```
doug@DOUG-64:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq
doug@DOUG-64:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand

```

---

### Post by Rick St. George on 2017-03-27
Here is what I did .... that worked!

I managed to change the default configuration from "ondemand" to  "conservative" at every boot. To do this, I had to install some packages  and edit some system files. All the steps require superuser permissions  to make the changes system-wide. Be careful when making the needed  editions.

The packages I had to install to make this configuration were:

```
cpufrequtils
``` 


and

```
sysv-rc-conf
``` 


I did the following: 

1) Edit the file /etc/init.d/cpufrequtils: (remember to use gksu instead of sudo)

```
gksu gedit /etc/init.d/cpufrequtils
``` 


I changed the line: GOVERNOR="ondemand" 
to
GOVERNOR="conservative" 

Then I changed the value in Max_Speed to 2nd highest indicated in 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

And set the Min_Speed to the Lowest Value shown in file above.

2) Using sysv-rc-conf: (CAVEAT - Be Very Careful Here)
There will be many options (apache, bluetooth, cron, ...). One of them  is ondemand and it will be started in many boot stages. Deactivate  ondemand in all of them, by REMOVING THE 'X', then the configuration set at  /etc/init.d/cpufrequtils will be used.

```
sudo sysv-rc-conf
```

=========
AFTERWARD
=========

Ran DeVeDeNG to Burn 2 videos to DVD. Normally CPU temp would run upto 90C and shutdown.

Now, CPU usage is at 75% and CPU Temp about 40C, with ALL 8 cores running. Hope this Helps someone else running AMD 8 core CPU.

---

