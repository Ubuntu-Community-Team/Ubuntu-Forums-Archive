---
title: "HIgh memory usage by some Screenlets"
date: 2008-11-21
forum: General Help
---

### Post by vipseixas on 2008-11-21
Hello Humans!

I've been using some Screenlets since last week and now I realized how much memory they are eating in my system. It's really too much ram for that little applications, I don't know if the problem is with poor Screenlet programming or a problem with Python, but look at that:

```
vseixas@vseixas-laptop:~$ ps -C python -o %mem,rss,size,args
%MEM   RSS    SZ COMMAND
 0.7 13508 14640 python -u /usr/share/screenlets/RingSensors/RingSensorsScreenlet.py
 0.6 12464 13312 python -u /usr/share/screenlets/Pager/PagerScreenlet.py
 0.4  9388  9872 python /usr/share/screenlets-manager/screenlets-daemon.py
 0.6 13016 14120 python -u /usr/share/screenlets/Picframe/PicframeScreenlet.py
 0.6 12108 13344 python -u /usr/share/screenlets/Trash/TrashScreenlet.py
 0.6 12904 14176 python -u /usr/share/screenlets/Places/PlacesScreenlet.py
 0.7 14132 16120 python -u /usr/share/screenlets/ClearCalendar/ClearCalendarScreenlet.py
 0.5 10608 13204 python -u /usr/share/screenlets/Flower/FlowerScreenlet.py
 0.6 11944 14864 python -u /usr/share/screenlets/Notes/NotesScreenlet.py
 0.7 13548 14452 python -u /usr/share/screenlets/Sensors/SensorsScreenlet.py
 0.6 13008 13600 python -u /usr/share/screenlets/DigiClock/DigiClockScreenlet.py
 0.6 13420 18688 python -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py
 0.9 19132 15628 python -u /usr/share/screenlets/AmarokControl/AmarokControlScreenlet.py
 0.8 15436 21808 python -u /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py

```

10MB seems to be the footprint of a Screenlet, here a have almost 200MB with 14 screenlets + the manager.

Is there a light at the end of the tunnel or do I have to use less screenlets? Actually I was planning to use more :P I don't understand the python language, but I will try to look at the code of a screenlet to find out what is eating all this memory.

[]s!

Vinicius

---

