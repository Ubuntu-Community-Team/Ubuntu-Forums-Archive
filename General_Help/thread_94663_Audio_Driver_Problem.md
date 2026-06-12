---
title: "Audio Driver Problem"
date: 2005-11-24
forum: General Help
---

### Post by webzila on 2005-11-24
I just installed Ubuntu 5.10 on an old pc that I have.
This computer has a SoundBlaster ISA PnP sound card.
I am not sure that the sound card is even installed properly. Everytime I try to play audio or even record something I get an error saying: Error loading the sound driver device /dev/dsp could not be opened.

I checked the packages and ALSA seems to be installed.
I am very new at this...how do I check to see if the sound card is even recognized by the system?
Are there drivers that I can install for an Sound Blaster ISA sound card - I dont even recall if its SB Live or just SB-16.

I also have another SB-Live PCI card. If I insert it will Ubuntu automatically detect it or is there something that I have to do?

Thanks

---

### Post by webzila on 2005-11-24
Here is what I have tried since posting this message:

I just tried the following without any luck:
sudo modprobe snd-pcm-oss
sudo modprobe snd-pcm-mixer-oss

I am guessing that changes the driver to OSS. How do you change back to ALSA?

I also tried the following:
sudo apt-get install udev

That didnt help either.

I tried installing and running isapnp program....it sees the Creative AWE64 sound card but I have no clue on how to edit the configfile and their instructions dont explain it.

Also I downloaded the ALSA-OSS Wrapper (AOSS) -- not sure how to use it or if this would even help.

:confused:

---

### Post by mallternative on 2005-11-26
I have a Soundblaster AWE64 too. 
I forgot to put it in the computer before installing Ubuntu! [whacks self fairly in the forehead.]
Now I don't know what to do! There's no mention of it in the device manager as far as I can tell . . 
Let's see. I'll have to google more.

---

### Post by jliedeka on 2005-11-26
There'sa lot of info out there for using OSS drivers for AWE-64 and old ISA SBs.  If you want ALSA, the two best reosurces are the ALSA project page and the ALSA-Configuration.txt file in the kernel sources docs.

For the ISA card, you may want to check out the ISAPnP HOWTO.

---

