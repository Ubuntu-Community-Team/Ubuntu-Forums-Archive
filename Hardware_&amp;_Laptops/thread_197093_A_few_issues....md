---
title: "A few issues..."
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Knight on 2006-06-15
Just picked up a Fujitsu Amilo A1650G and thought I'd try out Ubuntu on it. The big problem is no working WLAN. I downloaded the ndiswrapper and put on the the drivers from here

[http://ubuntuforums.org/showpost.php?p=1085392&postcount=55]("http://ubuntuforums.org/showpost.php?p=1085392&postcount=55")

But it says Hardware present: No, and not surprisingly, still doesn't work. Anyone know the trick to making WLAN flip on?
The other less critical but still annoying problem is the touchpad. After a few minutes of use it seems to think eveytime I touch it I'm holding down the left mouse button. Any ideas whats going on? Thanks in advance.

---

### Post by Knight on 2006-06-15
well, I accedently got the touchpad working better, it no longer flips out thinking I'm left clicking but at the same time, the scroll ability on it is gone, a workable tradeoff for me. But still can't get the WLAN working, any help would be appreciated. Thanks again.

---

### Post by Knight on 2006-06-15
I think I found the right drivers to use with ndiswrapper, but now when I go to add it and click install, nothing happens. Anyone know whats going on?

---

### Post by Knight on 2006-06-17
Okay got it all going now. I had to download and install [ndiswrapper]("http://ndiswrapper.sourceforge.net/") and [acer_acpi.]("http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html") After getting the proper .inf and .sys file off the driver CD, ndiswrapper detected the card right away. Now when I boot up, I just have to put this in the terminal...
```
modprobe acer_acpi
modprobe ndiswrapper
echo "enabled : 1" > /proc/acpi/acer/wireless
```
and the light flips on, then I'm able to use wifi-radar I got from the repositories to connect. Just thought I'd post a follow up to whats going on in case someone else is having the same problem.

---

### Post by damagedspline on 2006-08-18
> **Knight said:**
> Okay got it all going now. I had to download and install [ndiswrapper]("http://ndiswrapper.sourceforge.net/") and [acer_acpi.]("http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html") After getting the proper .inf and .sys file off the driver CD, ndiswrapper detected the card right away. Now when I boot up, I just have to put this in the terminal...
```
modprobe acer_acpi
modprobe ndiswrapper
echo "enabled : 1" > /proc/acpi/acer/wireless
```
and the light flips on, then I'm able to use wifi-radar I got from the repositories to connect. Just thought I'd post a follow up to whats going on in case someone else is having the same problem.

thanks, that helped!

btw, ndiswrapper is not required - i used the kernel driver that came with dapper and it worked like a charm.

the touchpad leftclick is annonying (like in "icon grab" action)- how did you fixed that?

EDIT: i forgot to mention - i need to chmod the /proc/acpi/acer/wireless every time i reboot to make it permission friendly + wifiradar recognize  g ap's as b

---

