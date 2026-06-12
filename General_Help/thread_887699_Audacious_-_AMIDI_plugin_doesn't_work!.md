---
title: "Audacious - AMIDI plugin doesn't work!"
date: 2008-08-12
forum: General Help
---

### Post by Diya on 2008-08-12
I've installed audacious, audacious-plugins, and audacious-plugins-extra.

My sound card:
```
Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
```

My sound card isn't capable of MIDI playback, as far as I know, but Audacious AMIDI plugin can do both hardware and software synth.

I followed [This]("http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/") How-To.

I've configured the AMIDI plugin according to the How-To, but still doesn't work! This is really frustrating.. help!

Timidity worked before, but I didn't like the midi quality it provided, so I completely removed it, hoping that AMIDI would solve all my problems.

---

### Post by Diya on 2008-08-12
I've finally fixed the problem after 12 hours of searching and trying different things. (Oh god, I'm so exhausted).

The cause of the problem:
1) Timidity Audio Plugin, it made Audacious play the default freepats linked to in timidity.cfg. (Causing a conflict)

2) The soundfont that I have downloaded is corrupt.

So, in order to fix the problem, all I had to do is:
1) Disable Timidity Audio Plugin in Audacious.
2) Download a new GM soundfont.

AMIDI plugin works perfectly now.

---

