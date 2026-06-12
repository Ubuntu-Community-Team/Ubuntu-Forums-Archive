---
title: "brightness dims on acer 5720"
date: 2008-11-18
forum: Hardware
---

### Post by liquid.silver on 2008-11-18
I have an Acer Aspire 5720 with intrepid installed and working. I have been using gutsy for quite some time and just recently upgraded.

The problem is that my lcd brightness often dims (it worked fine on gutsy). I can reproduce the problem and I have figured out that it is only when certain things happen, like starting vlc or virtualbox. It seems to be when changing video settings or outputting to the screen, but i'm not sure.

"/proc/acpi/video/VGA/LCD/brightness" still shows that the current brightness is set to 100%, but the real brightness isn't.

I can reset the brightness to 100% by manually dimming it and then brightening it, but this is a non-optimal solution.

Nothing is logged in the syslog and i'm not sure where acpi events are logged.

Any help would be appreciated.

---

### Post by liquid.silver on 2008-11-19
Some more info: i figured that the acpi events should be logged to /var/log/acpid which is all good and would probably help, except there is no such file. I'm not sure why.

"$ ps -A | grep acpi" returns:
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
 4764 ?        00:00:00 acpid
 5606 ?        00:00:00 hald-addon-acpi

so the daemon is running, but there is no logging...

this brightness issue is starting to get on my nerves. and it used to work perfectly in 8.04... :(

---

### Post by X_Splinter on 2008-11-30
Same problem here with Ubuntu 8.10

---

### Post by russu52 on 2009-01-28
check power-managment options. there is a box marked dim display when idle. uncheck. should be ok

---

### Post by ednicholson on 2009-05-17
I have similar problem using 9.04 on my Acer 5720-4680.  Using a dvd player like MPlayer Movie Player ends up very dim.  Too dim to watch form a comfortable distance.  I found this workaround but still looking for a proper fix.  I've seen a lot of people asking for fixes.

And I still get display brightness flickering.  Sometimes the flickering corresponds with mouse movement.  But sometimes not.

Workaround:
Open power management and jiggle the brightness control after starting the player. Leave power management open.  This "reminds" the power management to set display brightness as intended.  Unfortunately this work around does not work for other video players such as gxine.

---

### Post by liquid.silver on 2009-05-18
I've already written a simple workaround script. It might not be the best way, but it works for me. Just edit the cd command to work for your system. Here goes:

```
#!/bin/bash

#cd /proc/acpi/video/VGA/LCD
cd /proc/acpi/video/OVGA/DD03

sudo chmod a+rw brightness

while [ true ]
do
  echo -n "100" > brightness
  sleep 1
done
```

---

