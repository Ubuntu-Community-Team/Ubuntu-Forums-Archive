---
title: "[SOLVED] Uninstall PulseAudio 8.04"
date: 2008-09-23
forum: General Help
---

### Post by Vince4Amy on 2008-09-23
I sell and maitain computers which I Install 8.04 on. However PulseAudio simply does not work for most people including myself.

Is there a safe way I can remove it and use ESD or something similar, I don't know why Pulse was included because I use "If it aint broke don't fix it" and whatever previous releases used was no broken. Are there any packages which will have to be installed in place of pulse and can I safely remove all packages with pulse in them.

---

### Post by ThrobbingBrain66 on 2008-09-23
Have you seen or tried this thread yet?  It configures PulseAudio the way that it should have been configured in the first place.  I would give that a try before trying to completely remove it.

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Vince4Amy on 2008-09-23
Yeah I will give it a try thanks, but will it be okay to uninstall all the pulse packages any way just incase.

---

### Post by Nepherte on 2008-09-23
The supplied thread to fix pulseaudio should work. You don't really have to uninstall pulseaudio, you can set everything to use alsa in system > preferences > sound instead.

---

### Post by Vince4Amy on 2008-09-24
No, I'm still getting problems with applications not producing any sound still. I have tried the above guides, thanks. Can I remove all pulse audio packages without anything breaking?

I'd like it so sound is configured the same way as 7.10 and earlier if possible.

---

### Post by Vince4Amy on 2008-09-24
Never mind, I've sorted it.

I removed all Pulse Audio packages and installed (Not Exact package names)

Esound
Esound-Clients
and gstreamer-esound

---

