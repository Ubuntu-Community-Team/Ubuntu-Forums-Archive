---
title: "Accelerometer support for new HP Spectre 13 x2 tablet/laptop"
date: 2013-12-17
forum: Hardware
---

### Post by pgratz on 2013-12-17
I've been working through various issues with getting Kubuntu/Ubuntu installed on my new HP Spectre 13 x2 ([See my guide here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/")) with the generous help of the Ubuntuforums, and next on my list is getting the accelerometer working. 

On this one I don't really know where to begin.  No mention is made of the accelerometer in the DMESG and googling/forum searching has turned up nothing.  I tried manually loading the "hp_accel" module but that seemed to to make much difference.  No messages showed up in dmesg after that and I couldn't find any new devices in /dev/.  Does anyone have any ideas on how to get started on this?
Thanks!
Paul

---

### Post by Toz on 2013-12-17
Hi again.

I have an HP laptop with an accelerometer as well. [This document]("https://www.kernel.org/doc/Documentation/misc-devices/lis3lv02d") talks about the functionality of the device. Interesting that it can act as both a "freefall" interrupt device and a joystick. By default, it is recognized and functions as  joystick ("cat /var/log/Xorg.0.log | grep js0") using /dev/input/js0. **jstest-gtk** (from the jstest-gtk package) recognizes it and allows me to see its movements along the 3 axes. I haven't tested it as a joystick in a game though.

As for the device acting as a "freefall" interrupt device, running this command:
```
dmesg | grep accel
```
...yielded this message:
> [    2.883882] hp_accel: laptop model unknown, using default axes configuration
...and according to the documentation:
> If your laptop model is not recognized (cf "dmesg"), you can send an
email to the maintainer to add it to the database.  When reporting a new
laptop, please include the output of "dmidecode" plus the value of
/sys/devices/platform/lis3lv02d/position in these four cases.


I wonder whether its not working (or obviously not working - see "cat /sys/class/leds/hp::hddprotect/power/runtime_enabled" and "cat /sys/class/leds/hp::hddprotect/power/runtime_status"), is because its not part of the database. Unfortunately I never found the time to follow through with researching more on this device. Hopefully this will get you started.

---

### Post by coldraven on 2013-12-18
I was wondering the same when I got this HP five years ago. I do not think that the accelerometer is protecting the HDD but it is acting as a joystick.
Try installing "neverball" and you can steer the balls by tilting the laptop. Probably best done when alone or your friends will think that you've gone mad :)

---

### Post by pgratz on 2013-12-18
Thanks for the replys!

I think maybe the problem runs a bit deeper.  Here is the output from the suggested probes:
```

pgratz@pgratz-HP-Spectre-13-x2:~$ sudo modprobe hp_accel
pgratz@pgratz-HP-Spectre-13-x2:~$ sudo cat /var/log/Xorg.0.log | grep js0
pgratz@pgratz-HP-Spectre-13-x2:~$ dmesg |grep accel
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
pgratz@pgratz-HP-Spectre-13-x2:~$ 



```
(I'm pretty sure the grace-period thing has nothing to do with the accelerometer)
To me this looks like either it isn't identifying the accelerometer correctly or this one is not supported by hp_accel.

Just for reference, this is a laptop/tablet hybrid, what I'd love to get working is auto-rotation based upon orientation when in tablet mode (right now I'm doing something hacky with a key combination to force X to rotate).  It has an SSD so I'm not really concerned about the drop sensor aspect.
Paul

---

### Post by pgratz on 2013-12-19
A polite *bump*

---

### Post by Toz on 2013-12-19
Not sure what more I can add other than maybe suggest that you try getting a hold of the maintainer(s) and request that they add support for your device. From [https://www.kernel.org/doc/Documentation/misc-devices/lis3lv02d]("https://www.kernel.org/doc/Documentation/misc-devices/lis3lv02d"):
> Yan Burman <burman.yan@gmail.com>
Eric Piel <eric.piel@tremplin-utc.net>

---

### Post by pgratz on 2013-12-20
Thanks! I've emailed them.  So far no luck.  Doesn't sound like whatever the accelerometer is, its not supported by hp-accel/lis3lv02d.   Still trying to figure out what the chip is to see if we can go further...

---

