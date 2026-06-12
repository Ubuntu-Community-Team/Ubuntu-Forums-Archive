---
title: "snd_hda_intel partially fixed."
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by spotman on 2006-06-12
Hello,

If you have a laptop with a recent intel chipset (probably others), then you may be using the snd_hda_intel chipset.

I have been racking my brain for a bit now trying to solve the randomness of this audio chip.  Sometimes it would work for me, others not.  When I used custom kernels it was even worse, even with the most recent alsa stuff built in manually into 2.6.16.20 and 2.6.17rc6.  

Anyways, part of the reason it's glitchy might be your bios.  I found I had to re-enable my modem and printer port to get audio.  I have no idea why, but there is a connection here.

my laptop is a lenovo t60.

as a side note, if anyone has any experience/luck with ati's powerplay system and it corrupting the graphics system, please advise :)

-spot

---

### Post by josys36 on 2006-08-04
Did you happen to get the modem to work? I can't seem to install the software to make it function.

Jason

---

