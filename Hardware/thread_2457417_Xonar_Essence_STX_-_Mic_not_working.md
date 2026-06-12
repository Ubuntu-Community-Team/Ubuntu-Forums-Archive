---
title: "Xonar Essence STX - Mic not working"
date: 2021-02-01
forum: Hardware
---

### Post by Psyphre on 2021-02-01
Hi everyone,

This is the first time I have had to post a problem in the ubuntu forum for years - which is a testament to how far Linux has come from when I first started.

I've got a Xonar Essence STX soundcard that has worked with no issues for outputting audio, however for the first time I plugged a headset into the front panel (I saved up for an awesome senheisser headset). The audio works fine, but unfortunately the mic does not work at all.

When I've searched the forums all results are around 2010-2013 and massively out of date.

Would be super grateful for anyone who can help as I love this headset but will have to return it if I can't get it to work in linux :(

I tested in windows and works fine no issues there. Although I did have to choose front panel as the mic in the asus software, so I think linux needs to be told to do the same but don't know how!

Thanks!

---

### Post by Psyphre on 2021-02-02
Ok I managed to make some progress, I used alsa-mixer and in there I could switch the input to look at the front panel.

I don't get what pulse-audio actually does over alsa other than cause headaches lol.

---

