---
title: "Reading cpu temperature Intel celeron (R) lm-sensors"
date: 2012-12-01
forum: Hardware
---

### Post by atim21 on 2012-12-01
I know there are already a lot of questions like this, but non of the answers provided there could fix my problem. I try to read out my cpu temperature with lm-sensors on my ubuntu 10.04 LTS installation but I can't get to work. I did try the command

```
sensors-detect

```
several times but still nothing. My computer is an old PC with an Intel Celeron (R) @ 2.60 GHz. The odd thing is that the hdd temp is shown in the applet but when I type in the terminal

```
sensors
```

I get the error: "No sensors found! Make sure you loaded all the kernel drivers you need." I'm not really interested in the hdd temperature but I think it is strange that these sensors do work in the applet and not in the terminal.

This is the output that sensors-detect gives: [http://pastebin.com/F4hVKaLU](http://pastebin.com/F4hVKaLU)

Any suggestions?

---

### Post by jonnyboysmithy on 2012-12-01
I have an old intel pentium m (it is of the celeron family if I remember correctly) and I could read the temperature of that with: 
```
acpi -t
```
You probably have to install the acpi package first:
```
sudo apt-get install acpi
```
There is an applet that will work with the above.. Not sure which one, but try that see if it works.

---

### Post by atim21 on 2012-12-01
Should ```
acpi -t
``` give any output? When I type it in in the terminal I don't get any output. I use the GNOME sensor applet and this applet should be able to read out acpi thermal zones. After executing ```
acpi -t
``` there are still no extra sensors found in the applet.

---

### Post by 2F4U on 2012-12-01
Is sensors-detect telling you to load additional kernel modules? If not, it may indeed be the case that your machine either has no sensors or they are not compatible.
The command acpi -t should give you an output such as

Thermal 0: ok, 34.0 degrees C

I get this on my ancient ThinkPad T41 with Pentium M processor.

---

### Post by atim21 on 2012-12-01
This is the output that sensors-detect gives me:
[http://pastebin.com/F4hVKaLU](http://pastebin.com/F4hVKaLU)

When I type acpi -t  it just doesn't give anything back, no error, no temperature, nothing.

I found an other package called mbmon in the ubuntu software center and does give back data but how can I be sure that the data is correct? The temperature is always around 35°C even when I'm doing a cpu intensive calculation like calculating and drawing a fractal.

[Edit:] In the bios I can get temperature readings so my system definitely has sensors built in.

---

### Post by Yellow Pasque on 2012-12-01
It looks like you're out of luck. sensors-detect finds your sensors, but doesn't have proper drivers for them. Unfortunately, lm-sensors.org is down right now, or we could look in their sensor database for more details.

---

### Post by jonnyboysmithy on 2012-12-01
My laptop has tons of sensors: 2x ram temps, cpu-core0 cpu-core1, cpu-package-temp, graphics card temperature, ambient temperature (I think its ambient).. gosh its a lot.
For all I know 35C might be the ambient temp in your box or you ram temp...
In ubuntu only 4 of those sensors work (used to be two now its 4 with the newer 12.10).

I noticed an option in the acpi help:  ```
-p, --proc               use old proc interface instead of new sys interface
```Seeing you have an older system you may want to try that.
Is this a desktop machine?

---

### Post by Yellow Pasque on 2012-12-01
> **jonnyboysmithy said:**
> I noticed an option in the acpi help:  ```
-p, --proc               use old proc interface instead of new sys interface
```

I don't see any harm in trying the option, but I wouldn't recommend it. Ubuntu 10.04 uses a 2.6.32 kernel and does not use the old procfs.

---

### Post by atim21 on 2012-12-01
It's a desktopmachine. 
I'll try to use the old proc interfaces, hopefully that solves the problem.

---

