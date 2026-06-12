---
title: "HP pavilion dv5 --- no sound"
date: 2010-06-21
forum: Hardware
---

### Post by vawx on 2010-06-21
I have tried:

```
 gksu gedit /etc/modprobe.d/alsa-base.conf
```

```
 options snd-hda-intel model=hp-dv5
```

- a search showed that some of the HP pavilion entertainment pc's have this issue. But, it didn't work for me.

One wierd thing, I can hear sound at the login screen (the Ubuntu clicking noise) but I can't hear anything after that.

(My sound settings are set to the "internal audio" (not HDMI) and my computer is not set to mute / low volume.)

---

### Post by vawx on 2010-06-21
figured it out with more google.

[http://29a.ch/2009/6/2/getting-audio-to-work-on-a-hp-pavilion-dv5-ubuntu-9-04](http://29a.ch/2009/6/2/getting-audio-to-work-on-a-hp-pavilion-dv5-ubuntu-9-04)

---

