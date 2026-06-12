---
title: "Sony Vaio Z2 heating problem"
date: 2012-04-07
forum: Hardware
---

### Post by MarcoDiMarco on 2012-04-07
Hi all!

I recently installed ubuntu on my new sony vaio z2. I have never actually experienced any issues with ubuntu but now i got my first one.

It occurs to me that the laptop gets overheated. I've tried searching for the reason why it gets so warm. I got the device dual booted with windows and i found out that it only happens in ubuntu. 

Until now i have installed powertop:
[IMG]http://www.artwork-creations.com/Screenshot%20at%202012-04-07%2019_10_46.png[/IMG]

As you can see, not really something shocking is happening around there....

Furthermore, i have installed sensors:

```
~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +98.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +55.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +52.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +53.0°C  (high = +86.0°C, crit = +100.0°C)

```

I've also checked my system monitor, nothing thats out of the ordinary and using a huge amount of CPU or something..

Ive turned down my screen's brightness and used jupiter to lower my laptops perfomance to power saving. Still, too warm. 

Does any of you have a idea of what this might be and/or how to resolve this? Or any ideas on how to find the problem?

Many thanks in advance!

Note: i use ubuntu 11.10 with unity.

---

