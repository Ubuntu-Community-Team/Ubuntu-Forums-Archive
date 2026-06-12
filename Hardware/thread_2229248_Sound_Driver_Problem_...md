---
title: "Sound Driver Problem .."
date: 2014-06-12
forum: Hardware
---

### Post by ezomy on 2014-06-12
hi all ,
after i upgrade kernel to 3.13.0.30 i got problem ..
the sound card disappear (screenshot) :
[IMG]http://s16.postimg.org/r0e6es691/Screenshot_from_2014_06_12_10_15_45.png[/IMG]

and that alsa-project link of my PC : 
[http://www.alsa-project.org/db/?f=075dd37f3562a870b1979f487d75a5f2d1f55dc6](http://www.alsa-project.org/db/?f=075dd37f3562a870b1979f487d75a5f2d1f55dc6)

finally , sorry for my bad english :redface:

---

### Post by Yellow Pasque on 2014-06-12
```
Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

RoarAudio:
      Installed - Yes (/usr/bin/roard)
      Running - Yes
```

RoarAudio is blocking pulse's access to sound card.

---

### Post by Yellow Pasque on 2014-06-12
See if this works:
```
sudo killall roard
sudo alsa force-reload
```

If so, either remove roaraudio or prevent it from running upon startup.

---

### Post by ezomy on 2014-06-12
> **Temüjin said:**
> If so, either remove roaraudio or prevent it from running upon startup.

its worked fine , how can i do that :frown:

---

### Post by Yellow Pasque on 2014-06-16
```
sudo apt-get remove roaraudio
```

---

