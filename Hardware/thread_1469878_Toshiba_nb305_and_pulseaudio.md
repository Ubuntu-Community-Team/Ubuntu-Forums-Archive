---
title: "Toshiba nb305 and pulseaudio"
date: 2010-05-02
forum: Hardware
---

### Post by jim_charlton on 2010-05-02
I have a Toshibanb30500F netbook running Ubuntu Lucid with ubuntu-netbook-remix installed.  I have a problem with pulseaudio.  If I open a gnome-terminal window and hit the backspace key (at the CLI prompt) I hear the normal ping.  If I continue to hit the backspace key a few times the sound becomes distorted.  Other applications will lose sound as well (Rhythmbox, sound recorder).  If I wait a few seconds the sound returns to normal.  But almost any sound application will lose sound after a few seconds or minutes of play (sound scratchy, distorted or gone completely).  Shutting off the sound application and restarting will again give a few minutes of undistorted sound.

I have tried all of the common remedies of modifying /etc/pulse/daemon.conf (default-fragments and default-fragment-size-msec) and putting "model=asus-mode4" at the end of the options snd-hda-intel line in /etc/modprobe/alsa-base.conf.  It changes it a bit but does not solve the problem.

If I remove pulseaudio completely with 
apt-get purge pulseaudio
and then reboot, the sound is normal in gnome-terminal and even rhythmbox works.  But of course, other things cease to work. (note that removing pulseaudio with apt-get says that it will also remove ubuntu-desktop... but the machine seems to reboot OK after the purge!).  Reinstalling pulseaudio recreated the audio problem so the problem seems to be with pulseaudio.

I can file a bug report but just wanted to see if anyone had the same problem first.  I can find nothing on the internet about this specific problem.  The sound works normally in Winows 7.

---

### Post by sobolosrios on 2010-05-02
It appears that I have that problem as well.  I don't know a fix yet, but wanted to confirm.

---

### Post by jim_charlton on 2010-05-02
Thanks for your confirmation.  

I have posted a bug report to launchpad.  Bug # 574137.

---

### Post by sobolosrios on 2010-05-02
As a rather non-scientific test I watched about 15 minutes of Youtube using Chromium and didn't seem to have any problem.  That is, the audio did not degrade the longer I watched.  Perhaps it would have had I watched long enough, but it was fine after about 15 minutes.

---

### Post by jim_charlton on 2010-05-03
I find that I can often get good audio for a long time but then it will degrade suddenly. If I play rhythmbox music, it is fine but if I hit the backspace key in the terminal window a few times then both sounds suddenly degrade and stay that way until I shut off rhythmbox for a few seconds.  If I record something using sound recorder, it may play back perfectly the first time... but then fail the next time.  The same with twinkle (sip phone program).  The audio will suddenly go bad.

---

### Post by sobolosrios on 2010-05-03
I'll keep that in mind.  15 minutes of Youtube is about all that I can stand, so I'll try listening to music.

---

### Post by paulohahn on 2010-06-07
Same problem,

I now playing on Ubuntu 10.04 64bits.

The atached file is information about my system.

I will keep to trying to solve problem...

UP!!

---

### Post by lidex on 2010-06-09
> **jim_charlton said:**
> I find that I can often get good audio for a long time but then it will degrade suddenly. If I play rhythmbox music, it is fine but if I hit the backspace key in the terminal window a few times then both sounds suddenly degrade and stay that way until I shut off rhythmbox for a few seconds.  If I record something using sound recorder, it may play back perfectly the first time... but then fail the next time.  The same with twinkle (sip phone program).  The audio will suddenly go bad.

Is this with or without pulse?

---

