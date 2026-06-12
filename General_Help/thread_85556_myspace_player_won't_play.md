---
title: "myspace player won't play"
date: 2005-11-02
forum: General Help
---

### Post by autonomy on 2005-11-02
anybody figure out what's wrong with at least my myspace players? i tried [neon blonde]("http://myspace.com/neonblondebats") and [nin]("http://myspace.com/nin"), but neither one will play. at first, neon blonde said, "play", "buffering", and did that animation where the fake equalizer engages, but now, it won't even do that.

---

### Post by ecobuntu on 2005-11-02
click "standalone player"  that will make it work

---

### Post by Confuse on 2005-11-03
Doesn't work for me either, despite your solution to use the "stand alone player".

---

### Post by autonomy on 2005-11-03
Yeah, I think it's 'cause we're not enabled to play MP3s. I know I'm not. If you don't know why, it's explained in the wiki. Basically, MP3s are copyrighted and the ability to play them costs seventy-five cents per Ubuntu distribution. I think we're supposed to hope/get people to encode their music in Ogg Vorbis or use MP3s at our own risks.

---

### Post by ecobuntu on 2005-11-03
go to the ubuntu.com website and look for restricted format then look for mp3 and install the appropriate packages.

---

### Post by ecobuntu on 2005-11-03
[QUOTE=ecobuntu]go to the ubuntu.com website and look for restricted format then look for mp3 and install the appropriate packages.[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
There it is...

For MP3s

To play MP3s and many other restricted multimedia formats using totem or rhythmbox (included in Ubuntu), add the universe and multiverse repositories and install the following packages: 

sudo apt-get install gstreamer0.8-plugins gstreamer0.8-ffmpeg

---

