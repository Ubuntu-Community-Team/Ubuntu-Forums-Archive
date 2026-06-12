---
title: "Audiophile 2496 sound problem."
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by Leonin on 2006-05-14
Hi.
I have been using Kubuntu for awhile but I wanted to try Ubuntu. 
Anyway my problem is that I have a semi broken Delta 2496 card. It works automaticly in Kubuntu but in Ubuntu I have a angry hiss and no sound. 
The same thing happens in Windows XP but there have I found a work around, wich is locking the Codec Sample Rate at 44,100 in the M Audio controlpanel.
So my real question is, how do I lock the Codec Sample Rate in Ubuntu for my card? Are there anyway to install the maudio controlpanel?
I guess I have to edit some file, but since im beginner I have no idea where it is. I really hope that anyone on this boards knows how to do it. 
Thanks.

---

### Post by pellgarlic on 2006-05-14
hi - i have the exact same card - i had problems with it also when i first installed ubuntu, although not exactly the same as you...

i found that when trying to play back audio, it sounded kind of distorted, and "slowed-down", and like the high and low frequencies had been stripped away. 

i've heard that some people have success with fixing audio problems by disabling the "on-board" audio capabilities of the motherboard in the bios - you could try that for starters.

i had to install the multimedia codecs recommended here: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) to get my audio working properly. this would be recommended anyway, even if it doesn't fix your problem, as otherwise you won't be able to play certain file formats.

if you have done both of these things already, sorry, i don't have any other suggestions, except to say that i assume the card is too old to return to the place of purchase as "faulty", as it sounds like it is faulty by your description.

---

### Post by pellgarlic on 2006-05-14
me again! i think i found what you were looking for when i was messing about - 

open a terminal window, and type "gnome-volume-control". a "volume control" window should open. click on the "edit" menu, then select "preferences". in the small window that opens, scroll down and "tick" the tick-boxes for "multi track internal clock", "multi track internal clock default", and "multi track rate locking". 

i don't know if you'll need all of these, or if you may need more than these, but the ones i mention add new tabs to the 2volume control" window - "switches" and "options", which seem to allow selection of 44100 hz clock rate. hope this does the trick...

---

### Post by victor_c26 on 2006-11-11
I have the same kind of problem. The sound in Ubuntu just isn't as clear and detailed is in Windows XP. I have an Audigy ES, and I think the sampling rate is set to 22 KHz for some reason. I tried looking for it on the gnome volume control where you described, but the option just isn't there for some reason. Is there any other way to set the sample rate?\

I'd also like to ask another question. For some reason it says that the chipset on my Audigy ES is a SigmaTel STAC9721,23, but didn't Audigys have emu10k2 chipsets? Anyway I can tell Ubuntu, or the ALSA drivers that my Audigy is using an emu10k2?

---

