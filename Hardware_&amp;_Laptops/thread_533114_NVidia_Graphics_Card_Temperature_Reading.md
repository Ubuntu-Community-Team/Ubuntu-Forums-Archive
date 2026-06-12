---
title: "NVidia Graphics Card Temperature Reading"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by mavicus on 2007-08-23
I have an NVidia GeForce 8500GT, and will probably be purchasing 8800s for other computers in the near future.
I am able to see the temperature of the card in nvidia-settings.
However, I would like to see it in other software, such as hardware-monitor for the Gnome panel.
This I'm sure would involve getting it to detect as a normal sensor with lm-sensors or such, so that it shows up when I type "sensors" at the command line.

I have followed the post on how to configure lm-sensors, but nothing new shows up about my graphics card when I do that.

Does anyone know if there is a way to get this temperature reading to be detected like other voltage and temperature readings with lm-sensors, or in some other hack to detect it and inject this data into lm-sensors readings?

FYI, pertinent specs in this computer are:
Asus p5n-e sli motherboard (still working through voltage readings for it, or looking for someone with data)
quad-core processor
geforce 8500GT video card
both 32 and 64 bit versions of ubuntu 7.04, 32 bit is there just for emergencies.

-thanks

---

### Post by NoVista on 2007-08-26
Install "hddtemp"
It will add temperature monitoring for all your hard drives.
It does a great job here, identifies all three of my drives to the model number!

However, I too would like to know how to monitor temperature for video cards.
I haven't seen anything written on this. Somebody help please .. ..

---

### Post by mavicus on 2007-09-06
UPDATE:
I still don't know how to inject nvidia temp data into lm-sensors, if there is a way...

But for now I am able to monitor everything I want with sensors-applet, this includes nvidia data and hddtemp data.

---

### Post by NoVista on 2007-09-07
I am not endorsing this,  I have no way to check the package as it is not applicable to my video card, but I found this site you might be intersted in.. ..
[http://www.linuxhardware.org/nvclock/#download](http://www.linuxhardware.org/nvclock/#download)
If you scroll down to the "Features" section, it says:
Hardware monitoring (including temperature reading, fanspeed adjustments)
Support for internal NV43/NV44/NV47/G7x temperature sensor
Ability to enable disabled temperature sensors used on NV43/NV44/NV47/G7x boards

---

### Post by pejcaofrito on 2007-11-19
> **mavicus said:**
> UPDATE:
I still don't know how to inject nvidia temp data into lm-sensors, if there is a way...

But for now I am able to monitor everything I want with sensors-applet, this includes nvidia data and hddtemp data.

Rigth, but as their webpage says [here]("http://sensors-applet.sourceforge.net/index.php?content=requirements"):
"For NVIDIA graphics cards support:

    * NVIDIA binary driver with libNVCtrl installed (provided with the nvidia-settings utility) (to enable support GNOME Sensors Applet needs to be configured with the --with-nvidia flag)"

And I doubt that flag has been used (since nvidia-glx-whatever would become a dependency of G-S-A)

Anyway, G-S-A is indeed very good, now I'll try to find a deb built with that flag

---

### Post by mitsuho on 2007-11-19
If you have meaningful digits from command line 'sensors' after 'sensors-detect' installation
process.  'gkrellm' will be a nice program to monitor various hardware. Please try it.

---

### Post by reiki on 2007-12-15
Try this in a terminal:

```
nvidia-settings -g gpucoretemp
```

and see if you get a meaningful result. I am running Gutsy and using a 7300GT card .

I get a readout from Conky by putting this line in there:

```
${color lightgrey}NVidia GPU Temp:$color ${execi 30 nvidia-settings -q gpucoretemp |grep '):' | awk '{print $4}'} C
```

That should give you a place to start.

---

### Post by aaronjb on 2007-12-30
> **reiki said:**
> ```
${color lightgrey}NVidia GPU Temp:$color ${execi 30 nvidia-settings -q gpucoretemp |grep '):' | awk '{print $4}'} C
```

That should give you a place to start.

Excellent info :) I thought I was going to have to use 'nvclock' to pull out the temperature until I saw your post.

It looks like the nvidia-settings app that I have needs slightly different syntax however - the 'gpucoretemp' is case sensitive, and there's an annoying trailing '.' after the temperature - so here's what I used:

```
${color orange}GPU ${hr 2}$color
GPU0:  ${execi 30 nvidia-settings -q [gpu:0]/GPUCoreTemp | grep '):' | awk '{print $4}' | sed 's/\.//'}C
GPU1:  ${execi 30 nvidia-settings -q [gpu:1]/GPUCoreTemp | grep '):' | awk '{print $4}' | sed 's/\.//'}C
```

I have two 7900GS cards in SLi in this laptop, hence the two commands above - if you've only one GPU then only the first line would be valid.  The little sed script does a regex replace to kill the trailing '.'.

(Actually I have it pulling the current clock frequencies with GPUCurrentClockFreq as well now, but that's a little extraneous :))


Anyway - thanks for the tip :)

---

### Post by motin on 2008-06-27
> **NoVista said:**
> Install "hddtemp"
It will add temperature monitoring for all your hard drives.
It does a great job here, identifies all three of my drives to the model number!

Thanks man - that was exactly what I was looking for!

---

