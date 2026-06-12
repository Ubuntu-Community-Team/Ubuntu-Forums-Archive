---
title: "[SOLVED] Alsa only works with one program at a time"
date: 2008-11-21
forum: Hardware
---

### Post by tmtan on 2008-11-21
Im running Intrepid and have alsa installed on a sony vaio. it has just an intel on board sound card. Long story short, the sound works great except the sound card only pays attention to one application at a time, for example if rythmbox is open, and then you pull up youtube, you only get sound from rythmbox (or whichever application is opened first). Secondly, the sound gradient is slightly messed up. when turning down the volume, when the bar is half way down, the volume is completely off. so 100% of the volume is in 50% of the bar, the other half of the gradient does nothing. is anyone else having these issues or have any ideas to fix them. thanks.

---

### Post by srilyk on 2008-11-21
It's probably... I forget the name ATM - it's flex or fusion or something. It pretends to be a good program to interface between your apps and the sound card, but it fails big time. Instead it just locks the card. You have to uninstall it and then set some... ahh! Pulse! Yeah, look up pulse audio - I found some help on the forums somewhere. A quick search through the archive should turn up some good info. HTH,

Good luck!

---

### Post by Amorget on 2008-11-21
Which Vaio do you have?

---

### Post by tmtan on 2008-11-21
Sony Vaio VGN-FZ140E

---

### Post by tmtan on 2008-11-21
switching everything over to pulse audio manager did the trick for sharing the sound between apps

[http://ubuntuforums.org/showthread.php?t=843012highlight=pulse+program+sound](http://ubuntuforums.org/showthread.php?t=843012highlight=pulse+program+sound)

If anyone still has an idea on how to make the volume slider use its entire path instead of 100% of volume in 50% of the sliders bar, feel free to let me know.

---

