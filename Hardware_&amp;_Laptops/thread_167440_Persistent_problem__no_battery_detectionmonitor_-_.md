---
title: "Persistent problem:  no battery detection/monitor - Vaio PCG-k13"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by mlaverdiere on 2006-04-28
Hi to all,

I'm using Ubuntu Dapper on a Sony Vaio PCG-K13Q and, like many laptop users, I 'm not able to have my battery correctly detected and monitored.  The strange (and  a bit frustrating) thing is that I never had this problem on this laptop with other distros (all Debian based, i,e,: Debian sid, Knoppix, Morphix etc.) that I've used.  It seems to be a Ubuntu particular thing, maybe related to a kernel patch or a tweak that I have not been able to pinpoint yet.

Heres' the situation:

In fact, my battery is sometimes detected at boot and then after, everything is OK.  However, most of the time (2/3 of the times), it is not detected and the KDE/gnome applet and the acpi -V command indicate that there is no battery at all.  The dmesg command gives me this:   ACPI: Battery Slot [BAT1] (battery absent).  Also, if I remove and insert the battery when the system is booted up, then it is detected and everything works fine.

I've tried the following procedures, without any positive results:

- fixing my DSDT (following [https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29](https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29))
- using different kernel boot parameters (i.e. acpi=force, acpi_os_name=..., nopapic, nolapic, etc.) 

Someone has an idea of what's going on and what could be done to fix this thing?

Thanks in advance for your help.

---

### Post by mlaverdiere on 2006-04-29
Hi,

I've found one solution (well, a workaround...), and it's quite simple:  no need to play with DSDT file (like it was suggested in [https://wiki.ubuntu.com/ACPIBattery?...ght=%28acpi%29](https://wiki.ubuntu.com/ACPIBattery?...ght=%28acpi%29), etc.), to compile a kernel or to do some other relatively complex procedures

It seems that if I unload and reload the "battery" module, everything works fine after.  But before unloading the battery module, you have to unload the smart battery module, listed as "acpi_usb" with the lsmod command.


_**How to determine if this solution works for you:**_

To try this solution, do the following:

Open a terminal, and enter the following commands:

sudo rmmod acpi_sbs
sudo rmmod battery
sudo modprobe battery

Then, enter this command:
sudo acpi -V

if you see someting like this:

Battery 1: charging, 100%
Thermal 1: ok, 56.0 degrees C
AC Adapter 1: on-line

Then, voila, your battery is now detected and monitored and you now know that this solution works for you

If you don't see any reference to the battery after issuing acpi -V, the problem may be more complex.  See:  [https://wiki.ubuntu.com/ACPIBattery?...ght=%28acpi%29](https://wiki.ubuntu.com/ACPIBattery?...ght=%28acpi%29)


_**Fixing the problem in a permanent way:**_

I have created special init scripts that I put in /etc/init.d and /etc/acpi/resume.d in order to unload-reload battery module at each boot and resume after hibernation.

In a more detailed way, here's what I did and what you can do (at your own risk!):

1.  Using a text editor, put the following content in a file and save it:

#!/bin/bash
rmmod acpi_sbs
rmmod battery
modprobe battery

2. Make a copy of this file, name it  "modules-load-battery", make it executable (in a console, you can use the command "sudo chmod a+x modules-load-battery") and put this file in /etc/init.d  

3.  Use the Ksysv editor (or whatever it is called in K menu/system or in the "System settings"/System Administration/System services), in order to make this script run at each boot time (you can make it run just before the "kdm" script; it works for me).

4. Make another copy of this file, name it  "37-modules-load-battery.sh", make it executable (in a console, you can use the command "sudo chmod a+x 37-modules-load-battery.sh"), and put this file in /etc/acpi/resume.d; it will run at each resume from hibernate state.


Hope this helps.

---

### Post by dksdk on 2006-04-30
could you please detail how to write a init script and how to make it load on boot.
thanks in advance

---

### Post by mlaverdiere on 2006-04-30
Hi,

I was partly wrong in my first version of the 2nd message regarding the cause and the solution of the problem.  The "acpi_sbs" module is not really the cause of the problem.  It's just that in order to unload the "battery" module, you have to unload the "acpi_sbs" module first.  Anyway, the unload-reload of the "battery" module make the battery detection/monitoring works for me.

I have reedited the 2nd message to avoid any misleading info and I put more details on how to make scripts to do the unload-reload thing at boot and at resume time.

Hope this will be helpful for you.

---

### Post by kwicky21 on 2006-10-16
Hi, sudo acpi -V seems to give me this message always:

```
No support for device type: thermal

```

Regardless of wether I "reload-unload" the battery or not. I wonder what seems to be the problem here?..

---

### Post by mrmoney on 2008-03-06
I have the same issue "No device type: thermal"

My computer runs fine off the battery, but I have no way of knowing what the charge. Any help is greatly appreciated

---

