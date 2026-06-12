---
title: "ACPI not firing off /etc/acpi/battery.d/* when unplugged from AC?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by neptho on 2007-06-08
Greetings, all.

I've read the myriad of FAQs (although probably missed a couple), and have figured pretty much everything out that I have needed to get my aging Inspiron 6400 working with Feisty Fawn (7.04), however:

When I unplug my system from AC, I get the nice 'Running on battery' alert, but it does not seem to execute any scripts in /etc/acpi/battery.d/ ; I have one I have created that will run aticontrol to set the refresh rate lower, and save a trivial amount of battery life (all are chmod 755, root:root):

**/etc/acpi/battery.d/20-ati.sh**:
#!/bin/sh
PATH=/bin:/usr/bin
/usr/bin/aticonfig --set-powerstate=1

And, of course, it's brother: 

**/etc/acpi/ac.d/20-ati.sh**:
#!/bin/sh
PATH=/bin:/usr/bin
/usr/bin/aticonfig --set-powerstate=3

I've also created the following, as I saw no 'ac.sh', nor 'battery.sh':

**/etc/acpi/ac.sh**:
ac.sh 
#!/bin/sh
for n in /etc/acpi/ac.d/*; do
  "$n"
done

**/etc/acpi/battery.sh**:
ac.sh 
#!/bin/sh
for n in /etc/acpi/battery.d/*; do
  "$n"
done

Am I missing something?

Cheers!

---

### Post by neptho on 2007-06-08
I've found what I was looking for; the events are in /etc/acpi/events/(ac, battery), which call /etc/acpi/power.sh

However, ACPI does not seem to be firing off /etc/acpi/power.sh.  When I run /etc/acpi/power.sh manually, both with, and without AC, it works as expected. However, just unplugging the unit does nothing.

I've attempted to set checkpoints/breaks in /etc/power.sh by using logger to write to syslog, but nothing ever happens.

I've checked my /etc/defaults/acpi again, and it's fine.  ACPI is registering activity in /var/log/acpid.

I'm stumped.  What am I missing? :)

---

### Post by neptho on 2007-06-08
Ok, so I've got it figured out, finally.

For some reason power.sh is not infallable; it attempts to grep for the offline state too fast, it spawns before it's completely registered, so /etc/acpi/ac.d/* run for me in battery mode a good portion of the time.  I've personally broken out /etc/acpi/events/ to use two scripts now for battery and ac, but if you just want to have it automatically drop the screen refresh, this should do, even though it's not "the right way to do it": 

**/etc/acpi/ac.d/20-ati.sh**:
```
#! /bin/sh
for x in /proc/acpi/ac_adapter/*; do
    grep -q -i off-line $x/state
    if [ $? = 0 ] && [ x$1 != xstop ]; then
        /usr/bin/aticonfig --set-powerstate=1
    else
        /usr/bin/aticonfig --set-powerstate=3
    fi
done
```

I've added a variable 'ENABLE_CPU_SPEED' to my /etc/default/acpi-support to test for, and execute this script only if I want it on.  It can be annoying to force a drop between 800Mhz and 1.6Ghz

Note that I really lamed out for the automatic CPU scaling; I hardcoded the fields for 'high' and 'low' for my system.  You can see what your available fields are with 

'cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies '

**/etc/acpi/ac.d/45-cpu.sh**:

```
#! /bin/sh
. /etc/default/acpi-support
if [ $ENABLE_CPU_SPEED"x" = "truex" ]; then
PATH=/bin:/usr/bin
for x in /proc/acpi/ac_adapter/*; do
    grep -q -i off-line $x/state
    if [ $? = 0 ] && [ x$1 != xstop ]; then
        SPEED=`cut -f4 -d" " /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies`
    else
        SPEED=`cut -f1 -d" " /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies`
    fi
        /usr/bin/cpufreq-selector -f $SPEED
done
```

---

