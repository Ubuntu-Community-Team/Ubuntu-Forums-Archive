---
title: "Linux temperature monitoring and hardware info"
date: 2008-07-11
forum: General Help
---

### Post by Shwick2 on 2008-07-11
I'm going to be installing Ubuntu 8.04 desktop and I need a program, preferably with a GUI, that provides temperature monitoring of all known sensors on my motherboard.

I've heard about lm_sensors, but is there a GUI for it?

Also, is there a hardware info program for Linux that is similar to cpu-z?  I'm looking for something that will provide thorough, human readable information.  At the least:
-cpu multiplier
-fsb
-memory speed
-memory timings

I've heard of HardwareLiSter, but I looked through a few screenshots and I'm not sure if it has what I want.  Does anyone have any recommendations?

Thanks.

---

### Post by cariboo on 2008-07-12
You can monitor cpu temps, core temps fan speeds hard drive temps and any other sensor that is supported by lm-sensors.  you can install them from the command line like this:

 ```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Or use Add/Remove Programs or Synaptic Package Manager

Once you have installed the packages in a Application-->Accessories-->Terminal type:

```
sudo sensors-detect
```

answer yes  to all the questions, then reboot.

Once you are back to your desktop right click on the upper panel and click add to panel, scroll down to hardware sensors and click, they will appear in the panel. Right click on the sensors then click preferences and select the sensors you want to monitor.

Jim

---

### Post by ModelM on 2008-07-12
You might want to check out GKrellM. Between all the built-in features & those provided by plugins, it does quite a lot.

---

### Post by Shwick2 on 2008-07-12
Thanks Cariboo907, that was exactly what I needed to know.

 ModelM: GKrellM looks good, I might try that out as well.

---

