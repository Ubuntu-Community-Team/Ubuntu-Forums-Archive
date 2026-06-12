---
title: "how do I disable all the updates regarding to sound?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by just_linux on 2009-01-23
new updates always F*s my sound system. 
I set it up now and I do nt want any one F with it . 
How can I disable updates witch are regard to my sound system . 
Thanks :popcorn::p

---

### Post by Shazaam on 2009-01-23
1. Open Synaptic (System>Administration).
2. Lower left, click "Status".
3. Upper right click "Search".
4. In the search box that opens type in "pulse" (without the quotes). This should give you a list of all pulse-audio files; the ones with a green box are installed.
5. Highlight the ones you need, then go to "Package>Lock version" and check the box. The file will then be in a list called "Pinned" and will be ignored during update checks.
Other file names to search for= "alsa" and anything related to your sound hardware/sound card.
One thing you need to remember is other updates may affect the sound system. If you have special drivers installed for a particular piece of hardware you will probably need to re-install them after a kernel update.

---

