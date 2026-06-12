---
title: "Screenlets - Not starrting on Boot"
date: 2008-09-21
forum: General Help
---

### Post by Newc on 2008-09-21
Hello

I am currently running the latest edition of Screenlets, on start of the machine the screenlets will not boot.  I will then open Screenlets Manager and notice that the tick in the box for "Start/Stop" is not present, however when I check these boxes the screenlets will then load as usual.  I have made a bash file, made entries in the sessions>start up programs, yet they still will not load...any ideas?

---

### Post by Kevbert on 2008-09-21
In sessions what command have you put in ?  Here's an example from mine
```
python -u /home/kevin/.screenlets/WordOfTheDay/WordOfTheDayScreenlet.py
```
This automatically runs the WordOfTheDay screenlet with no manual bash file.

---

### Post by Newc on 2008-09-21
Yes...here is what I put in sessions
```

python -u /usr/share/screenlets/Clock/ClockScreenlet.py

```
(that doesn't load the clock)
Here is the file I made
```

#!/bin/bash
compiz --replace &
sleep 5
emerald --replace &
sleep 5
avant-window-navigator &
/usr/share/screenlets-manager/screenlets-daemon.py > /dev/null &
/usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py > /dev/null &
/usr/share/screenlets/Clock/ClockScreenlet.py > /dev/null &
/home/kyle/.screenlets/Pidgin/PidginScreenlet.py > /dev/null &
/usr/share/screenlets/RingSensors/RingSensorsScreenlet.py > /dev/null &
/usr/share/screenlets/Trash/TrashScreenlet.py > /dev/null &

```

---

### Post by dBuster on 2009-03-22
After having issues with clearweather not starting for me I searched and found this posting.  After reading it I did some digging and found out that the entry made for clearweather into the sessions was incorrect!!  

I dug into the settings for clearweather in sessions and it was pointing to my home folder when clearweather was in the usr/share/screenlets instead.  Made that change and rebooted and voila it was there!

Thanks for this thread and the information here.  Gave me what to look for and solve my issue.  I will retain this for other screenlets that I can not get to start automatically.

---

### Post by dodle on 2009-03-22
> **dBuster said:**
> I dug into the settings for clearweather in sessions and it was pointing to my home folder when clearweather was in the usr/share/screenlets instead.  Made that change and rebooted and voila it was there!Thanks dBuster, your post helped me out a lot.  I had installed CPU_meter as a privileged user, so it was located in /usr/share/screenlets instead of $HOME/.screenlets.  After reading your post, I went to /usr/share/screenlets/CPU_meter and changed this line in menu.xml:```
<imageitem label="Open 'top'" icon="terminal" id="exec:gnome-terminal  --working-directory=$HOME -x top" />
```to:```
<imageitem label="Open 'top'" icon="terminal" id="exec:gnome-terminal  --working-directory=/usr/share/screenlets -x top" />
```

---

### Post by JayUK20 on 2009-07-19
I am also having the same problems where no screenlets do not display after reboot. All of my screenlets and the manager are located in /user/share and have opened up the the files names ending in .py but nothing inside those files tell me where they should be located.

---

