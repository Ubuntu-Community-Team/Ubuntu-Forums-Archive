---
title: "Sound = bye-bye"
date: 2008-09-11
forum: General Help
---

### Post by Inane_Asylum on 2008-09-11
I **finally** got sound working on my Toshiba Satellite A205-S5809 a few weeks back.  It was the usual hda-intel alsa-base issue...anyway, I was cleaning house a little last night and uninstalled several programs I didn't use.  The ones I can remember are Rosegarden, VLC Media Player, Blender, Superkaramba, and **maybe** a couple others.  Nothing seemed to have gone wrong until I booted up my computer this morning, and...no sound.](*,) I checked /etc/modprobe.d/alsa-base, and my options snd_hda_intel line is still there, but cat /proc/asound/cards is spitting out "no soundcards" again.  I suspect uninstalling Rosegarden or VLC may have something to do with it, but I'm still kinda green with Linux.  Would uninstalling programs kill a shared library needed for sound?:confused:

Any and all help would be greatly appreciated...

P.S. I'm at work and not around my computer at the moment, so I'll either have to walk my wife through it (not likely she'll want to), or fiddle with it when I get home.  I'm thinking about reinstalling the programs one by one, rebooting, and checking the sound...whatever...

---

