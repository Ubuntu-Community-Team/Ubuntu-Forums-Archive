---
title: "Temperatures...."
date: 2008-06-07
forum: Hardware
---

### Post by RadarBat on 2008-06-07
I would like to find some way to keep up with in-box temperatures (i.e.- CPU, HDD, Video Card, Ambient) I have looked for temp guages, but have found nothing I like. Currently, the mobo is at 32 degreea C and the CPU is at 57 degrees under light load. Is this too hot?     Ben

---

### Post by jbrown96 on 2008-06-07
Acceptable temperatures vary depending on your system. I have a Core2Duo 2.0GHz in a laptop and it's at 47C under light load. ```
cat /proc/acpi/thermal_zone/THM0/trip_points
``` will show you the temperature where the system kills power to avert damage. My C2D says 127C. You can change THM0 if you have more than one core (e.g. THM1 for the 2nd core, THM2 for the 3rd, etc.)
```
 cat /proc/acpi/thermal_zone/THM0/temperature 
``` will also show you the current temp, so you don't need monitors running all the time if the look bothers you.

---

### Post by sergiom99 on 2008-06-07
my /proc/acpi/thermal_zone/THM0 is empty!
what about trip points?

---

### Post by RadarBat on 2008-06-07
> ben@ben-desktop:~$ cat /proc/acpi/thermal_zone/THM0/trip_points
cat: /proc/acpi/thermal_zone/THM0/trip_points: No such file or directory

That did not work.

Edit; Neither did the other - Same response. Am I in the wrong dir or something?  Ben

---

### Post by nick_h on 2008-06-07
Try:
```
cat /proc/acpi/thermal_zone/THM/trip_points
```

---

### Post by RadarBat on 2008-06-07
Same thing:
> ben@ben-desktop:~$ cat /proc/acpi/thermal_zone/THM/trip_points
cat: /proc/acpi/thermal_zone/THM/trip_points: No such file or directory


---

### Post by nick_h on 2008-06-07
You could step through the path using TAB completion.  Type cat /proc/a and then hit TAB a couple of times and it will either complete the directory or give you the options.  It will have the same effect of doing an ls of each directory in turn.

In answer to your original question - what have you tried so far and what are you looking for?

The obvious packages are lm-sensors, hddtemp and sensors-applet.

57C and 32C don't seem very high.

---

### Post by RadarBat on 2008-06-07
> **nick_h said:**
> You could step through the path using TAB completion.  Type cat /proc/a and then hit TAB a couple of times and it will either complete the directory or give you the options.  It will have the same effect of doing an ls of each directory in turn.

In answer to your original question - what have you tried so far and what are you looking for?

The obvious packages are lm-sensors, hddtemp and sensors-applet.

57C and 32C don't seem very high.

I am looking for a not-so-very-expensive in-box temp gauges to monitor the above-mentioned.

This is the first gaming machine I have built and the first time I am going to try gaming. I am a bored 61 year old retired fart who really likes Ubuntu but doesn't know much about it. I tried Dapper Drake for 6 months and decided to wait to convert to Ubuntu. 

I am unfamiliar with the packages you mentioned.....Ben

---

### Post by nick_h on 2008-06-07
**sensors-applet** is a Gnome panel applet that displays system temperatures.  Install it through the Synaptic package manager or in a terminal with:
```
sudo apt-get install sensors-applet
```

Then you will need to add it to a panel.  Right-click on a panel and select "Add to Panel".  The applet will be called "Hardware Sensors Monitor".  It should do CPU temperature by default.  It also can display system voltages, fan speeds etc... if your system supports them.

**hddtemp** is a package that monitors hard drive temperature.  It is compatible with sensors-applet.

**lm-sensors** monitors other sensors if supported by your computer.

---

### Post by RadarBat on 2008-06-07
Sensors-applet shows 44 degrees C for the GPU (video card?). Does it display anything else?
Do **hddtemp and lm-sensors** need to be installed via SPM? 

EDIT: I have installed **hddtemp** and **lm-sensors** but nothing more is displayed. Does my computer not support them? Ben

---

### Post by ssc351 on 2008-06-10
> **RadarBat said:**
> 
EDIT: I have installed **hddtemp** and **lm-sensors** but nothing more is displayed. Does my computer not support them? Ben

Run sudo sensors-detect

---

