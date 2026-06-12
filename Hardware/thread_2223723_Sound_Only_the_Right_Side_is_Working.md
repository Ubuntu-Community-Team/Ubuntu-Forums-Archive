---
title: "Sound: Only the Right Side is Working"
date: 2014-05-12
forum: Hardware
---

### Post by Vid_Warren on 2014-05-12
Hi,

I'm using a Samsung NC10 Plus netbook. In the last few weeks, I upgraded to Ubuntu 14.04.
My first Ubuntu was (ages ago) 10.04 and I have updated every step of the way.

There's no sound coming out of the left side of the laptop. I do have a feeling that this happened today but I'm not entirely sure.

[B]Things I've tried already:
[/B]
sudo wget pastebin.com/download.php?i=f5f9654bb -O /etc/asound.conf
      sudo wget pastebin.com/download.php?i=f2e38265 -O /usr/share/alsa/cards/HDA-Intel.conf
---
Installing this [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
---
Opening the alsamixer in terminal. I tried changing the mixer from 'default' to HDA Intel to no effect; I think they're the same as no other soundcard came up.
The chip in my soundcard is a 'Realtek ALC269'.
---
When I type this to Terminal:
grep "Codec:" /proc/asound/card*/codec*
It returns this:
Codec: Realtek ALC269

-

So far, nothing has worked. Hopefully one of you will have something better.

Thanks in advance.

---

### Post by Vid_Warren on 2014-05-22
I've plugged in speakers. They work (in stereo).

When I unplug them, only the right speaker in my laptop works. Any ideas?

---

### Post by Yellow Pasque on 2014-05-22
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

