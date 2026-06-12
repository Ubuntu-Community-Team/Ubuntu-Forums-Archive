---
title: "Playing Multiple Audio in 8.04"
date: 2008-05-03
forum: Hardware
---

### Post by simonfiction on 2008-05-03
Hi,
I've done a fresh install of 8.04 on my system which ran Gutsy no problems. Not sure why but I know longer seem to be able to have 2 applications play audio at the same time. For example, I can't listen to rhythmbox and watch flash video with audio. Or even rhthymbox with the last.fm client. I get the message "The ALSA sound system is either busy or not present".

All of my devices are set to "Autodetect" in the Sound preferences.

Any suggestions? I'm at a loss and this is a show stopper for me :(

---

### Post by simonfiction on 2008-05-03
Hmm, Just realised everything works fine when I specify ALSA as my playback device. I'm assuming this is to do with PulseAudio issues I keep hearing about. Is it a case of applications attempting to use ALSA when it should be using PulseAudio? Is there any easy way to fix this without switching back to ALSA?

---

### Post by sgreddin on 2008-05-27
I had the same issue. I use Rhythmbox and flash wouldn't play at the same time as my player. Also, even after restarting both Firefox and Rhythmbox, Rhythmbox would simply not play. But i fixed it by going System> Prefernces> Sound, switched Sound Events, Music and Movies, and Audio Conferencing to PulseAudio Sound server. You may need to only swithc Music and Movies, but i ytypically go for overkill to make sure it works. Next, Alt+F2 and type "killall pulseaudio". At this point my computer slowed down, froze for a few moments, and then resumed. It still wouldn't play from Rhythmbox but i simply rextarted the computer, and now I have simultaneous audio and no freezing :D
Hope this helps!

---

