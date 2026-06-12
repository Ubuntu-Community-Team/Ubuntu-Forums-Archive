---
title: "Sound output to both laptop speaker and headphone"
date: 2008-07-22
forum: Hardware
---

### Post by D.Sync on 2008-07-22
I'm currently using Acer Aspire 5920G and I'm having issue with the headphone.

Whenever I jack in my headphone to the jack port, the sound comes from both my laptop speaker and my earphone. However, the volume on my headphone is very small. I would like to mute the speaker when I plug in my headphone.

Anyone can rectify such problem? Thanks.

I'm using Realtek ALC888 and HDA Alsa Mixer.

---

### Post by Dark_Stang on 2008-07-22
Try opening up the file"/etc/modprobe.d/alsa-base" and add "options snd-hda-intel model=laptop" to a new line and reboot.

---

### Post by imon9 on 2008-07-22
sudo gedit/etc/modprobe.d/alsa-base

add this to the last line:
options snd-hda-intel model=acer

save it and reboot

---

### Post by terrorcide on 2008-07-22
I have the same laptop and neither of these solutions work for me. I have to manually go into the alsa mixer and mute "surround" when I'm using headphones

---

### Post by D.Sync on 2008-07-22
> **terrorcide said:**
> I have the same laptop and neither of these solutions work for me. I have to manually go into the alsa mixer and mute "surround" when I'm using headphones

Thanks much for the solution. Never thought it would be that easy. :)

---

### Post by heinchen on 2008-09-01
i have a acer Extensa 2902 LMI

Chip:Audio Realtek AC97 
Driver: 5.10.0.5420 Version

And i have a 5.1 speakersystem Concept Magnum from "teufel"
and another output System Keenwood amplifier with other 5.1 Speaker.

I have the same Problem, but the matter is happen recently.

One week before the happening I installed new Audio Driver, because I have uninstalled accidently the old drivers. (but I believe this was not the cause)

I believe it is a hardware-problem, because I have always problem with mediplayer classic and avi-Files. The loudness go back after 30 min Video-play-time.

I believe the cause is: the laptop don't works with powerful speakersystems. The Hardware isn't concepted for this Systems.

Any other Ideas,
Thanks for Reply

PS: Sorry for my bad english

---

### Post by ambawatajay on 2008-09-15
I am using the same model and the same has been fixed in Intrepid.
Still no luck in Hardy.:(

---

### Post by olejorgen on 2008-09-29
[http://ubuntuforums.org/showthread.php?t=806620&highlight=headphone](http://ubuntuforums.org/showthread.php?t=806620&highlight=headphone) maybe?

---

