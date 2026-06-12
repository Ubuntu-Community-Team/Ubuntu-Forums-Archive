---
title: "Low laptop battery alarm/warning script"
date: 2011-08-03
forum: Hardware
---

### Post by aleblanc on 2011-08-03
Here is a very short script I use for playing an audio file when my battery gets low and is not charging. I thought others might find this useful.
It is based on another script I found somewhere (can't remember where) but I added a line to check if the power cable is plugged in first (otherwise the alarm kept going off while charging).
You should setup a cron job to run this script every minute or so.
Copy the following code into a file, e.g. battery_alarm.sh.
Change /usr/share/sounds/yelp.wav to the path of the audio file you want to play. Change CMB1 to your battery name (check with: ls /proc/acpi/battery/). Change the value of 550 to whatever value you want. I chose 550 since it is about 10% of the fully charged value as shown in /proc/acpi/battery/CMB1/state (remaining capacity).
Save the script somewhere and make it executable with "chmod +x battery_alarm.sh", then setup a cron job to run the script every minute or so (see [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/CronHowto")  for how to do that).


```
#!/bin/bash
# Simple script to play warning sound if battery is low (if remaining capacity < 550mAh).
# This should be called by a cron job every minute or so.

if [ "`cat /proc/acpi/ac_adapter/AC/state | grep off-line`" ]; then
    awk -vSP=550 '/remaining capacity/ && $3<SP{system("aplay /usr/share/sounds/yelp.wav")}' /proc/acpi/battery/CMB1/state
fi
```

---

### Post by krzysztofikus on 2012-01-23
I wanted to set up the alarm and followed your instructions, but the script seems to be not working. Is there any way to check what is wrong?

---

### Post by Bufeu on 2012-07-05
> **krzysztofikus said:**
> I wanted to set up the alarm and followed your instructions, but the script seems to be not working. Is there any way to check what is wrong?
It does work, but you must have the package aplay and a a sound file called yhelp.wav in /usr/share/sounds.

You can always change the location of the file that are going to be played. You can also use VLC Media Player instead using ```
cvlc /home/file/toplay.wav vlc://quit
``` intstead of ```
aplay /home/file/to/play.wav
```

EDIT: Thanks for the script btw.

---

