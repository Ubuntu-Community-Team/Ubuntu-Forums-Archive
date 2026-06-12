---
title: "Battery monitor script"
date: 2011-01-31
forum: Hardware
---

### Post by Alexis Phoenix on 2011-01-31
I made this script to remind me to charge/discharge my laptop battery within levels which promote battery health (only for Li-ion batteries!).

Please can people test this script and see what you think - it needs to run in the background so maybe as a cron job or maybe as part of xinitrc. It relies on the gnome message box, zenity.

Check battery name - it may not be the same on your system.

This is only the first attempt at this, so tell me what you think - also ways the script can be improved!
```
#!/bin/bash

flag=0
oldflag=0

while [ 1 ]; do
  full="$(cat /sys/class/power_supply/BAT1/charge_full)"
  now="$(cat /sys/class/power_supply/BAT1/charge_now)"
  status="$(cat /sys/class/power_supply/BAT1/status)"
  
  value="$(echo "scale=1; 100/($full/$now)" | bc | awk '{printf "%.0f", $0}')" 
# awk/printf used because scale=0 doesn't work properly in bc

 # echo "$full $now $value" # only for testing

  if [ $value -ge 39 ]&&[ $value -le 41 ]; then
    action="Optimum charge for storage. You should store the battery in a cool place if you don't need to use it"
  fi
  if [ $value -le 15 ]&&[ "$status" -eq "Discharging" ]&&[ "$flag" != "1" ]; then
    action="You should plug into the mains now to prolong battery life."
    oldflag=$flag
    flag=1
  fi
  if [ $value -ge 85 ]&&[ "$status" = "Charging" ]&&[ "$flag" != "2" ]; then
    action="You should unplug the mains and run on battery for a while to prolong battery life."
    oldflag=$flag
    flag=2
  fi
  if [ "$oldflag" -ne "$flag" ]; then
    ret="$(zenity --warning --title "Battery Status" --text "Battery charge is at $value%. $action")"
  fi

  sleep 60
done
```

---

