---
title: "Battery status problems"
date: 2008-11-07
forum: Hardware
---

### Post by carens on 2008-11-07
I installed Ubuntu 8.10 on my HP ZE2000 series laptop yesterday. Everything seems to work fine except for the battery status.

**Power management icon**
When on AC power the status is always: "Computer is running on AC power. Laptop battery discharging (0,0%)". When running on battery: "Computer is running on battery power. Laptop battery discharging (0,0%)". The icon always looks the same (though sometimes with a plug overlay on it, but not always when plugged in).

**acpi -V**
Shows similar info as the power management icon, i.e. always discharging. Though once or twice it did show "charging" too.

**cat /proc/acpi/battery/BAT0/info**
On my battery it says 10.8 V, 4.4 Ah. In the info stats it says "design capacity: 6000 mAh" and "design voltage: 14800 mV".

In Windows XP everything seems to work fine. How do I fix my Intrepid install?

---

### Post by NeeBone on 2008-11-07
Same issue. Was fine in 8.04 but upgrading to 8.10 killed it.

In fact, i upgraded to 8.10 during the alpha (i know..sshhh!) It was upgrading to the beta that nuked battery reporting.

Incidentally, i recently had a lot of screen flicker and half the screen would occasionally go dim. I thought it was a power issue until I ended nuking my xorg.conf by mistake. Rebuilt it (including reinstalling the nvidia drivers) and its working ok now.

So I'm thinking the battery issue is some sort of config malfunction but I'm not sure what. Works fine in Vista (dual booted for testing).

HP dv6375us

---

### Post by iosif on 2008-11-09
I think I may have a similar problem.  The Battery Charge Monitor on my upper panel displays 34.9% charged and charging on AC power, but if I left-click on the Battery Charge Monitor, it shows "Laptop battery" at 100%.  There are also discrepancies when the Monitor shows, for example, 70% charged on battery and then immediately drops to 4% charged, opens a warning message, and then shuts the computer down.  What's the deal?

EDIT:
Or maybe my battery is just dying.  Nevermind.

---

### Post by PsyWolf on 2008-11-29
i'm having similar problems.  I listed them in detail in my post [http://ubuntuforums.org/showthread.php?p=6273128#post6273128](http://ubuntuforums.org/showthread.php?p=6273128#post6273128)

anyone found any fixes yet?

---

### Post by tommcd on 2008-11-29
Some troubleshooting:
1.Run **lsmod** in terminal. Make sure the modules **ac** and **battery** are running. If not, load them with "sudo modprobe ac", and "sudo modprobe battery".
Other modules you may need are: fan, processor, thermal and button. Check to see if they are running also. If not, modprobe them.

2. Try loading the gnome battery monitor. Right click on 1 of the panels, choose "add to panel". Select "Battery Charge Monitor". See if that one works any better for you.

---

