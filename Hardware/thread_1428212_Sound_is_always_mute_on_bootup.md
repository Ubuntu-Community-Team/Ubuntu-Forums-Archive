---
title: "Sound is always mute on bootup"
date: 2010-03-12
forum: Hardware
---

### Post by Cushie on 2010-03-12
Why is my AAO netbook, running Karmic, always mute when I bootup.  I can turn on the audio via the toolbar icon and use the sound/Skype programs OK but the setting is not remembered the next time I boot.  I have not had this problem before on earlier OS versions or on other computers.  A solution would be appreciated.

---

### Post by subedistra7 on 2010-03-12
i think its a pulseaudio bug.

```
sudo apt-get purge pulseaudio
```

---

### Post by garvinrick4 on 2010-03-12
Hope you did not purge pulseaudia:



Mute Fix

Audio mute fix
Works everytime for me,
This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore


Now set audio where you like and log-out on log-on to make
sure of fix.

---

### Post by subedistra7 on 2010-03-12
> **garvinrick4 said:**
> Hope you did not purge pulseaudia:



Mute Fix

Audio mute fix
Works everytime for me,
This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore


Now set audio where you like and log-out on log-on to make
sure of fix.

try this advice first.

---

### Post by Cushie on 2010-03-13
> **garvinrick4 said:**
> Hope you did not purge pulseaudia:



Audio mute fix


Add # to the line 'load-module module-device-restore'

in file   /etc/pulse/default.pa 

#load-module module-device-restore




Worked a treat, now I've got the haunting drum roll back, great!
Many thanks 'garvinrick4' and purge was not necessary.
Regards Cushie :)

---

