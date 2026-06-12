---
title: "Switching between sound-cards"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by SLilburn on 2005-06-23
I recently installed Ubuntu, for the first time (although I've been using Fedora Core 3 for a while, I still consider myself a card-carrying n00b). I had an issue with the monitor being at a tiny resolution, which I managed to resolve on my own by running the configuration script to XOrg again; however, I have had issues with sound -- namely, I haven't been getting any.
I'm pretty sure my issue is that I have two soundcards in the computer, my SoundBlaster (the one I want to use) and the on-board card. At the moment, the on-board card is designated hw:0 and the SoundBlaster hw:1.
I used KDE and was able to get sound through that control panel (by placing hw:1 in there) but GNOME has no ability to say which card I want to use (and I can't figure out how to run any ALSA configuration programs or scripts).
I've, so far, checked alsamixergui (which says the on-board card is the sound output), placed snd-emu10k1 in /etc/modules and made sure that the sound was turned up in the mixer and the speakers were on (gotta cover all bases).

Any help with getting ALSA to use the SoundBlaster as the soundcard would be much appreciated.

(P.S.: Would it be possible, in future, to include a sound-card selector within the installer like Fedora Core?)

EDIT: fixed problem by building ALSA again, configuring the install for emu10k1.

---

### Post by FrzzMan on 2005-06-23
[QUOTE=SLilburn]I recently installed Ubuntu, for the first time (although I've been using Fedora Core 3 for a while, I still consider myself a card-carrying n00b). I had an issue with the monitor being at a tiny resolution, which I managed to resolve on my own by running the configuration script to XOrg again; however, I have had issues with sound -- namely, I haven't been getting any.
I'm pretty sure my issue is that I have two soundcards in the computer, my SoundBlaster (the one I want to use) and the on-board card. At the moment, the on-board card is designated hw:0 and the SoundBlaster hw:1.
I used KDE and was able to get sound through that control panel (by placing hw:1 in there) but GNOME has no ability to say which card I want to use (and I can't figure out how to run any ALSA configuration programs or scripts).
I've, so far, checked alsamixergui (which says the on-board card is the sound output), placed snd-emu10k1 in /etc/modules and made sure that the sound was turned up in the mixer and the speakers were on (gotta cover all bases).

Any help with getting ALSA to use the SoundBlaster as the soundcard would be much appreciated.

(P.S.: Would it be possible, in future, to include a sound-card selector within the installer like Fedora Core?)

EDIT: fixed problem by building ALSA again, configuring the install for emu10k1.[/QUOTE]
 I think I'm going to bump this thread...

---

