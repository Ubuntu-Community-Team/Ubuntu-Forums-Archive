---
title: "Sound on front line-out only after plug-out and plug-in again"
date: 2013-06-05
forum: Hardware
---

### Post by mercury1981 on 2013-06-05
**Hi all!**

I have the very annoying situation that since several weeks I have to plug-out and plug-in my headphone to my computer in order to hear something on my headphones.

I am using Ubuntu for more than 4 years on this computer and until now it worked perfectly, but since approx 3 weeks I have the following situation:
1. I boot my PC
2. I log-on to XFCE
3. I try to play a MP3 file in VLC
4. => NO SOUND on my headphone
5. I plug-out the headphone
6. I plug-in again
7. in the top-right corner I can see the volume-level-display overlay
8. now I can hear the MP3 file

After a reboot the situation is the same - each time! :-(

I am not sure if it is correlated to my switch from GONME to XFCE but that happened also several weeks ago (but in the first days with XFCE I did not have this problem).

Can anybody please give me hints how to solve this as it is cumbersome to get under my desk each time to plug-out and plug-in my headset.

Thanks a lot!

---

### Post by ohnonot on 2013-06-07
the problem sounds vaguely familiar.
is your system using pulseaudio?

---

### Post by mercury1981 on 2013-06-07
Can you please tell me how to find out if my system is using pulseaudio? :oops:

---

### Post by ohnonot on 2013-06-07
open taskmanager, or type 'top' in a terminal, and see if you find a process that contains 'pulse' in its name.
i've been using xubuntu a while back but i really can't remember if it uses pulseaudio.

edit: nevermind, i found it. xubuntu uses pulseaudio.
go to sound settings (e.g. through your volume systray icon), tab output devices, and play with the green button (tooltip: 'set as fallback') and maybe other settings, too. for me it would be logical to set headphone as fallback, be sure it is un-muted, and set the volume to a reasonable level.

---

### Post by mercury1981 on 2013-06-07
Thank you!

You pointed me in the right direction - there were some problems I managed to solve now :-)

1. xfce4-mixer was not installed on my system - so I could not change it using taskbar / system-settings and so on (I have no idea why it was not installed)
2. I installed it and found out that "Playback: Build-in Audio Analog Stereo PulseAudio Mixer was muted (I have no idea why).

So I unmuted it and now it works! Thanks a lot!

---

### Post by ohnonot on 2013-06-07
glad to be of help.
please mark this solved: edit first post -> go advanced -> chose [solved] prefix. thanx, others will profit.

---

