---
title: "BIOS clock"
date: 2015-10-27
forum: Hardware
---

### Post by mayagrafix on 2015-10-27
When I boot Ubuntu, the OS resets the BIOS clock from local time to Zulu time. How can I keep the BIOS clock set to local time instead?

---

### Post by Bashing-om on 2015-10-27
mayagrafix; Hello again .

Dual booting with Windows, such that Windows controls the hardware clock ?
If so there is edit that will resolve the situation.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2015-10-27
Is this a dual boot machine?  If so, then there is a switch in Windows to not store local time when shutting down. Linux uses UTC in BIOS and then uses */etc/timezone* to present local time on the desktop.  If you want to change this behavior, then you have to use a fake timezone.

---

### Post by VMC on 2015-10-27
```
grep UTC /etc/default/rcS
```

I have your problem whenever its set to UTC=yes.

---

### Post by mayagrafix on 2015-10-27
I remember on install choosing to have hardware clock set to UTC. Is there a way to undo?

---

### Post by mayagrafix on 2015-10-27
The time works AoK in Ubuntu. However, when I boot Windows OS it shows wrong local time. As long as I do not boot Ubuntu, Windows OS clock maintains correct local time.

---

### Post by mayagrafix on 2015-10-27
Procedure to Synchronize the System Time to Hardware Clock
This is a one-time procedure to ensure that your hardware clock's time zone is correctly and consistently recognized by all the Linux installations you multiboot on a single machine.
Assuming you are dual-booting Distro X and Y, first boot into Distribution X. First check the hardware clock with the following command.
 hwclock --show    
If your hardware clock is not set to your local time, then you must set the system time to local time. As root,
Update via NTP:*If you installed the ntp package you can:*
   ntpdate pool.ntp.org
-or-*
Manual update:*
   date --set "5 Aug 2012 12:54 IST"
Obviously in the above command you must set your date, time and time zone correctly.
Now as root, synchronize the hardware clock to the current system time as local time.
 hwclock --systohc --localtime
Now the hardware clock is readjusted to the system time and both now point to the local time.
Obviously there are other ways to achieve the same effect, but this process is least likely to confuse as you set initial time inside the Operating System and then adjust the BIOS clock accordingly.
Now boot into Distro Y and follow the same steps as above. It doesn't matter that the hardware clock is now set correctly, you can still reset the clock once to make sure that every distribution you multi-boot recognizes the hardware clock as set to the local time.


Syncing to UTC instead of Local Time
Some people prefer setting their hardware clock to UTC (Universal Coordinated Time) instead of local time. If you want to set your hardware clock to UTC and adjust the date/time accordingly, use the above steps but simply change the*hwclock*command to
 hwclock --systohc --utc
while setting the hardware clock from your system time.
Be consistent in time settings across Operating Systems when you dual boot. If you use different settings in different Operating Systems, your local time will be messed up.
Sources


<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>

Make Linux use 'Local' time
To tell your Ubuntu system that the hardware clock is set to 'local' time:
1. edit /etc/default/rcS
2. add or change the following section
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no

---

### Post by mayagrafix on 2015-10-27
> **Bashing-om said:**
> **mayagrafix; Hello again **.

Dual booting with Windows, such that Windows controls the hardware clock ?
If so there is edit that will resolve the situation.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

Saludos, compadre :)

---

