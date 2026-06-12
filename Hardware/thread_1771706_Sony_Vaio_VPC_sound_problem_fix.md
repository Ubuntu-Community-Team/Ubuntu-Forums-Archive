---
title: "Sony Vaio VPC sound problem fix"
date: 2011-05-30
forum: Hardware
---

### Post by neverov on 2011-05-30
I have a laptop Sony Vaio VPCYA1V9R. For a while I had a sound only in headphones, speakers didn't work. I found following solution (author claims it works also for Sony Vaio VPCEB2E1R, VPCEB1M1E and probably other models):

* install hda-analyzer 
  ```
wget -O run.py http://www.alsa-project.org/hda-analyzer.py
```* run it 
  ```
python run.py
```* open Node[0x19] PIN, change VREF checkbox from 80 to HIZ
* check the sound 
  ```
aplay /usr/share/sounds/alsa/Front_Center.wav
```If sound works - make the change permanent, to do that you will need a hda-verb program. Download it, make it, put it somethere in the path (for example at /usr/bin/hda-verb).

Add a following line to /etc/rc.local (before line exit 0):

```
/usr/bin/hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x60

```This will fix the sound after machine start.

But sound will be broken after return from sleep, to fix that create a file /etc/pm/sleep.d/99_fix-sound with content:

```

#!/bin/bash

case "$1" in
    thaw|resume)
        /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x60
        ;;
    *)
        ;;
esac
exit $?

```and make it executable.

---

### Post by lidex on 2011-05-30
I would suggest filing a bug in launchpad so this gets fixed in alsa so you don't have to hack it. Follow the link in my sig.

---

