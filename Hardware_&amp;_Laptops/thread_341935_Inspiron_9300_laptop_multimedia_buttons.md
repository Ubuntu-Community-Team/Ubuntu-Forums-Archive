---
title: "Inspiron 9300 laptop multimedia buttons"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by jfinkels on 2007-01-19
Ubuntu 6.10 on Dell Inspiron 9300 laptop (about one year old). Like the newer Inspiron models, it has multimedia buttons on the front (the front bezel I guess you would call it) including the following: volume mute, volume down, volume up, play/pause, previous track, next track, stop. 

The volume buttons work, but they only affect the "Master" channel when I open up the ALSA mixer. This is a problem for several reasons. First, headphones are an entirely different channel and aren't affected at all. Second, when not using headphones, the regular PC speakers require volume on both the "Master" channel and the "Master Mono" channel, otherwise you only get half the sound coming out of the speakers (took me a long time to figure out how to fix that :P).

On top of all this, the play/pause, previous, next, and stop buttons all have no effect.

So my question is this: is there a set of drivers or some sort of protocol for enabling buttons like these? If so can someone point me in the right direction? Thanks!

---

### Post by Ravanous on 2007-01-19
Hey, I have the same laptop & have never tried any of the buttons on the front save for the 3 volume buttons :D

It would be cool if these could be enabled to work within VLC or some other application.

edit:
After looking at [this]("http://rtr.ca/dell_i9300/") page, it looks like using [xmodmap]("http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html") will get the job done.
(Look at Installation Note #8, there is a script there for getting the job done)

I am gonna try it over the weekend and see how it goes.

---

