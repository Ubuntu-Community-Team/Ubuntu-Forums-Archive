---
title: "Fast Track Pro as midi only?"
date: 2011-04-20
forum: Hardware
---

### Post by ScreenSilently on 2011-04-20
Hello,

I'm trying to setup my _Fast Track Pro_ with alsa.
While I get sound from my speakers, _no inputs or outputs are recognized_.
I tried to connect it with QJackCTL but I don't get any I/O in this too.
There's not a mixer on the (Volume Control) too.

I don't know what other information to provide.

Please someone help me.

Ubuntu/Linux are awesome, but that's the only reason I can't stay.

---

### Post by ScreenSilently on 2011-04-24
nobody?

---

### Post by cchhrriiss121212 on 2011-04-24
Have you checked alsamixer? (just type it in a terminal window)
Also unless you apply a patch, this device only works at a maximum of 16bit/48k due to bandwidth of USB 1.1. See here for more info:
[http://alsa.opensrc.org/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/M-Audio_FastTrack_Pro)

What software are you aiming to use?

---

### Post by ScreenSilently on 2011-04-27
"This sound device does not have any controls."

It can't find any controls as you can see.

I can hear sound but can't use the inputs.

---

