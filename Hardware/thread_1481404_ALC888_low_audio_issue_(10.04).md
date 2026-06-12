---
title: "ALC888 low audio issue (10.04)"
date: 2010-05-12
forum: Hardware
---

### Post by maclancer on 2010-05-12
I don't know if this is the right threat but I am having issue with the audio been playing stuff too low that I can barely ear it. I tried all type of fix from this forum before I posted this issue and nothing seen to work. I updated alsa to the latest version, I used alsamixer with everything up and nothing work. I tried the "options snd-hda-intel model=MODEL" fix and don't work either. Does anyone with a perfect working ALC888 can tell what to do? thank you!

---

### Post by khelben1979 on 2010-05-12
Tell us more about your hardware configuration:
```
lspci
```
and post to this thread.

---

### Post by dino99 on 2010-05-12
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-05-13
How about some more info. Is this an upgrade or fresh install?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

