---
title: "No sound - Ubuntu 10.10 netbook remix on Dell Mini"
date: 2011-01-06
forum: Hardware
---

### Post by mdouble on 2011-01-06
I up installed 10.10 netbook remix on my Dell Inspiron netbook about 2 months ago and it's had no problems until yesterday.  For reasons that are entirely unclear the sound just stopped functioning.  I have no system sound, no sound from audio or video files, no sound at all.  

I have read through the forums and tried some of the suggestions offered for other sound issues, but without success.  I have checked to be sure nothing is muted in the alsa mixer etc.  Unless I've missed something all seems to be as it should.  

I run Ubuntu 10.04 on my desktop computer and, oddly enough it also lost all sound.  This happened before Christmas 2010.  Once again I tried many solutions offered in forums and spent some time working on the problem on IRC #ubuntu.  So far no luck getting sound back on that system either.  

I am beginning to suspect a ghost in the machine, and the ghost likes thing very quiet.  Help with either of these problems will be most gratefully accepted.  Thanks in advance

---

### Post by lidex on 2011-01-07
Try this. Reset pulseaudio configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

