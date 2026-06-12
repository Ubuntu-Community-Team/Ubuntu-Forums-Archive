---
title: "cpu, fan speed, cool and quiet etc"
date: 2009-09-14
forum: Hardware
---

### Post by badbetty on 2009-09-14
Hello folks

Asus M4A78 Pro Phenom II x8 quad   is the guts of my desktop running Ubuntu 9.04.

Please, is there anyone who has a good degree of knowledge to resolve getting the 'cool and quiet' feature [of the hardware] working so it does all that it should properly? 

I believe, the cores' MHz are being affected, but not the fan(s).

I have got the BIOS settings enabled.  I have 'cpufreqd' and the utils all loaded, including and applet and it seems that Ubuntu is reducing the MHz on my core(s) it seems; all of them i hope!

However, the fan speed remains at full speed all the time, despite the MHz reductions on the cores.
(are all fans controlled I wonder).

I have tried lm_sensors, but it cannot detect any K10 based sensors it seems - 'driver to be written' is the msg - when in detect mode.

I have to say that in Win XP [spit] , the software really does shut all the machine down to really quiet when idle - even the fans!

How does one control all this reliably and correctly?
As you can guess I am really very new to all this Linux stuff.

Thank you for any help; and for reading!
BB

---

### Post by mad0master on 2009-09-17
yeah, my laptop also got a sort of noisy... :(

---

### Post by compeng on 2009-09-19
I have a ASUS M4A78E-T mobo with an AMD Phenom II 945 quad core.  I am interested in what the cool-n-quiet features does too.  I  just turned it on.

I started to play with the Q-fan 2 features.  It seems to reduce the fan speeds if you set it to [Quiet].  I am not sure I trust it to turn the fans up when it needs it.  I tried to install lm-sensors.  It did not detect anything it could control.  Badbetty did you try this yet?

---

### Post by Petter s on 2010-05-03
I also have ASUS M4A78E-T and the cpu-fan is running at max all the time in ubuntu 10.04. It is really quiet in windows.
compeng where did you set it to [Quiet]?

---

### Post by tehowe on 2011-01-16
Installing powernowd from Synaptic will adjust the frequency of your cores, but even with Cool and Quiet enabled on my ASUS M4A88TD-V EVO USB3 and powernowd doing its thing, I still haven't heard the fan take a break yet.

You can watch what your cores are doing with 

```
cat /proc/cpuinfo | grep -i Mhz
```

They'll stay at topspeed unless you have powernowd installed. If you want to give them a workout, open terminal windows and run

```
cat /dev/urandom > /dev/null
```

Now if you drop into a shell and 

```
man fancontrol
```

Clearly this is some kind of util for fine-grained control of fan speeds. Searching around elsewhere on this forum, I discovered there's a script that's supposed to help you set up the fancontrol config file called 'pwmconfig' but running it from root told me that 

*/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed*

Any hardware gurus willing to point this thread in the right direction to shut noisy fans up? Sample config file for fancontrol maybe? I've an AMD Phenom II x6 BTW

---

### Post by tehowe on 2011-01-19
> **tehowe said:**
> Installing powernowd from Synaptic will adjust  the frequency of your cores, but even with Cool and Quiet enabled on my  ASUS M4A88TD-V EVO USB3 and powernowd doing its thing, I still haven't  heard the fan take a break yet. 

And blah blah blah...



Forget about that. As it turns out, I was missing as additional BIOS setting as well. For some reason the Asus M4A88TD-V EVO USB3, and probably others, come with a default Q-Fan setting of NORMAL (it's in the POWER subsection of the BIOS). 'Normal', apparently, is to have your computer sound like a jet turbine, with my 1090T hexcore running at around 5500 - 6000 RPM.

I simply changed this setting to SILENT and now we're at far more reasonable sounding ~4000 RPM. Try it out, your fan bearings will thank you.

---

