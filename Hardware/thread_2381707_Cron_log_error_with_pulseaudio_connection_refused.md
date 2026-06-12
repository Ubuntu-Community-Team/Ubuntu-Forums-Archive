---
title: "Cron log error with pulseaudio connection refused"
date: 2018-01-04
forum: Hardware
---

### Post by 0N3 on 2018-01-04
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

My custom crontab script works fine but doesn't produce any sound. Any help appreciated! Runnig the script from my desktop it works and plays sound cron is causing some issue fr it to not play sound.

```
#! /bin/bash




# read battery percentage value
OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT1 | grep percentage`




# select only the int value
IFS=':' read -ra P <<< "$OUT"
PERCENTAGE="%"
BATTERY_VALUE=${P[1]%$PERCENTAGE}




# send a notification if battery level is under 15% and not on AC power


if ! on_ac_power; then 
	if (($BATTERY_VALUE  < "15")); then
	    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	    notify-send "Battery charged! You can now unplug your laptop!"
	    paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi


# send a notification if battery level is equal to or over 90% and is on AC power


if on_ac_power; then
	if (($BATTERY_VALUE  >= "90")); then
	    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	    notify-send "Battery charged! You can now unplug your laptop!"
	    paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi
```

---

