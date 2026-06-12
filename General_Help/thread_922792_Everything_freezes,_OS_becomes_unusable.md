---
title: "Everything freezes, OS becomes unusable"
date: 2008-09-17
forum: General Help
---

### Post by rdionicio on 2008-09-17
Once in a while I'll have this weird problem where my audio wont work anymore and then when I try to restart my computer from the menu, the window wont even come up. My firefox starts to freeze when I try to research it and when I want to restart my computer through the terminal, I can't because the window doesnt come up. Sometimes I can get everything back by press ctrl-alt-backspace but the audio doesnt come back which means I have to restart my computer completely.

Has anyone had this kind of problem before?

I've tried looking through some logs and I found this

```
Sep 17 09:50:56 moo pulseaudio[5816]: pstream.c: Failed to import memory block.
Sep 17 09:54:24 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 17 09:54:30 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 17 09:57:36 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 17 10:00:17 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 17 10:01:13 moo last message repeated 8 times
Sep 17 10:01:24 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 17 10:02:40 moo pulseaudio[5816]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
```

---

