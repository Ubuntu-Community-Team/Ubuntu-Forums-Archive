---
title: "Laptop Fan Runs ALL THE TIME!"
date: 2010-05-24
forum: Hardware
---

### Post by daemon3 on 2010-05-24
My laptop fan seems to run all the time, which, ironically, heats up the computer, so I get a lot of system crashes, especially if I'm watching my favorite show on Hulu.  I'm trying to control my fan with the program fancontrol, but I'm having a hard time finding out my fan device.  When I type sensors, I get the following output:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +73.0°C  (crit = +105.0°C)

```
But I can't find temp1 in /dev/.  Any idea how to find my fan device?  Thanks.

---

### Post by dino99 on 2010-05-24
run: sensors-detect, but check the powersaving settings

---

### Post by Yellow Pasque on 2010-05-24
> which, ironically, heats up the computer, so I get a lot of system crashes, especially if I'm watching my favorite show on Hulu.
The fan doesn't heat up the computer; it runs because the CPU is too hot. Your laptop's overheating :( (or you have a bad sensor, but that's not too likely, especially if your system crashes under load).

Laptop manufacturers often use cheap thermal pads to connect the heatsink to the CPU. You may have to open up the laptop, clean out the dust, clean the heatsink/CPU with rubbing alcohol and reapply the heatsink with quality thermal grease.

Until then, try and find a thermal shutdown trigger in the BIOS. Overheating the CPU to the point of failure is a good way to put yourself in the market for a new CPU.

---

### Post by daemon3 on 2010-05-30
So, to solve the real problem, I'd need to get a better CPU?  Isn't the CPU dependent on the operating system, in that Ubuntu controls the CPU which, in turn, will keep my computer cool?

---

### Post by Yellow Pasque on 2010-05-31
> **daemon3 said:**
> So, to solve the real problem, I'd need to get a better CPU?
No. You need to fix your cooling system.

---

### Post by yossell on 2010-05-31
To a degree, you're right, the operating system controls how hot the cpu is. If the operating system is running your cpu at high frequencies without downclocking, then your system will run hot. 

There are utilities you can run on your computer which will try and make the cpu run more slowly. As a start, you might try adding the cpu frequency scaling monitor to gnome panel and experiment with the settings. However, video may not play so well with the chip constantly downclocked. So I would have a look at your laptop's cooling system. 

I certainly wouldn't recommend overriding the fan - as that will probably lead to overheating problems unless you're very sure what you're doing and can reliably monitor your system's temperature.

---

