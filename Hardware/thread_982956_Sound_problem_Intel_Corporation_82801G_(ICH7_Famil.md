---
title: "Sound problem: Intel Corporation 82801G (ICH7 Family)"
date: 2008-11-15
forum: Hardware
---

### Post by MasterSander on 2008-11-15
At first I couldn't get it to play through speakers, only through headphone, but then I added a line to /etc/modprobe.d/alsa-base, saying options snd-hda-intel model=medion and now I can play through speakers if I put front open (not PC speakers) and that's where the problem is. I recently bought a 5.1 surround system and only the headphones work, I can't configure it to change to center etc. Anyone can help me, or anyone have the same sound card?

---

### Post by MasterSander on 2008-11-15
anyone?

---

### Post by MasterSander on 2008-11-16
bump

---

### Post by MasterSander on 2008-11-16
bump

---

### Post by MasterSander on 2008-11-16
bump

---

### Post by pacofvf on 2008-11-16
try:
$ alsamixer -c 0

---

### Post by MasterSander on 2008-11-21
yeah I know that gives me the audio preferences from alsamixer instead of pulseaudio but I've had the problem since forever so that didn't really help. Thx anyway

---

### Post by MasterSander on 2008-11-21
Anyone? I'd really much rather be using linux than windows

---

### Post by MasterSander on 2008-11-22
bump

---

### Post by lopoetve on 2008-11-22
As much as you don't want to hear it, it seriously looks like Alsa + the hda-intel drivers don't work well at all right now.  :(  I'm about to give up on mine and go back to vista full-time with cygwin, or ubuntu in a VM for my programming.  Have to be able to listen to music.

---

### Post by MasterSander on 2008-11-22
yeah that's the problem, I constantly listen to music and it's k when I'm not using my 5.1, but otherwise it just sucks

---

### Post by MasterSander on 2008-11-23
bump

---

### Post by MasterSander on 2008-11-24
bump

---

### Post by plunder on 2008-11-24
see if this helps you, i did something similar to get mine working


[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

-p

---

### Post by MasterSander on 2008-11-30
Doesn't help, already seen that guide before ;P Thx though

---

