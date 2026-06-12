---
title: "Fan speed control script"
date: 2009-11-09
forum: Hardware
---

### Post by ScottHW on 2009-11-09
I have been using a simple script to allow manual control for the fan on my Gateway M275 laptop.  Credit for the script goes to ***newfangled***.  Full history here:
**Gateway M275 Tablet laptop with Ubuntu Hardy Heron (8.04.1)**
[http://ubuntuforums.org/showthread.php?t=984634](http://ubuntuforums.org/showthread.php?t=984634)

Here's the script:
> #!/bin/sh

fan0status=$(grep "status:" /proc/acpi/fan/FAN0/state |awk '{print $2}')
fan1status=$(grep "status:" /proc/acpi/fan/FAN1/state |awk '{print $2}')

case "$fan0status" in

off)
echo -n 0 > /proc/acpi/fan/FAN0/state
;;

on)
case "$fan1status" in

on)
echo -n 3 > /proc/acpi/fan/FAN0/state
echo -n 3 > /proc/acpi/fan/FAN1/state
;;

off)
echo -n 0 > /proc/acpi/fan/FAN0/state
echo -n 0 > /proc/acpi/fan/FAN1/state
;;
esac
;;
esac 

I had the script saved in */usr/local/bin/fanspeed*, with a Launcher (Application) on my Panel.  A single click would allow me to rotate through three fan settings.  I used sudoers to allow permissions for the script so I wouldn't have to type the password every time.

Thing is, now that I've upgraded, the script doesn't work any more.  I am certainly not a Ubuntu expert, but I've tried to figure out what the deal is.

I double-checked the sudoers file to make sure that the permissions I had previously set should still work for the script.

I believe the script is running, although not accomplishing the objective of alternating the fan speed.

I tried to manually enter the echo lines into a terminal
```

scott@gateway:~$ echo -n 0 > /proc/acpi/fan/FAN0/state
bash: /proc/acpi/fan/FAN0/state: Permission denied
scott@gateway:~$ sudo echo -n 0 > /proc/acpi/fan/FAN0/state
bash: /proc/acpi/fan/FAN0/state: Permission denied

```
But I can't honestly say I remember ever trying this before upgrading, so I don't know if this response is unique to my upgrade.

Any ideas as to why this may have stopped when I upgraded to Karmic?  Other relevant details available on request.

---

### Post by ScottHW on 2009-11-09
Are there major changes in Karmic related to sensors, ACPI, or the like?

I can't seem to figure out what exactly is keeping this script (or the commands) from working like they used to.

---

### Post by ScottHW on 2009-11-09
I know I also tried to run the same commands as root
```

sudo su
root@gateway:~$ echo -n 0 > /proc/acpi/fan/FAN0/state

```
And while the commands seemed to work, nothing happened to the fan.

Is it possible that the fans aren't being controlled the same way they used to be?

---

### Post by presence1960 on 2009-11-09
I can tell you that the sensors in gkrellm do not read the same in karmic as they did in Jaunty.  So it may be a change in karmic that is the root of the problem.

---

### Post by ScottHW on 2009-11-09
Interesting, thanks for the info, presence1960. I'll have to look more into that.

---

### Post by ScottHW on 2009-11-10
Here's someone else trying to control fanspeed 

**[ubuntu] Reading sensors and doing fancontrol in Karmic**
[http://ubuntuforums.org/showthread.php?t=1321293](http://ubuntuforums.org/showthread.php?t=1321293)

From that, I now realize that Karmic also comes with the new kernel, 2.6.31, and that the problems could be there somewhere.

---

### Post by ScottHW on 2009-11-10
Here's another one that may be useful

**HOWTO: Fancontrol**
[http://ubuntuforums.org/showthread.php?t=250025](http://ubuntuforums.org/showthread.php?t=250025)

'course, this original post is from Sept 2006.  But the last post summarizes pretty nicely:
> **Nerevar144 said:**
> This is a good howto, just it's out-dated.  Just install lm-sensors then reboot and run pwmconfig.  DO NOT CHANGE YOUR fancontrol FILE!  Reboot and it will be automagically loaded.  Presto!

And just in case, I've attached a PDF of the original How-To

---

### Post by skiMJ on 2009-11-19
[QUOTE=ScottHW]Are there major changes in Karmic related to sensors, ACPI, or the like?
...
[http://ubuntuforums.org/showthread.php?t=1321293](http://ubuntuforums.org/showthread.php?t=1321293)[/QUOTE]

Yes, doing some reading in that thread and links, I see that the the new kernel does strict resource enforcement that it didn't do before. ASUS motherboards seem to commonly have some resource conflicts.

These can be fixed by using new drivers such as asus_atk0110 but this requires lm-sensors 3.1 which isn't in karmic yet. You can build it yourself or use someone else's build of lm-sensors (see [https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418))

It's not the "proper" fix but in the interim you can add "acpi_enforce_resources=lax" to the boot command line and this will revert the ACPI behavior back to the old (wrong) way.

See also:
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

---

### Post by christopherreay on 2010-01-11
It is extremely normal to come up against problems which seem stupid. Changes, etc. If you are going back to legacy ways of doing things, it is probabaly because there is a new way of doing it.

Try checking out this post:
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

> AND... after 20 minutes or so reading files, you will find:

"# Use the variables to override the temperature trip point settings exported
# by BIOS (in degree Celcius).
# The number in the end defines the thermal zone for which the value should
# be active. Use the powersave -T command to find out supported thermal zones
# and their default trip point settings. A value of 0 will be ignored.
# Active trip points are not supported at the moment as fans cannot 
# be controlled over ACPI on most machines.
"
Aaaa ahahahahahaaaa

---

