---
title: "No audio through HDMI only when running VLC"
date: 2016-01-24
forum: Hardware
---

### Post by Dr.Leet on 2016-01-24
Hello
I am trying to play music through my Pioneer VSX-528 Receiver using an HDMI cable. I am running Xubuntu 15.10 on an Asus UX32VD laptop.
If I open VLC and start a movie I get sound through my external speakers when I switch to HDMI output. But if I am running Spotify and switch to HDMI output there is no sound.
So in order to get sound through my external speakers I have to open VLC, switch to HDMI output, shutdown VLC and start spotify, then it works just fine. But if I switch to the laptop speakers and back to the external speakers again, while Spotify is running, there is no sound. Even if Spotify is not running during the switching and started afterwards it doesn't work. For some reason VLC has to be running.

I have absolutely no idea why it works when VLC is running and doesn't when Spotify is running. Does anyone know what to do? And what output do you need to see?

---

### Post by Dr.Leet on 2016-01-25
It seems like the problem was caused by a lack permissions. I did the following:
- sudo usermod -a -G audio,pulse,pulse-access,video,voice USERNAME
- Enable mirror displays
Now I can switch between HDMI and PC speakers.

---

