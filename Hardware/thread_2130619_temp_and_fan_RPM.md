---
title: "temp and fan RPM"
date: 2013-03-30
forum: Hardware
---

### Post by t430 on 2013-03-30
Hi,

Just finished installing Ubuntu 12.04.2 on my Lenovo Thinkpad T430. My thinkpad does not have the Switchable Graphics, just stock graphics card on the motherboard.

I installed the lm sensor utility and given below is the output:

```
think@t430:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +200.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +43.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +41.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +41.0°C  (high = +87.0°C, crit = +105.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2471 RPM

think@t430:~$ 
```

The next few seconds when I run the command, everything else remains pretty much same, just the fan1 RPM shows 0
```

think@t430:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +42.0°C  (crit = +200.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +43.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +43.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +42.0°C  (high = +87.0°C, crit = +105.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM

think@t430:~$ 
```

The next few seconds, the fan1 RPM jumps again to 2495 RPM...and then gradually reduces and this keeps happening.

My questions are:

1) Are the Core Temps too high? 42-43 and sometimes even 48 Degree Celcius.... I am very much using a cooling pad.

2) The fan1 RPM worries me the most...

Please let me know.

---

### Post by carl4926 on 2013-03-30
Don't believe everything you read. Use your eyes... Is that Fan spinning?

The figures are self explanatory and clearly OK

---

### Post by t430 on 2013-03-30
Hi Carl,

Thank you for your quick reply. The Ubuntu forums are really great....never got such a quick reply before on any forum till date. :)

Coming back to the heat issue, I can hear the fan spinning, but its not whizzing too much.

The laptop feels a lot more warm, especially the left palm rest really feels a lot warm...warmer than how it feels on Win 7.

The bottom of the laptop feels a lot warm too....

Wierd thing is, even with RealTemp application (Win7) it states temperature at the same degree, but somehow the laptop feels much more warm to touch on Ubuntu.....

---

### Post by carl4926 on 2013-03-30
I'm on a eeepc ATM

```
kernelcruncher@kernelcruncher-1015PEM ~ $ sensorsacpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +100.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +23.0°C  (crit = +100.0°C)
Core 1:       +25.0°C  (crit = +100.0°C)



```

Feels..... is kind of subjective
I'm not saying you are imagining it. But if the sensors are suggesting all is well and there is no substantial evidence to the contrary.......

But I guess it's good to be careful

---

### Post by t430 on 2013-03-30
Hi Carl,

Thank you for sharing the details.

However, I do see that my Core 0 and Core 1 temperature is double than yours....I think that could mean that my laptop is getting way too hot.

I get the same readings on Ubuntu and Win 7, though. Is there some way to know what is a "good/decent" temperature for a laptop?

Is 45 C way to high?

---

### Post by Yellow Pasque on 2013-03-30
> **t430 said:**
> Is 45 C way to high?

45C is fine, but I'm assuming that's at idle, so it doesn't mean a whole lot. The real test is loading your CPU (use cpuburn or just watch a fullscreen Flash video) and then checking the temps.

---

### Post by carl4926 on 2013-03-30
Lenovo G550 running openSUSE 12.3 kde

```
acpitz-virtual-0Adapter: Virtual device
temp1:        +44.0°C  (crit = +119.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +40.0°C  (high = +105.0°C, crit = +105.0°C)



```

---

### Post by matt_symes on 2013-03-30
Hi

I would be happy with your temps.
```

matthew-S206:/home/matthew % sensors                                         
acpitz-virtual-0
Adapter: Virtual device
temp1:        +67.0°C  (crit = +98.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +68.0°C  (high = +70.0°C)
                       (crit = +115.0°C, hyst = +115.0°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +68.0°C  

matthew-S206:/home/matthew % 
```

Under some load though

```

load average: 2.20, 2.18, 2.16
```

Lenovo s206.

Kind regards

---

### Post by t430 on 2013-03-30
Hi Matthew,

Thank you so much.

I can breath a little easy now :)

Thing is, I mainly got this laptop to install VMWare and run 2-3 instances of Linux, and stuff on those lines...If I did that, the temperature would surely shoot up, so these temps had me worried.

Does your laptop feel unusually warm to touch ?

---

### Post by matt_symes on 2013-03-30
Hi

> **t430 said:**
> Does your laptop feel unusually warm to touch ?

Sometimes it does feel quite warm. Do do tend to either keep it on a table and, if it's on my lap, i keep it on an upturned tray to help ensure adequate air flow.

I would really not worry too much about the temps you are currently seeing.

They obviously will go up under load but i really only ever get worried about temps > 75 degrees C. That then is starting to run pretty hot.

Stress testing the graphics and CPU on my friend box saw temps getting pushed it to 90 and 85. Now that is getting hot !

CPU's are pretty robust nowadays and temp sensors are not always too accurate.

Kind regards

---

### Post by tgalati4 on 2013-03-30
So you are trying to run several virtual machines on a laptop?  That is normally a workload for a rack-based server.  And they have 7 fans that spin at 6,700RPM and go up to 15,000RPM and sound like a jet taking off.  

You can install* thinkfan *to better control the speed of your fan.  It's possible that your fan is cycling.  Check the fan controls in your BIOS--if any.  I have a thinkpad T43p and when compiling a kernel for 2 hours it does get toasty--70C.  As long as you don't see smoke and you are wearing asbestos pants, you should be OK.

---

### Post by t430 on 2013-04-13
Hi Matt and [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895"),

Sorry for the delayed reply. Office/Family kept me way too busy for past two weeks or so.

Thanks for your reply. I am glad that there's nothing unusual with my laptop.

Regards,

T430

---

