---
title: "Acer Aspire 3810t Timeline fan always spinning"
date: 2009-12-26
forum: Hardware
---

### Post by qnano on 2009-12-26
Hi,

I have a dual partition (Vista/Karmic) on an Acer Aspire 3810t Timeline (Intel Core 2 Solo SU3500 -1.4 Gh) laptop. There seems to be a problem with the fan speed, I have noticed that the fan is almost constantly spinning, particularly as soon as I open a new programme, much more than under Vista, to the point of being annoying even though temperatures don't seem to be high. 

I installed "CPU Frequency Monitor" on the Gnome panel, through which it is possible to alter the frequency operation of the Centrino mainboard. It is by default set to "ondemand", but changing it all the way up to 1.4 GHz does not make a difference in terms of the fan spinning. 

I then installed the "Sensors" applet to check temperatures. The Core0 temperature always hovers around 41 C, which is in my view pretty low for the fan to constantly keep spinning. I then ran "pwmconfig" to receive an error message
 " There are no pwm-capable sensor modules installed"

My kernel is 2.6.31-16-generic.

Anyone with a similar problem or a solution, please share!

---

### Post by gabriele962 on 2010-04-26
Hi,

I have the same problem, fan is always on and temperature around 41 degree forever without running process. In this condition the battery duration is pretty low compared to windows (4-5 hours)

In the same state, with Windows7, the temperatur is around 35 degree, the fan is in very low status and also the battery is more durable, around 7 hours.

---

### Post by mr bob on 2010-04-27
Which BIOS version do you have? If it is 1.20 or higher it seems to keep the fan spinning.

I reverted back to 1.17.

See the main 3810t thread for details.

---

### Post by salsa2010 on 2010-05-11
> **mr bob said:**
> Which BIOS version do you have? If it is 1.20 or higher it seems to keep the fan spinning.

I reverted back to 1.17.

See the main 3810t thread for details.

same problem, no solution... Downgrading from 1.2 to 1.17 did not help... :confused::confused:

---

