---
title: "cant get my speakers to work on ubuntu (dual booted)"
date: 2020-11-27
forum: Hardware
---

### Post by spiros83 on 2020-11-27
Hey ther!Anyone could help me with ubuntu not recognizing my speakers as an output audio device? tried alsamixer (everything not muted) and i cant see the speakers nor in settings nor pulseaudio...tried whatever i found on internet, it only shows me the vga card as output dev or smth....new to ubuntu, speakers work properly on wind dual boot...thxxx

---

### Post by Yellow Pasque on 2020-11-27
If you're dual booting and having issues with audio, make sure you completely shut down. Sometimes, when doing a reboot from Windows, Linux can't initialize the sound properly.

If you're still having issues after a cold boot, upload your alsa-info and share the link here.
```
sudo alsa-info --update
alsa-info
```

---

### Post by spiros83 on 2020-11-27
[http://alsa-project.org/db/?f=6523ccb471b2d7db2fb28b37380a47323d9e003b](http://alsa-project.org/db/?f=6523ccb471b2d7db2fb28b37380a47323d9e003b)
Thanks for helping!

---

### Post by spiros83 on 2020-11-28
So could anyone offer any help? Will appreciate it, thxx

---

### Post by Yellow Pasque on 2020-12-02
Everything looks good in the alsa info. What is the output of:
```
pacmd list-cards
```

---

