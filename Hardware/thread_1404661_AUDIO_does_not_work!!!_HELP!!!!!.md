---
title: "AUDIO does not work!!! HELP!!!!!"
date: 2010-02-11
forum: Hardware
---

### Post by starsky84 on 2010-02-11
Hi, I'm a new linux user, I just installed ubuntu 9.10 but the audio doesn't work! I hear nothing.. and also the mic is mute! Can somebody help me? I tryed with the alsa drivers but I think it's my fault, I know little about linux. My pc is a hp dv32250el and my sound device is Intel HDA. Thanks for your support!!!

---

### Post by ajgreeny on 2010-02-11
Open a terminal and enter ```
alsamixer
```A mixer application will open in the terminal with many of the sound levels you don't normally see.  Make sure nothing is muted or set too low.

You use the cursor keys to navigate from slider to slider, and to raise and lower them, "M" to mute/unmute, tab to move from Playback to Capture to All, and Esc to save and leave it.

Also install padevchooser from the repos to make sure that things work properly.

---

