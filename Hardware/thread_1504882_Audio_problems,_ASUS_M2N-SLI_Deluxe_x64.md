---
title: "Audio problems, ASUS M2N-SLI Deluxe x64"
date: 2010-06-08
forum: Hardware
---

### Post by seabishop on 2010-06-08
Stuck for long time with this, now that's it, need to solve and need your help.

Hardware:
ASUS MSN-SLI Deluxe x64, integrated sound card
Simple audio output device, connected to pc

Software:
Ubuntu 10.4 LTS

Symptoms:
No sound.

Have been trying many different things (PulseAudio, Alsa, various conf file changes), no result. Maybe someone has had same problem? How can I diagnose problem better? Should I reinstall all sound related stuff (one more time, maybe this time miracle happens)?...

---

### Post by lidex on 2010-06-09
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by seabishop on 2010-06-10
Thanks for answering :). Here is link to information I uploaded with your script.

[http://www.alsa-project.org/db/?f=34c3698ec071329f84b072ee24b04d29bba6e889](http://www.alsa-project.org/db/?f=34c3698ec071329f84b072ee24b04d29bba6e889)

---

### Post by lidex on 2010-06-11
Have you installed alsa-backports? If so, uninstall and reboot. Next follow the alsa-upgrade link in my sig to get v 1.0.23

---

### Post by seabishop on 2010-06-12
Tried alsa upgrade script with no result (when doing "aplay" it responded something about "Cannot connect to Pulseaudio"), so I reinstalled Ubuntu (patience ended). That helped, now have sound. :) Thanks for assisting.

---

