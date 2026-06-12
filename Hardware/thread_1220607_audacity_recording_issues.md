---
title: "audacity recording issues"
date: 2009-07-23
forum: Hardware
---

### Post by mblack3 on 2009-07-23
Hello
i recently downloaded audacity. I am trying to record from a cassette player to the computer via a double-ended headphone jack to the mic on my laptop. Well on ubuntu it doesnt record anything. I played around with alsa and pulseaudio volume control to no avail. For some reason, if pulseaudio volume control is open and i show, under input devices, all input devices, audacity picks it some audio but really distorted and scratchy. I want to clean it up and make it record audio, it does so fine in vista. Thanks and let me know if this makes sense. Thanks

---

### Post by nixscripter on 2009-07-29
I've had trouble with pulseaudio in the past. Audacity should allow you to pick the raw ALSA device if you kill pulse audio first (which might have other side effects on your system).

If you quit audacity, and run ```
sudo /etc/init.d/alsa-utils restart # save and reload alsa mixer settings
sudo /etc/init.d/alsasound restart # kill processes using alsa
```

you should be able to restart audacity and give it raw access to the device.

---

