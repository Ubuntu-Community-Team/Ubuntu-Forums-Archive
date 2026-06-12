---
title: "Sound issue with Gnaural2"
date: 2008-07-19
forum: Hardware
---

### Post by L815 on 2008-07-19
I finally got the issue with flash & sound fixed with a guide found on here.
Though in OpenSUSE it works without any issues.


Another issue I've encountered is using Gnaural2 or even Gnaural.

If I have any application using sound, Gnaural2 fails to play. This sucks because I want to play it with music. On Vista it works fine.

The exact error at the bottom panel of gnaural2 is: 
- Init Audio System: Host error,[device 0]

I was wondering if there is a way to fix this?


EDIT:
Also if I am running Gnaural2, and open a program that requires sound, it will cause that program to freeze :/

---

### Post by Aielyn on 2009-07-27
Although it's very much late, since the question was asked over a year ago, I figured I'd provide the answer so other people who search for an answer to this question will find this answer.

The problem is that Gnaural2 is coded to use OSS for sound, while Ubuntu's standards are ALSA and Pulse, I believe. To get Gnaural2 to work in Ubuntu, install the alsa-oss package via synaptic. Then, edit the Ubuntu menu via "Main Menu", go to wherever Gnaural2 shows up (it showed up under Application-Other on my system), and edit the "properties" of that option so that rather than saying "gnaural2 %f", it says "aoss gnaural2".

EDIT: Similarly, if you want to open it via command line, run "aoss gnaural2" rather than merely "gnaural2"

---

