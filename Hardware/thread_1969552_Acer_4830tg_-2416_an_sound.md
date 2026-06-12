---
title: "Acer 4830tg -2416 an sound"
date: 2012-04-30
forum: Hardware
---

### Post by d3lfino on 2012-04-30
Hi all,
I've installed 11.10 before and 12.04 now on my new notebook.
Everytings works fine (also optimus with bumblebee) except audio....
I've tried with gstreamer-properties to select alsa ,didnt work.
I'tryed to use alsa-analizer to select EAPD on the node 0x01b ,didnt work
I have read all the thread on this and on the italian ubuntu forum....google...no solutions.....

cuold someone help me please????

---

### Post by CHFFriday on 2012-04-30
d3ifino,
Are you saying you have NO audio? No Audio with any thing?

CHFFriday

---

### Post by d3lfino on 2012-04-30
yes...no audio!!!from internal speaker from the jack...from hdmi....no audio

---

### Post by d3lfino on 2012-05-01
no one have any idea? :(

---

### Post by Lagartos on 2012-05-01
Exactly same problem for me.

---

### Post by Lagartos on 2012-05-01
Suspend&resume brings sound back, but still hope to load system already with sound.

---

### Post by d3lfino on 2012-05-03
also for me after a suspend and resume i can hear audio

---

### Post by d3lfino on 2012-05-20
No one have an idea???
no one have this audio device ???

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

---

### Post by kalhusoru on 2012-06-08
i have already reported it as a bug and am waiting for a fix. in the meantime, suspend/resume fixes the sound temporarily. i hope they fix the bug soon. must be a problem with ubuntu pulse audio configuration.

---

