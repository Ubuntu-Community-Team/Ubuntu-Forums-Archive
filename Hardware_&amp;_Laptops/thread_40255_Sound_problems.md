---
title: "Sound problems"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by CAE on 2005-06-08
Hey guys. Not really sure which forum this should be in as I guess it is a part-hardware, part-software issue, but I'd appreciate any help you could give me. If a mod feels the need to move it, then be my guest.

Anyway, here's my problem. Firstly, I get no sound out of gstreamer applications (totem, rhythmbox). Xine applications work fine and I know there's totem-xine, but I'm still without a music player (unless you can suggest a xine based player). Plus I'd rather sort this out.

I'm in the rather painful situation of having two active soundcards. Disabling one isn't an option, before you mention it. To get around it, I've got an /etc/asound.conf that looks like this:
```
ctl.!default {
  type hw
  card 1
}
```

This sets the default device to card 1, which is a Sound Blaster Live! (while card 0 is onboard). I have installed the gstreamer packages as recommended by ubuntuguide.org as well as a few others. My gstreamer-properties are set to ESD as my sink and ALSA as my source.

So far, I have fired up alsamixer and toggled analog/digital output jack with no results. While I was doing this I noticed the weirdest thing. If I turn PCM up past about 74, I get a piercing, and I mean ear-splitting, whine from my headphones/speakers. At lower PCM levels, there's a dull whine. This is not something I've heard before and I have no idea what's causing it.

Thanks.

---

### Post by CAE on 2005-06-08
Nevermind, problem solved.

---

