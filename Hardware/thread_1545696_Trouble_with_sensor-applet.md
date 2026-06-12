---
title: "Trouble with sensor-applet"
date: 2010-08-04
forum: Hardware
---

### Post by Vimmander on 2010-08-04
Here's the quick rundown.  I have, by default, libsensors4 installed, so I ignored tutorial steps that needed libsensors3 installed.  I installed sensors-applet and hddtemp (some plugin was installed as a dependency).  I have looked at the preferences menu for sensors-applet, but see no option for hard drive temperature.  The GUI displays the following icons, from left to right:  CPU, temp1, Core0 Temp, Core0 Temp, Core1 Temp, and Core1 Temp.  All the icons are for CPUs, but temp1 has a blue graph, if that's of any significance.  I have included a screenshot of my desktop.

Questions:  Why can't I add an icon for hard drives?  Is temp1 the hard drive?  And why do I have two temperatures for each of my cores, when I have only two cores?  Both pairs of temperatures are never the same, and change independently of one another.  In CPUID's hwmonitor for Windows, only one temperature was shown for each core.  Is it that each core has two sensors, and CPUID took an average of them, whereas sensors-applet shows them separately?

Thanks in advance!

---

