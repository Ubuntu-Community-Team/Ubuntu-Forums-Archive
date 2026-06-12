---
title: "Fan is not turning on in Lucid on Dell Studio 1555"
date: 2010-09-06
forum: Hardware
---

### Post by v1nsai on 2010-09-06
My fan does not seem to be turning on anymore, I just noticed it's at 90C.  It's been working for a while now so I'm a little stumped.  I discovered the control files for acpi are in /proc/acpi, and that the acpi temperature can be monitored by checking ```
cat /proc/acpi/thermal_zones/*/temperature
```
This outputs 0C on all 3 thermal zones on my system.  Seems like this may be the problem.  I'm using the coretemp module and sensors-applet to monitor my system, so I know there are sensors on the board and they are working properly.  Is there a way to get ACPI to use coretemp, or how should I go about getting acpi to behave?  My laptop is cooking :-/

Edit:
Seems to only happen after I come back from suspend...god it's been years and suspend is still the one thing I can never get to work on any linux distro.

---

