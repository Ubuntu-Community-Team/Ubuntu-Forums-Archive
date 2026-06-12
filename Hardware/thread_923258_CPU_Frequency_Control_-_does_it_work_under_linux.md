---
title: "CPU Frequency Control - does it work under linux"
date: 2008-09-18
forum: Hardware
---

### Post by reesje on 2008-09-18
Hi Guys,

I am trying to get frequency scaling to work on my laptop, a HP5100 series with a 1.6Mhz core duo processor. By running this:
```
sudo dpkg-reconfigure gnome-applets
```
I can give CPU frequency monitor administrative rights, and thereby control the multiplier.

However I don't think setting the frequency using CPU frequency monitor works. What is my evindence? Actually I don't have hard evidence, but one indication is that when I run two instances of burnMMX (cpuburn package) I can see that the temperature rises from the approx. 48C in idle to approx. 67. There  is no difference whether it runs with the frequency set to 800MHz or 1600MHz. 

In windows I have done more or less the same using Notebook Hardware Control (for setting the frequency) and Orthos (for stressing the CPU) If the multiplier is set to 1600MHz the temperature rises to approx. 70C and if set to 800MHz 55C (I think Orthos is harder on the CPU when set to small FFTs).

What happens the the temperature under windows makes sence, since the CPU is running at a much lower voltage at 800MHz (0.95V) whereas what happens in linux indicates that the software doesn't have the appeared control over the hardware.

I have emifreq and I get the same results. When using both I can see that emifreq affects the displayed frequency in CPU frequency monitor (if set to dynamic I can see in CPU frequency monitor that the frequency changes sometimes, whereas if set to 800MHz CPU frequency monitor always shows 800MHz).

I hope somebody will be able to help me figuring out what is wrong, since it helps me keeping the fan turned off during movie playback. In windows this works perfectly, but I would much rather use linux.

BR,
René

---

### Post by reesje on 2008-09-22
OK. Found the solution. After fiddling around in preferences for the applet I saw that it showed only CPU0. I have to add two applets to the panel and set BOTH to powersave. Now it seems to work. Not very smart. It should be possible to control both cores from the same applet. Who wants to set only one core to e.g. powersave? Oh well, at least it works.

BR,
René

---

