---
title: "Turn Off CPU Scaling For Real"
date: 2008-10-11
forum: Hardware
---

### Post by lightnb on 2008-10-11
I've set "computer speed policy" to "always maximum speed" in power management, but it's lying.

The computer is still revving up and down all day long and its getting on my nerves. How can I lock/force/'do it anyway' the processor at full power, and the fan at full speed, always?

---

### Post by lightnb on 2008-10-16
bump.

---

### Post by lightnb on 2008-10-19
If there's no software means of fixing this, maybe I can rewire the CPU fan to another power source that's a constant voltage?

---

### Post by deanjm1963 on 2008-10-19
If you open up "Services" from System > Administration and "unlock" it, there is an option to disable "turn off" cpu scaling (CPU Frequency Manager).

hope this helps.

---

### Post by aaronb on 2008-10-19
Its hard make stable the amount of heat the processor will output even if you lock the speed of the processor by disabling Intel speed step or whatever AMD users in the BIOS. (If you disable the power saving options, your PC may use more power and probably be louder).

I've found it best for desktop PC to...
1. Use canned air every 6 to 12 months to clear out dust from the PC.
2. Change the CPU heat sink to something a little better than the stock heat sink.
3. Look at your BIOS settings as a lot of PCs or Laptops come with options on how fan speed is controlled.

(The usual notice about how BIOS settings can damage your PC or Laptop.)

---

### Post by lightnb on 2008-10-19
Hi Guys,

I turned off the CPU scaling service and rebooted, but the fan still changes speed a lot. Are CPU and Fan scaling separate? Maybe CPU scaling is fine, and it's just the fan that's causing problems.


The ideal scenario would be:

The Fan and CPU both run at full. If there's 15 minutes of inactivity, they drop down to minimal. When there's any activity, they jump back to full and stay there until the system is idle again for a full 15 minutes. Just like a screen saver.


If that's not possible (or practical) is there a way to set the CPU fan to "always full" as well? I don't mind the noise, it's just the changing speed that bothers me.

I've checked for settings in BIOS, but it's one of those stupid Intel BIOS's that don't give you any choices. I'm on a laptop, so I'm not sure if there's much in the way of replacement heat sinks. The air coming out of the exhaust hole is always hot, so I think more fan would be beneficial.

Also, the output of 'Sensors' is:

```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0°C  (crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +67.0°C  (crit = +100.0°C)

```

There's a whole bunch of stuff missing, but I cant find any guides/instructions for LM-Sensors, etc. under Hardy. Maybe this is related?

Thanks again

---

### Post by aaronb on 2008-10-19
This link may help:

[http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed](http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed)

---

### Post by Krydahl on 2008-10-19
Yes, CPU scaling and fan control are definitely separate. 

If you can't turn off the fan control in the bios then the easiest way is probably to just not plug the fans into the motherboard - use a power lead off the PSU instead. If the fans run too fast, you can get a fan controller and manually tweak the voltages to adjust fan speed.

Ah, just re-read your post and see it's a laptop. You're probably screwed then.

---

### Post by lightnb on 2008-10-19
I'm still having trouble with the sensors command, and pwmconfig gives the error:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

I did run sudo sensors-detect.

---

### Post by aaronb on 2008-10-19
> **lightnb said:**
>  I did run sudo sensors-detect.

Did you agree to all the questions?
And have you rebooted since running it?

---

### Post by lightnb on 2008-10-19
yes and yes.

---

### Post by aaronb on 2008-10-19
Whats your make and model of laptop?

---

### Post by lightnb on 2008-10-20
System76 Serval Performance

---

### Post by Simon S on 2008-10-21
On my laptop, an old Dell D400, I installed the configuration editor, ran it from the main > system tools menu and set the apps > gnome-power-manager > cpufreq > policy_ac key to "performance". After that it runs at maximum soeed all the time when plugged in and I can change it back to ondemand whenever I like.

Hope it helps

Simon

---

### Post by lightnb on 2008-10-23
I think the CPU is actually set to full power, and it's just the fan that's being obnoxious. I thought they were linked, so when the CPU revs up the fan revs up, and vis versa, but I think the CPU is actually working correctly.

Is there any configuration directve that disables fan speed scaling?

---

