---
title: "SB Audigy 2 NX Woes"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by TimTheEnchanter on 2005-06-21
Hi everyone,

I'm fairly new to linux and totally new to Ubuntu, and having some serious sound card issues.

On a fresh install, my sound card is detected (cat /proc/asound/cards) and is in position 0 in the list. However, the mute button will remain on at all times. I've tried to change the settings in alsamixer but so far that's proved fruitless.

I then tried to follow the guide at [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+NX.&chip=UNKNOWN&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+NX.&chip=UNKNOWN&module=emu10k1)
and was unsuccessful there as well. I encountered errors when I got to the "modprobe" step of that guide, and when I restarted Ubuntu had stopped detecting my card.

Does anyone have any advice on how to get this working? I'm willing to reinstall Ubuntu and start fresh if it'll help.

---

### Post by WMCoolmon on 2005-07-12
You probably need to unmute one of the channels in alsamixer (pressing "m" will toggle mute).

If you already tried that, not sure.

---

