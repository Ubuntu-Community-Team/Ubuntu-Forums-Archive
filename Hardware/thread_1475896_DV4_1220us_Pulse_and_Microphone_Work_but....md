---
title: "DV4 1220us Pulse and Microphone Work but..."
date: 2010-05-07
forum: Hardware
---

### Post by zampes on 2010-05-07
Hi all!
I have an HP dv4 1220us. My audio config is the normal one for this machine and I have recently installed lucid 10.04. Pulse and Alsa are in the 'clean' install state.
I have modified the /etc/modprobe.d/alsa-base.conf file by erasing all its original install contents, and replaced them with:

```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
```
(see attached file with Alsamixer config)

Now the microphone works, but only the first ten minutes. I can test call skype and hear myself. Then after around 10 minutes, the microphone dies. I know this because I have the volume meter from Pulse open and on top of all other windows.
Does anybody know why this happens? Has been happening since 9.04 -then on to 9.10 and still now on Lucid.
Help? Anyone?

---

### Post by dino99 on 2010-05-07
install paprefs and gnome-alsamixer (tweak the settings)

into /etc/modprobe.d/alsa-base.conf
add the good codec
options snd-hda-intel model= 
( info at cat /proc/asound/card0/codec#* | grep Codec )

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by zampes on 2010-05-07
Hi there, thanks for replying with a solution. When typing 
```
sudo cat /proc/asound/card0/codec#* | grep Codec
```
the result is:
Codec: IDT 92HD71B7X
Codec: LSI ID 1040

which is these should I add to alsa-base.conf?
Thank you :)

---

### Post by zampes on 2010-05-07
Sorry, already found how to do it... Thx :)
Now it's testing time.

---

### Post by zampes on 2010-05-07
So I've taken all the necessary steps, done everything right and the microphone DOES work, skype test call and all but...
It still dies after 8 minutes (typed "uptime" as soon as it died).
Is Pulse shutting down microphone because it thinks that it's not being used? It driving me nutters!
Help? Ideas?

So the thing is that the Mic works until I launch anything else, Rhythmbox, Chromium, Firefox, Amarok, sometimes even Gedit or Kate... This is so weird... wild guesses anyone?

---

### Post by zampes on 2010-12-08
After months of looking for an answer, this is what this HP model needs to get the sound card/ microphone working:

> cd /etc/modprobe.d
sudo gedit alsa-base.conf


and inside the file:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
options snd-hda-intel position_fix=1 enable=yes

Restart and have fun with a microphone that never dies :)

---

### Post by balak on 2011-01-07
Thank you zampes. I was able to use this for my hp dv4z laptop as well (which has the same audio chip).

---

### Post by gilaadb on 2011-12-19
Amazing! I was looking for a solution to that problem for many months now :)
Thank you very much for sharing your findings and not keeping them for yourself!

---

