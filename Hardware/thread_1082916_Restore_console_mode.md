---
title: "Restore console mode"
date: 2009-02-28
forum: Hardware
---

### Post by asl.pavel on 2009-02-28
Ubuntu 8.10 laptop Dell Inspiron 1525 with intel embeded video. Some times i can't restore to console mode ( CTRL+ALT+F1 ) i just got black screen, but it actualy works ( i can type ( in blind ) some command and it will be executed ), and sometimes switch to console mode not happens ( screen blinks and i am again in X mode ).And more, console mode not compleatly dead when reboot i can see it again , it some how restores ( tried stop gdm but it doesn't help ) I noticed this problem when i started configure other window manager ( awesome 3.1 ), and was forced to often switch from console mode to graphic mode ... and it becomes realy annoying to reboot system when console mode dies !!! I use plain text mode, no frame buffer:
```

[~] $ cat /sys/class/vtconsole/vtcon0/name 
(S) VGA+
[~] $ cat /sys/class/vtconsole/vtcon0/bind 
1

```

Plz help ... or at least suggest how restore text mode without rebooting ...:confused:

---

