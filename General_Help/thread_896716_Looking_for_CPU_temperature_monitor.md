---
title: "Looking for CPU temperature monitor"
date: 2008-08-21
forum: General Help
---

### Post by rubrboots on 2008-08-21
I am looking for a program that will monitor and log my cpu temperature. I have read about conky and torsmo and they appear to represent real time data only. I will be running this on a mythbuntu box so I will not be viewing the desktop very much. I would like to have the ability to access a log that reports the system temps every 10 mins or so. Does this type of software exist for ubuntu?

---

### Post by Thingymebob on 2008-08-21
simple bash script to record temperatures to a log file called sensorslog
```

og#!/bin/bash
date >> sensorslog
echo "Sensors Value " >> sensorslog
sensors >> sensorslog
echo "acpi thermal zone" >> sensorslog
cat /proc/acpi/thermal_zone/THRM/temperature >> sensorslog
echo "---------------------------------------" >> sensorslog
exit 0

```

make it executable (chmod +x *scriptname*)

set it up in crontab to run every ten minutes (crontab -e)
```

# m h dom dow command
 0,10,20,30,40,50 * * * /path/to/scriptname

```

---

