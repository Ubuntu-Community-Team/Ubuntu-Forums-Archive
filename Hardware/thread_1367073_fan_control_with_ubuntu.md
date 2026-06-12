---
title: "fan control with ubuntu?"
date: 2009-12-29
forum: Hardware
---

### Post by v1nsai on 2009-12-29
I just put Ubuntu 9.10 Karmic on my new Dell Studio 15, and I've noticed that it keeps my fan off until my CPU reaches around 60 degrees Celcius, which I think is a little close to too hot, so I'd like a way to switch the fan on and off on my own.

I've found a lot of topics on this, but most of them point to threads like [this]("http://ubuntuforums.org/showthread.php?t=230673") and [this]("http://ubuntuforums.org/showthread.php?t=42737") which have a lot of info, but are pretty dated.

Could anyone confirm that these old threads are safe and *might* work or point me to a more recent way to control the fans?

---

### Post by v1nsai on 2009-12-30
This has been a difficult topic to find information on, I'm guessing a lot of it is hardware-dependent so finding general instructions are difficult.

Is there something on my system I could look up to find more specific information for my setup?  I'm not even sure what controls the fans, I don't know what I need to be looking for.

Most of the threads I've found have been for controlling fan speed, but I'm really just interested in controlling whether the fans are on or off, I just don't like it getting so hot before the fans turn on.

---

### Post by sarthorks on 2009-12-30
This ACPI HowTo, although a little outdated (i think) is still pretty helpful and a good place to start things.

Go through [this]("http://www.columbia.edu/~ariel/acpi/acpi_howto.html") and [this section]("http://www.columbia.edu/~ariel/acpi/acpi_howto.html#thermal_management") in particular, for the Thermal Management bit.

---

### Post by v1nsai on 2010-01-01
Cool, I'll start picking through that when I can.  

I wanted to re-phrase my question a bit.  I'd like to let Ubuntu control the fan, but I just want to lower the threshold for when the fan kicks on to a lower temperature.

I just think 60 celsius is a little hot, or does this sound ok and normal to anyone?

---

### Post by v1nsai on 2010-01-01
Thanks, that was extremely helpful!

In the article, the author says that he/she had never seen more than one cooling zone in /proc/acpi/thermal_zone but I've got three (TZ00-TZ02).  The contents of these folders seem to be identical so if I make any changes I'll probably just change all three (would replacing the contents of two folders with symlinks be a bad idea here?)

My cooling_mode isn't set, echoing to it returns directory not found, so maybe BIOS is controlling my fan?  I haven't found anything in there about it though.  Also, I'm not able to make any modifications to these files, it complains this is on a read-only disk, so where's the control file?

If I wanted to make the fans come on at 50C, would I add an entry to trip_points something like:

```
active: 50C
```

---

### Post by v1nsai on 2010-01-18
I've been doing some more research on this, and I realized that the reason I have more than one TZ is because that's just the generic name given to each zone.

So anyway, my next problem is that it doesn't seem like linux is using active cooling.  When I look at any of my trip_points files, all they contain is 'critical (S5):           100 C'.  The way I understand it if my system were using active cooling I would have a line that looks something like the one I posted above.

---

### Post by Ross86 on 2010-01-18
I'm a total Ubuntu novice and I don't know how to even change the directory's as instructed above...how is this done? through the terminal?

Is there any idiots guide to changing the fan settings?

I've got an ACER 5315 and the overheating is getting beyond a joke, operation of the fan just seems to be completely random!

Any help would be greatly appreciated :D

---

### Post by Gatorade on 2010-01-18
I've been trying to find an easy way to do this as well.

I've got a dell d620 and it sometimes gets up to 70 degrees before the fan comes on, and even then it only stays on for a short period.

I'd like to be able to set the thresholds myself.

---

### Post by argosreality on 2010-01-18
> **v1nsai said:**
> I've been doing some more research on this, and I realized that the reason I have more than one TZ is because that's just the generic name given to each zone.

So anyway, my next problem is that it doesn't seem like linux is using active cooling.  When I look at any of my trip_points files, all they contain is 'critical (S5):           100 C'.  The way I understand it if my system were using active cooling I would have a line that looks something like the one I posted above.Well, looks like there was a bug possibly in the kernel relating to how the Dell Studio laptops handle ACPI [https://bugs.launchpad.net/linux/+bug/392812]("https://bugs.launchpad.net/linux/+bug/392812") which should be fixed in either 10.04 or else kernel 2.6.31-17. Granted, most of this post deals with lid closing and hotkeys but there are thermal management issues discussed as well.

Looks like there might be another regression related to it in 2.6.32 as well ;) [http://bugzilla.kernel.org/show_bug.cgi?id=14667](http://bugzilla.kernel.org/show_bug.cgi?id=14667)

---

### Post by argosreality on 2010-01-18
> **Gatorade said:**
> I've been trying to find an easy way to do this as well.

I've got a dell d620 and it sometimes gets up to 70 degrees before the fan comes on, and even then it only stays on for a short period.

I'd like to be able to set the thresholds myself.Have you tried using the i8kfan software? Specifically mentions support for your model [http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html) (Not studios though)

---

### Post by Gatorade on 2010-01-19
I'm using Ubuntu 9.04 , the only thing I saw for linux is written for debian.

"Fan control for other operating systems

   1. A FreeBSD/NetBSD/OpenBSD version of the original DOS i8kfan command line tool ported to *BSD by Damir Lampa (unfortunately the link is dead)

   2. Since Linux kernel 2.4.15 there's also a kernel module written by Massimo Dal Zotto to get access to the important SMM functions under Linux. The tools to access that driver are here:

      [http://www.debian.org/~dz/i8k/](http://www.debian.org/~dz/i8k/)

   3. Here's a daemon called dellfand specifically for the linux 2.6 kernel series:

      http://dellfand.dinglisch.net/"


or the dellfand , but I don't know if I've got the right kernel "2.6 series"

---

