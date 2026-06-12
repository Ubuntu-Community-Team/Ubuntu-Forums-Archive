---
title: "ASUS K50IJ + Ubuntu 9.04 = no sound"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by WestCity on 2009-10-17
Hello, I used search and found some posts about this issue, but I think it was written for more experienced users than me... Please, write a "step by step" for me. I really want to have sound on my laptop. :)

---

### Post by WestCity on 2009-10-24
I solved this problem:


1. Updated everything with System -> Administration -> Update Manager.

2. Installed Alsa 1.0.20 (driver, lib, utils).

3. Added 2 extra lines in the end of alsa-base.conf:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
 
 4. Installed hda-verb and added 1 extra line in rc.local just before the line "exit 0":

hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM


And sound was working after restart... :smile: 

Hope, it will help to someone who has similar problems with sound and Alsa drivers on ASUS K50IJ.

---

