---
title: "Roland UA 1G Soundcard support"
date: 2010-03-05
forum: Hardware
---

### Post by icyzer on 2010-03-05
Heyall

A friend of mine has been quite interested in Ubuntu for a while, and is in doubt about installing it. But he is into music and uses some hardware that I'm not known with.
A Roland UA 1G soundcard thingie. He won't install Ubuntu untill he knows whether or not his soundcard is supported. 

I've been looking at some of [the supported hardware list of alsa]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Roland_Edirol") but no luck there, do you guys know or think there is any chance this card is supported by alsa/ubuntu. Or is there an easy workaround to get it working?

---

### Post by icyzer on 2010-03-06
Noone?

---

### Post by bigsuccess on 2010-06-15
This is a bit old but it was few from search results I thought I'd add to it for the record...

I'm have run lucid with 1.0.21 ALSA and it was detected as a normal usb sound card with the card's "advanced driver" mode set to off.

I was hoping an upgrade to ALSA 1.0.23 would detect it in advanced driver mode. It didn't for me but I'm still running lucid 10.04 and alsa 10.0.23 and it still works as a normal sound card...

According to cakewalk the difference for this card with the driver mode setting off/on is 24-bit/44kHz (in and out) vs 24-bit/96kHz (in or out) respectively.

So what I've found is it'll work out of the box as a normal usb sound card, but not in advanced driver mode which gives you the extra quality goodness. I'm not a sound guy, I'm more of a computer guy so higher numbers appear better - but reality might be that unless you're trying to match the source the 44kHz or 96kHz difference isn't even all that important. It would be great to get it working to find out for sure but I found just having the card was a massive improvement over on-board.

---

