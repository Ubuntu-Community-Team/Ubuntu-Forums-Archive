---
title: "how to interpret /usr/bin/sensors"
date: 2010-06-06
forum: Hardware
---

### Post by lz1dsb on 2010-06-06
Today I stumbled upon this nice neat application called Conky. I was able to grasp pretty quickly the idea behind the configuration file (well, at least most of it, as it seems the configuration options there are almost endless). So I was able to built a config file from the many examples there are in the net and in the forums. I'm very interested in the possibility to be able to monitor the temperatures on my machine (Dell Studion 1555) and I got this example:
Temps - CORE1:${execi 6 /usr/bin/sensors | grep Core0 | paste -s | cut -c12-19}, CORE2:${execi 6 /usr/bin/sensors | grep Core1 | paste -s | cut -c12-19}, HDD:${hddtemp /dev/sda9 127.0.0.1 7634}
The problem is, that when I start Conky with that line, I don't see any readings of the temps. And I believe that my problem is that for my machine I got a slightly different output that what the author of the script got. Here's what I get:
laptop:/usr/bin$ sudo /usr/bin/sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +100.0°C)                  
temp2:       +47.0°C  (crit = +100.0°C)                  
temp3:       +52.0°C  (crit = +100.0°C)   
Now I understand what's the idea behind the above mentioned script, #execi is executing /usr/bin/sensors each second and there are some output modifiers. On my machine though, the output modifiers are useless, as the output doesn't show such a wealth of information. So here comes my major question. How to interpret the output of /usr/bin/sensors on my machine? Is this specific by the hardware vendor or the Linux version? How to get more info?
And also the second concern. I noticed that I have to be a superuser to execute /usr/bin/sensors. I'm not sure if this happens when conky is started. How to make conky execute the script as a superuser, and is it really needed?

---

### Post by lz1dsb on 2010-06-08
I think I found it. After installing the packet lm-sensors and than detecting what sensors I do have on my machine with sensors-detect, I'm now able to read the temperature of my CPU... Well, unfortunately the output isn't showing that much information like I was expecting, like fan speed, voltages etc. but at least it's something...

---

### Post by lz1dsb on 2010-06-09
I'm able now to use output modification on the output of sensors:
"CORE 0:${execi 6 sensors | grep Core.0 | awk '{print $3}'}"
so now I can read the temperature of both cores and visualize it correctly in conky.
The problem I still got though, is the temperature of the HDD. I can execute the command hddtemp only as a super user. So even though I start conky as a superuser, hddtemp doesn't give me any readings in the conky window. Any ideas?

Cheers,
Boyan

---

