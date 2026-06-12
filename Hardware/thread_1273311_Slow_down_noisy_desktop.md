---
title: "Slow down noisy desktop?"
date: 2009-09-23
forum: Hardware
---

### Post by ticktick on 2009-09-23
Hi there,
recently I purchased a Dell SX270 desktop and I was looking forward to use that as my new workstation at home with Ubuntu. But it turns out that this thing is extremely noisy and that spoils all the fun and concentration. It becomes very warm during operation, so I guess there is a good reason that the cooler is going crazy. Isn't there a tool to downgrade the MHz and slow down the cooler? I thought I saw something like that a while ago, but I cannot remember what it was.
Greetings, Tom

---

### Post by cguy on 2009-09-23
Maybe it's overreacting.
Adjust the PWM settings in BIOS to keep the speed under control.

Gnome already has a built-in frequency scaler which is called just like that. Look for it in the "Add to panel..." window.

--
If other, uncontrollable fans also make a noise, buy some potentiometers and stick'em in the circuits. I did just that and now everything is pretty silent. No probs with the temperatures.

---

### Post by ticktick on 2009-09-23
Thank you cguy,  When I try to add the CPU Frequency Scaling Monitor to the panel, it returns an error message:    CPU frequency scaling unsupported. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.  I don't understand what you mean by PWM settings in the BIOS. I actually entered the BIOS to see if anything can be changed, but the 2.8 MHz are fix, no option to modify it.   (By the way, I made a mistake: I don't own a SX270, but an SX280.)  Your hint to stick some potentiometers somewhere into my machine is probably too geeky for me to understand. But again, thank's a lot. I guess I consider buying somthing else.

---

### Post by cguy on 2009-09-23
Enter the "System health settings" (or similar) in BIOS and you'll the system temperatures and options to modify the CPU fan speed (PWM - Pulse Width Modulation - is a techinque to control the rotational speed)

You have a start value - the minimum speed of the fan
You have a max value  - the maximum speed of the fan
You have a slope/step/whatever it's called - how fast the fan may accelerate

^^^ these are small numbers (1,2,3...60, maybe as high as 128), not actual fan speeds

A high acceleration (which means a sudden change in background noise) is more annoying than a fast rotating fan, so be sure to set a low number for it.

I have set a step of ~2, a minimum speed at ~1500 rpm and the maximum speed - no idea.
Overall it's silent and cool enough.

Choose what seems reasonable for you.


HOWEVER
On my system, the real noise sources were the PSU fan and system chip fan, both uncontrollable by software; the latter was spinning as high as 5500 rpm -> extremely annoying.

Fitting potentiometers is nor hard nor geeky. Don't set limiting beliefs.
Each fan has 2, 3 or 4 wires.
If you can't control a certain fan by software (BIOS included), you can insert a potentiometer along the RED wire and fix it somewhere on the case, for easy access.
Choose a low power potentiometer with a range between 0 and ~150 Ohms.

It can make a HUGE difference.

----

Regarding the CPU frequency scaler:
Unless your CPU is very old, I highly doubt it doesn't support scaling. Install cpufreq (and any other dependency) from synaptic and then try adding the panel item again.
Do a google search to see which are the dependencies.

```
cat /proc/cpuinfo    <- the command I gave to the terminal
...
stepping	: 2   <- means that my CPU has two possible frequencies
...

```

---

### Post by ticktick on 2009-09-23
Hi cguy,  Thank you very much, again, for the time and patience you took for my problem, you are very generous and helpful. The BIOS of the SX280 really doesn't have the options you mentioned, I walked through it several times. The only thing that seems to come close to noise options is the choice for Hyper-Threading (On/Off, I chose off) and HDD Acoustic mode (bypass, quiet, suggested, or performance; I chose quiet). And in /proc/cpuinfo, there is stepping=1. I searched for a BIOS update, but I seem to have the most recent one. At the moment, the noise is moderate. But as soon as I start say firefox, I feel like standing next to a jumbo jet. I am fed up with this thing, I cannot stand noise in my quiet study room. I think I consider buying something like the Eee box or some of these new nettops. I don't have the money, really, but it might even be an investment for the long run, as it saves the environment and power consumption. Anyway, thank you very much again. You have been very kind. Greetings, Tom

---

### Post by nitrogensixteen on 2009-09-23
Replace your system fan with a SilenX or other ultra-low noise fan.
[www.frozencpu.com](www.frozencpu.com) has a wide selection.

---

