---
title: "[solved] Non-stop working fan. Amilo v2010."
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by mkor on 2005-12-06
Ubuntu 5.10 on Fujitsu-Siemens Amilo v2010 laptop.

The fan was behaving strange - was working all the time, until the cpu temp reached the first "trip point" (/proc/acpi/thermal_zone/THRM/trip_points). After that it worked properly - when the temperature dropped, the fan was turned off.

That was because after booting the system the fan state (/proc/acpi/fan/FN2/state) was "off", but it was turned on. It looks like the system didn't know that the fan was on. After reaching the first "trip point" the state was changed to "on" and from that moment the system had real information about the fan.

I added two commands to turn the fan "on" and then off as the last script in rc2.d:

```

echo 0 > /proc/acpi/fan/FN2/state
echo 3 > /proc/acpi/fan/FN2/state

```

And now it works perfectly - I don't have to "heat" the cpu to get the fan working properly when I turn on the laptop :D 

Helpful pages: 
[http://ubuntuforums.org/archive/index.php/t-77635.html](http://ubuntuforums.org/archive/index.php/t-77635.html)
[http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html)

==== Edited 08/12/2005 ====

However... I have just learned that when I reboot the laptop and the CPU is warm, the fan works ok. Then, my script turns off the fan - when the CPU's temperature is above the first "trip point". And the fan is off till the next event, which is the second "trip point" - 60 C.

So, my script has to be more intelligent... Maybe during the weekend I will find some time to work on it...

---

### Post by frontline3k on 2005-12-07
Hey, this solves the problem to my Fujitsu Siemens M7440 ([http://ubuntuforums.org/showthread.php?t=96624](http://ubuntuforums.org/showthread.php?t=96624)).

Thanks.

---

### Post by mkor on 2007-05-21
I have just installed Ubuntu 7.04 and it is still not solved. Does anyone know what to do to solve it at "distribution" level?

---

