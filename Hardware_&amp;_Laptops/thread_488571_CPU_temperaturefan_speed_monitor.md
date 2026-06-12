---
title: "CPU temperature/fan speed monitor"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by marshall.robert on 2007-06-30
Hi, is there a program/applet/or something that can report the cpu temperature and fan speed?

thanks
-rob

---

### Post by youknowit on 2008-02-14
If you are still looking for a solution, here is what I found:

[http://www.linuxforums.org/forum/servers/44767-temperature-fan-speed.html](http://www.linuxforums.org/forum/servers/44767-temperature-fan-speed.html)

This is particularly useful, I think:

[http://www.edgedesign.us/about/lm_sensors](http://www.edgedesign.us/about/lm_sensors)

One way to use lm-sensors is this:

```
sudo apt-get install lm-sensors
```

Then, you detect what hardware elements can be detected by issuing

```
sudo sensors-detect 
```

It will tell you which modules need to be loaded in order to use the sensors programme.  Load those modules by issuing

```
sudo modprobe [the modules suggested by sensors-detect programme]
```

Once all the modules are loaded, issue 

```
sensors
```

It will tell you the CPU temperature, fan speed, etc.

---

