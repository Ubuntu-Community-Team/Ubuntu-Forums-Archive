---
title: "Asus K50*"
date: 2009-08-20
forum: Hardware
---

### Post by mustangzach on 2009-08-20
Okay, about a week ago, I upgraded a friend to Ubuntu. They have an Asus K50 laptop. Well, I couldn't get the wireless to work, so I installed the jaunty-backports-modules package. It worked like a charm.


However, now I must deal with the dreaded vt1708s sound chip. It worked iirc when we first booted it, once it was installed, and seemingly until I installed the backports package. Could that have broken it?

It shows up under volume control, but every time she tries to test the audio in the sound control panel, it gives this error:
> 
audiotestsrc wave=sine freq=512
audioconvert ! audioresample ! gconfaudiosink:
could not uopen audio device for playback
so yes.. it seems like it should be working, but it fails to do so. Like I said, volume control recognizes the chipset and everything, it just doesn't play sound.

Help anyone? She loves the interface, btw.

---

