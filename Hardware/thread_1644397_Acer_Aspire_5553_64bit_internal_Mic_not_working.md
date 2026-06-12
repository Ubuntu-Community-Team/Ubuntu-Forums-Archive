---
title: "Acer Aspire 5553 64bit internal Mic not working"
date: 2010-12-13
forum: Hardware
---

### Post by kdavies on 2010-12-13
Hi 

Please can you help.

Recently got an Acer Aspire 5553 with Ubuntu 10.10 installed which I am very pleased with.:D

The internal microphone is very noisy.

alsamixer reports it to be Realtek ALC271X.

The module loaded is snd_hda_intel

In /etc/modprobe.d/alsa-base.conf
I now have 
options snd-hda-intel index=-2 model=auto
I have also tried model=acer and acer-aspire from HD-Audio-Models.txt

I have the alsa-info.sh script output [here]("http://www.alsa-project.org/db/?f=9f294bda9abb5aa2855ffc4d65c4c37c62121db8")

Any ideas?

---

### Post by kdavies on 2010-12-24
Have added the lines

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

To /etc/modprobe.d/alsa-base.conf 

Although it is quiet, the mic now works:-))

---

### Post by Refresh100 on 2011-02-27
What internal mic? I have the same laptop and don't have a built-in one, or do you mean the jacks on the side?

---

### Post by kdavies on 2011-02-28
Hi, it cant be the same laptop as you dont have a mic.

Please only reply if you have a solution or can aid in troubleshooting.

---

