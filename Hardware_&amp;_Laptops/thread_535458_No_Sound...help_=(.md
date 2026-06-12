---
title: "No Sound...help =("
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by kittyloaf on 2007-08-26
I installed Ubuntu yesterday, and a friend helped me to get it working pretty good today.

But, there is no sound at all =(

i followed an alsa-how-to for ubuntu. When i check alsamixergui it says Chip: Realtek ID 268 HDA Intel

and when i play a song in a music player, like xmms, the visualizers move, but no sound =(  ...and it's not muted.


Can anyone help? ^^

---

### Post by ddrichardson on 2007-08-26
There is a good [howto]("http://ubuntuforums.org/showthread.php?t=205449&highlight=intel+hda+sound") here, if it doesn't work then log a bug report with ALSA.

---

### Post by gundumfx on 2007-08-26
> **kittyloaf said:**
> I installed Ubuntu yesterday, and a friend helped me to get it working pretty good today.

But, there is no sound at all =(

i followed an alsa-how-to for ubuntu. When i check alsamixergui it says Chip: Realtek ID 268 HDA Intel

and when i play a song in a music player, like xmms, the visualizers move, but no sound =(  ...and it's not muted.


Can anyone help? ^^

well here is what you should do well i had ubuntu for a long time an i use fedora core 7 but when i got ubuntu i could not watch youtube videos an music an more it keeps freazzing well 
Open the terminal the in terminal copy an paste this 

sudo apt-get install ubuntu-restricted-extras

an When you've got that screen with the license agreement, hit <tab> to highlight "OK", then <enter>. The install process will continue.

ok tell me if this works

---

### Post by darenw on 2007-08-26
any chance you've got jackd running?   last winter, when i was using the jackd system (jackaudio.org)  to connect various sound/music apps, most  alsa-based apps stopped working, or weren't reliable. firefox and various mp3/mpeg players quit.  even if there was some sort of jackd/alsa thingy to keep everything working, it didn't for me.   some apps will start jack automatically, so maybe logout/login or restart the machine to restore proper operation?

---

### Post by kittyloaf on 2007-08-26
darenw, nope, it doesn't work at all...

---

