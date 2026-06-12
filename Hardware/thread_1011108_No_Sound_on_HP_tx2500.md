---
title: "No Sound on HP tx2500"
date: 2008-12-14
forum: Hardware
---

### Post by soldierx1 on 2008-12-14
Ok so whenever I go to play music I can't hear anything coming from my laptop, I also don't get anything from the headphone jacks. Also when I boot up there is no music or sounds. However today I managed to get some sounds to play. Ok so I went into the terminal to try some things that the page [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) said to do and when I pressed the right or left arrow keys a beep sound was made! So I kept pressing the arrows and it kept beeping, now I also was trying to play music at the same time but heard nothing, however in between some of the beeps I heard bits of the music! Can anyone help me? I have Altec Lansing speakers on my hp pavilion tx 2500 laptop.

---

### Post by Favux on 2008-12-16
Hi soldierx1,

First you need to go to System>Preferences>Volume Control or right click on icon at top right and Open volume control.  Make sure all the volume sliders are up, including PCM, Intrepid can accidentally mute you on install.

To your /etc/modprobe.d/alsa-base file try adding the following line:

options snd-hda-intel index=0 model=toshiba position_fix=1

If that doesn't work you might also try:
options snd-hda-intel index=0 model=acer

---

