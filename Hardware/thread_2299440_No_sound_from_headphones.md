---
title: "No sound from headphones"
date: 2015-10-18
forum: Hardware
---

### Post by martin175 on 2015-10-18
On Ubuntu 14.04, HP ZBook 15 G2 notebook I get no sound from headphones when I plug them. Sound on main speakers is working on Ubuntu. Headphones are working on Win 10.

I ran alsamixer and played with volume levels there with no luck. Can you please help?

---

### Post by righN on 2015-10-18
Try

```
sudo apt-get install pavucontrol
```

---

### Post by martin175 on 2015-10-19
It is completely weird. In pavucontrol, I see this:

I play youtube video - I see sound level bar at HDMI output (unplugged) section moves only. No sound to speakers and headphones, no matter whether they are plugged or not.

 I play mp3 - I see sound level bar moves both for Speakers and Headphones (no matter whether they are plugged or not). But sound comes only from main speakers when headphones are unplugged.

---

### Post by Yellow Pasque on 2015-10-20
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Firefox (and Chrome too IIRC) has a funny way of not caring what audio device you have chosen. It likes to use whatever device is index 0. You can use some trickery to force your desired output to index 0: [https://wiki.gentoo.org/wiki/ALSA#HTML5_does_not_play_in_the_Firefox_browser](https://wiki.gentoo.org/wiki/ALSA#HTML5_does_not_play_in_the_Firefox_browser)

---

