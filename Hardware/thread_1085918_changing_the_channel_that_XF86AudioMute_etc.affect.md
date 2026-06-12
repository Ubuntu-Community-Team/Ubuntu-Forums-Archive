---
title: "changing the channel that XF86AudioMute etc.affects"
date: 2009-03-03
forum: Hardware
---

### Post by Askr on 2009-03-03
hi,
im using ubuntu 8.10 with the 2.6.27-13 kernel and gnome 2.24.1, and alsamixer v1.0.17 on my Sony Vaio VGN-NS12 M/W and kinda everything works absolute fine, except one thing
these neat multimedia keys just do what they are supposed to do, except XF86AudioMute, XF86AudioLowerVolume and XF86AudioRaiseVolume

these keys are recognized by the system and are doing something, they let the soundcontrol overlay pop up and are changing one channel, but not the right one.
in system > preferences > keyboard shortcuts are these keys mapped like in the screenshot and they work. but they affect the wrong channel - they affect the "in-gain" channel from the oss mixer (see screenshot)

now to the questoion: how to change the channel to "Master" or "PCM" from the alsa mixer (i'm using that one)? i think that somewhere in the system must be noted which channel these standard keybinds affect - but i can't figure out where ^^

does someone knows how to change this channel?

---

### Post by Askr on 2009-03-05
anybody who knows this? :<

---

### Post by jon_mease on 2009-05-05
Hi, I stumbled upon your post while trying to figure out how to do this in Ubuntu 9.04 and wanted to post what I found.

In Ubuntu 9.04 it seems the XF86Audio* keys are bound to the "Default Mixer Tracks" option in the System->Preferences->Sound dialog box.

Hope this works for you as well!

-Jon

---

