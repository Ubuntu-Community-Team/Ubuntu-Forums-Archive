---
title: "Pulseaudio not working with SB16 (ISA)"
date: 2008-05-15
forum: Hardware
---

### Post by Diskdoc on 2008-05-15
- Fresh Hardy install + latest updates
- snd-sb16 loaded (edited /etc/modules manually)
- Sound works using just ALSA (though irritating clicks in sound)
- Using Pulseaudio fails. Errormessage from the sound setup screen:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Any advice?

---

### Post by soxs on 2008-05-15
I get this very same error.. nasty. Currently I am forced to use alsa. :-/

---

