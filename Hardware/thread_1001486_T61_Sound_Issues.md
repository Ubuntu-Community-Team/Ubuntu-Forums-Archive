---
title: "T61 Sound Issues"
date: 2008-12-04
forum: Hardware
---

### Post by Startacus on 2008-12-04
I have a T61 with 8.10 and my sound has just randomly stopped working. The sound was working before but now it has randomly stopped working. As far as I know nothing is muted. 

Thanks for the help.

---

### Post by optimisteo on 2008-12-06
exact same problem here!
never had an issue before upgrading...

i have to reboot to get sound again

any workaround?

---

### Post by optimisteo on 2008-12-06
actually there is!

try:  alsa force-reload 
in the console

works for me!

---

### Post by Startacus on 2008-12-06
That didn't work for me. My sound doesn't start working again when I restart either. It just stopped working and hasn't worked since.

---

### Post by David Valentine on 2009-01-27
I'm in the same boat.  My T61 sound has worked out of the box on Hardy and Intrepid, but suddenly stopped earlier today and I cannot get it going again, despite following several howto's.  I've checked and rechecked the various volume controls, added "options snd-hda-intel model=thinkpad" to /etc/modprobe.d/alsa-base, and still no joy.

UPDATE:  I have joy.  Here's what I did:```
$ alsamixer -Dhw
```then ensure that not only the master and pcm are unmuted, but also the headphone, even though I'm not using headphones.

---

### Post by optimisteo on 2009-01-28
Cool!
According to manpage the h is for help the -D <device identification>
What's the w ?

regards,

Opti

---

### Post by David Valentine on 2009-01-29
> **optimisteo said:**
> According to manpage the h is for help the -D <device identification>
What's the w ?It's actually not "h" and "w", but "hw", which is required by the "D" option.  I don't know what "hw" means or what other hardware options there are.

---

