---
title: "Sounds - Where is alsaconf?"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by BanskuZ on 2005-07-26
Hi, I have some problems with sound. Other distros (MEPIS,Debian...etc) include program called "alsaconf". Ubuntu doesn't include that program, even "alsa-utils" is installed. So, where I can get "alsaconf"/How to get sounds working?

Soundcard: Soundblaster Live!  :mad:
Sorry for my bad englisssh.

---

### Post by Xian on 2005-07-26
You might read [THIS](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1) page and skip down to the 'Setting up modprobe and kmod support' section. Hoary uses a 1.0.8-4 version of alsa so you'll need to use the snd-card-emu10k1 notation in that configuration (as noted in the text).

---

### Post by varunus on 2005-07-26
Hoary, for some reason, released with a problem with the Soundblaster Live.  Follow the instructions in this thread (stickied in this forum):
[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)

It'll get you going with sound.

---

