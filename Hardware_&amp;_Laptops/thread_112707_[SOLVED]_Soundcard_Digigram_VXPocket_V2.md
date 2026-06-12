---
title: "[SOLVED] Soundcard: Digigram VXPocket V2"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by ibanez88 on 2006-01-04
I'm having a devil of a time trying to get the Digigram VXPocket V2 sound card to work in Linux.  This is a PCMCIA card for my laptop.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Digigram&card=VXpocket+V2&chip=&module=vxpocket](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Digigram&card=VXpocket+V2&chip=&module=vxpocket)

I've tried following this to a tee, without success on both Toshiba Satellite 5105 and Averatec 1050-EB1 laptops.

Has anyone got this card working?

---

### Post by ibanez88 on 2006-06-08
Anyone?

---

### Post by nabdan on 2006-11-28
Hi

I'm also interrest to run a Vxpocket v2

I have you managed problem ?

If anyone can help :mrgreen: 

Bye !

---

### Post by nabdan on 2006-11-28
I found that:

I will try tonigth and let you know.

Any advices are more than welcome !

[http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/](http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/)

Bye all

---

### Post by nabdan on 2006-12-07
Hi all,

previous link works, I can use my Digigram Vxpocket v2 with it.

[http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/](http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/)

Just need to copy files :) 

Now make Jack running (seems not easy) :-k 

Bye.

---

### Post by ibanez88 on 2007-07-18
Thank you nabdan!  I'm not sure what was different this time, but I tried out your solution on a fresh install of Fiesty and it worked!  (At least playback, I haven't tried to record yet.) 

I set the card value to 0 instead of 1, plus I blacklisted my other soundcard from modprobe. 

 :guitar:

---

