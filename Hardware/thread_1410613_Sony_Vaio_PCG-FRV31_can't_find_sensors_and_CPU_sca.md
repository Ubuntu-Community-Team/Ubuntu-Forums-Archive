---
title: "Sony Vaio PCG-FRV31 can't find sensors and CPU scaling not working"
date: 2010-02-18
forum: Hardware
---

### Post by 2ways on 2010-02-18
Hi Folks,

I have a Sony Vaio PCG-FRV31, 2.4 GHz Celeron, 1 GB RAM, 40 GB HDD and am running 9.10 Karmic.

My laptop is overheating badly, and, as a result, is running extremely slowly, which is probably a Sony issue, but to get a handle on what is really happening, I've been trying to find temperature and fan sensor information.

I've been through the How To at [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780), which was really helpful, but still have some questions (not to mention I could cook an egg on this thing right now).

When I run sensors-detect the result is that it finds no sensors.

> Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.In the process, it told me that it needed two drivers, but that they were already loaded.
i2c-ali15x3
i2c-ali1535

Running sensors then, gets me nothing.

Not being deterred, I added those two drivers manually to /etc/modules, and tried again.

running sensors now gets me:

> lewis@Asa:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +85.0°C  (crit = +90.0°C)  Interesting.  Note the temp!

Then I added xsensors to see if that might give me more information, but it comes up blank.

The strange thing is that I added some hardware monitoring app in the top panel (right-click on the top panel, select 'add to panel', etc.), and that does show something.  In fact, it shows a temperature for 'temp1', which I found from lm-sensors, but also shows a CPU temperature from acpi (currently running at 25 degrees over the critical temperature!).

The Sony part number for the motherboard is A8068048A, but I can't figure out who makes it and there doesn't seem to be any information about how to make ubuntu detect the sensors on that motherboard.  A replacement part number for it is MBX-88 JE 12, but I'm not sure that means anything.  Still can't find any helpful information about it.

I thought perhaps the overheating was related to ubuntu not being able to control the CPU scaling properly.  Any thoughts on that?

I tried to add the CPU Frequency Scaling Monitor to the top panel as well, but was told it was not supported, as below:

> You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.Anyway, I'm still guessing I've got lots of dust stuck in the back of this laptop that is making it overheat, but the overheating problem increased many-times over when I switched to ubuntu, so I thought it might be partially related to ubuntu as well.

On top of that, I still want to be able to read sensor info from the Sony.  Both temperatures I can read right now are at 85!

Thanks for the help.

---

