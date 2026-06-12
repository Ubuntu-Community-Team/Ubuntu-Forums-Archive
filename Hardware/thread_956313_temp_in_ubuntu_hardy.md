---
title: "temp in ubuntu hardy"
date: 2008-10-23
forum: Hardware
---

### Post by jrecortel on 2008-10-23
hello.i would like to ask if the overheating problem on laptop is resolved in ubuntu 8.04.i've searched the forum and encountered
[http://ubuntuforums.org/showthread.php?t=539365](http://ubuntuforums.org/showthread.php?t=539365)
my question is do i still need to apply the fix that this site recommend or is the overheating problem already solved in hardy?im using compaq presario v3901tu and i would like to safeguard it against overheating.thanks in advace.
btw, running acpi -t display about 40-45C on both CPU's.is this the normal temp for CPU's?i dont know how i can monitor the HD temp.on my touch, its very warm.

---

### Post by ThaRabbit on 2008-10-23
you can monitor temperature in several ways, the quickest would be to install the gnome panel applet:
[img]http://micampe.it/screenshots/sensors-applet-thinkpad.png[/img]

It will display the temperature readouts in your gnome panel like so:
[img]http://wolfgang.lonien.de/wp-content/uploads/2006/07/gnome-sensors-applet.png[/img]

40-50 is fairly normal, depending on what system you have. Shouldn't have to go over 50 though.

---

### Post by jrecortel on 2008-10-23
thank you ThaRabbit.im just wondering how can i install the app.im just a new linux user and im not that familiar yet about the system.

---

### Post by ThaRabbit on 2008-10-23
> **jrecortel said:**
> thank you ThaRabbit.im just wondering how can i install the app.im just a new linux user and im not that familiar yet about the system.

The best way then, for you, would be to use synaptic.

It's a graphical tool that lets you search the applications premade for your ubuntu by the ubuntu team.

System -> Administration -> Synaptic Package Manager

Use the search function and search for "sensors-applet"

Click the tickbox in front of the application and select install. It will automatically sort out other requirements for you :)

When that is all done and installed, you can right click your gnome taskbar and "add to panel". The sensors applet should be listed :)

---

### Post by jrecortel on 2008-10-23
just installed sensors-applet.i can now monitor the cpu temp but unfortunately not my hdd temp.is there something im missing or is it just my laptop has no temp sensor for my hdd.also, no monitor for fan speed.

---

### Post by ThaRabbit on 2008-10-23
> **jrecortel said:**
> just installed sensors-applet.i can now monitor the cpu temp but unfortunately not my hdd temp.is there something im missing or is it just my laptop has no temp sensor for my hdd.also, no monitor for fan speed.

The sensors-applet package uses hddtemp to read-out hdd temperatures, as mentioned in the description of that package:

> Display readings from hardware sensors in your Gnome panel
GNOME Sensors Applet is an applet for the GNOME panel that displays
readings from hardware sensors, including temperatures, fan speeds and
voltage readings.

It can gather data from the following sources:
 * ACPI thermal zones, via the Linux kernel ACPI modules
 * Linux kernel i2c modules
 * lm-sensors (libsensors)
 * Linux kernel i8k module (for Dell Inspiron Laptops)
 * Linux kernel ibm-acpi module
 * Linux kernel PowerPC modules therm_adt746x and therm_windtunnel
 * Linux kernel iMac G5 Windfarm module
** * hddtemp daemon for reading temperatures from S.M.A.R.T. equipped hard disks**
 * Linux kernel Omnibook module
 * NVIDIA graphics cards
 * Linux kernel sonypi module (for Sony Vaio laptops)

Alarms can be set for each sensor to notify the user once a certain high or
low value has been reached, and can be configured to execute a given command
at given repeated intervals.

so to enable hdd temperature read-out. Go back to Synaptic and look for the package "hddtemp"

Install, reboot and check the applet configuration again :)

---

### Post by jrecortel on 2008-10-23
thanks again ThaRabbit.i can now monitor my hdd temp.:)
really appreciate your help.
but i still have a question if you dont mind.how can i monitor the fan speed?

---

### Post by jrecortel on 2008-10-23
i would like to ask how can i monitor the fan speed.already installed libsensors but there still no fan monitor.help please.

---

### Post by ThaRabbit on 2008-10-24
You're welcome :)

> **jrecortel said:**
> i would like to ask how can i monitor the fan speed.already installed libsensors but there still no fan monitor.help please.

You might need to configure things, please use and follow this command:

```
sudo sensors-detect
```

It will detect and offer to load the required modules for sensors detectable in your system.

---

