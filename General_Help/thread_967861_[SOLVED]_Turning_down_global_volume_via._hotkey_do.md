---
title: "[SOLVED] Turning down global volume via. hotkey doesn't work"
date: 2008-11-02
forum: General Help
---

### Post by eZtaR on 2008-11-02
I can't adjust the volume via. the hotkeys specified in System > Preferences > Keyboard Shortcuts.

The volume 'dialog' shows up and the bar reacts to the hotkey, but it doesn't affect the volume knob next to the clock (see screenshot).

Any pointers on how to fix this?

[screenshot](http://dl.getdropbox.com/u/230132/audio)

---

### Post by eZtaR on 2008-11-02
Here's what jdong advised me to do to fix the problem, which worked :D

<jdong> eZtaR: ok first off, which is correctly adjusting the volume?
<jdong> eZtaR: ack where's my coherent train of thought today, let me clarify:
<jdong> the problem is, sometimes sound drivers are wacky enough that the "master channel" is difficult to correctly detect.
<jdong> in your case, the volume hotkey system and the mixer applet have differing opinions what the master channel is.
<jdong> my question is, which is right?
<eZtaR> The one next to the clock ;)
<jdong> eZtaR: do you know what is the name of the channel it is controlling?
<eZtaR> hda ati sb?
<eZtaR> (alsa mixer)
<jdong> eZtaR: open up the full mixer program, play with the up down bar on the panel applet and see which channel is the one that's sliding
jdong> eZtaR: go to System->Prefs->Sounds
<jdong> eZtaR: there's a combo box to set which mixer(s) to control with the hotkeys

---

