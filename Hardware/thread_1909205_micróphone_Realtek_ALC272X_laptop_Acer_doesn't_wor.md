---
title: "micróphone Realtek ALC272X laptop Acer doesn't work"
date: 2012-01-14
forum: Hardware
---

### Post by pepercut on 2012-01-14
Buenas he buscado en casi todo google como configurar el microfono en mi ubuntu pero no ha sido posible 

Aqui adjunto la información que capturo el sh del Alsa
[http://www.alsa-project.org/db/?f=cbb24390843a5288de7a47357e2d5a17a80b5a2f](http://www.alsa-project.org/db/?f=cbb24390843a5288de7a47357e2d5a17a80b5a2f)

y esta las configuraciones que he probado en el alsa-base.conf y no han sido efectivas
options snd-hda-intel model=acer
options snd-hda-intel model=ALC272
options snd-hda-intel probe_mask=1 
options snd-hda-intel model=laptop position_fix=1 enable=yes


de antemano muchas gracias por cualquier ayuda que puedan dar

---

### Post by madvinegar on 2012-01-15
I had the same problem in as acer aspire one 250 and I did the following to fix it.

Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

You can then set back your overall sound balance as it was before so as to get sound from both of your speakers.

This should do the trick.

---

### Post by pepercut on 2012-01-16
> **madvinegar said:**
> I had the same problem in as acer aspire one 250 and I did the following to fix it.

Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

You can then set back your overall sound balance as it was before so as to get sound from both of your speakers.

This should do the trick.

thanks in advance actually I have Pulse Audio volumen control and i do your indications but has not worked. I think the problem is that the internal microphone does not detect for Ubuntu but i don't know why.

---

