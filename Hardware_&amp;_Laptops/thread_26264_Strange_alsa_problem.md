---
title: "Strange alsa problem"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by NickB on 2005-04-12
Hi,

I recently switched to Ubuntu 5.04 from Debian unstable, and everything worked fine after the install.  However, I removed my TV capture card the other night, and now I'm getting some strange behavoir.

Hotplug is recognizing my Ensonique 1371 card and loading all the right alsa divers (snd_ens1371 et. al.), but it's not working at all.  When I cat /proc/asound/modules, I get nothing, and /proc/asound/cards says there are no cards installed (ditto with aplay -l).

I can't figure for the life of me what happened and why hotplug can see the card (and so can lspci etc.), but the alsa drivers won't talk to it.  I've never had to specify any options for the driver, nor have I ever had any problems with it in the past.  As I said, it worked fine until I removed my TV capture card, and that's *all* I did.

Thanks in advance for any help/advice anyone can give me.
Nick

---

### Post by NickB on 2005-04-12
I resolved the problem by shuffling my cards around.

Nick

---

