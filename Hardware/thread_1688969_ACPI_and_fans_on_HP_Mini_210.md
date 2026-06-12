---
title: "ACPI and fans on HP Mini 210"
date: 2011-02-16
forum: Hardware
---

### Post by markqvist on 2011-02-16
Hi all ):P

After a bit of twiddling, Ubuntu 10.10 is running beautifully on my HP Mini 210. One thing I can't seem to get my grips on though, is the fan control. In the beginning, ACPI was totally helpless, couldn't even read battery rate information and such. A BIOS update seems to have solved this (it was running F.02 and is now running F.14).

While there was absolutely no control of the fan on the old BIOS (it was running quite loudly ALL the time, annoying), things have helped now. There is a distinct difference between the speed at startup and after the system is fully booted.

But what is actually managing this? It doesn't seem like it's ACPI. There's nothing in /proc/acpi/fan. The command "fancontrol" just gives:

```
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
```

Running "acpi -c" (for cooling device information, according to man) gives this though:

```
Cooling 0: LCD 10 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
```

Which leads me to believe that ACPI does see _something_. But maybe I'm totally wrong :P

Also, when running "sensors-detect", one interesting part seems to be:

```
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8502
```

Which, in my extremely limited knowledge about this stuff, makes me think that this could be some kind of control chip that is just not supported yet.

Also, I removed the back cover from the computer to have a look, and I think that the fan is maybe on the GPU actually? (it's a Intel GMA 3150)

The bottom line is, that I'd really like to be able to mess around with my fan speeds myself, and that I have no clue about where to do this. Or whether my system is in reality able to manage them at all.

Aaar, the confusion! If anyone can give me any pointers, it'd be much appreciated!

Cheers!

Mark

---

### Post by jerrrys on 2011-02-17
well you are right. its not there (etc).  it is in sbin, but still can't do anything with it.  maybe you can find something useful here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+adjust&as_qdr=all&sa=Google+Search&lang=en#894](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+adjust&as_qdr=all&sa=Google+Search&lang=en#894)

---

### Post by InNeedOfAnswers on 2011-03-23
I installed Ubuntu 10.10 on a new HP Mini 210-2072CL.  Everything installed properly except for the fan sensor.  Now the fan is oscillating from on to off constantly.  I searched for solutions everywhere but did not find anything.  It seems that sensors don't pick up the fan controller since I only see CPU's and their temperature, but no fan.  Any help is appreciated.  I can provide all information if needed.

---

