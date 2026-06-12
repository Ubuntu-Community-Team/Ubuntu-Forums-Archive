---
title: "No sound after removing bluetooth"
date: 2015-08-04
forum: Hardware
---

### Post by cogset on 2015-08-04
I've recently removed bluez along with bluez-alsa and bluez-cups and maybe bluez-gstreamer in Ubuntu 12.04 thinking that, since I don't use bluetooth at all, they weren't needed: as a result, now I have no sound at all in any application from Firefox to VLC, nothing at all.  

Even reinstalling the packages hasn't fixed this issue so far, I'm 99% sure this  has to be the source of the problem because I've noticed that all audio was missing shortly after this "cleanup": any suggestions on how do I proceed now to troubleshoot and fix this mishap?

---

### Post by Vladlenin5000 on 2015-08-04
Hi and welcome.

What you removed may have also removed other dependencies. As a general rule you shouldn't blindly remove system packages because bad things can happen... And to free how much kB? Really?

Try:

```
sudo apt-get install --reinstall alsa pulseaudio
```
Reboot.

---

### Post by cogset on 2015-08-05
I've solved it following the first part of this wiki [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) which means that I've deleted the entire .pulse directory and the .pulse-cookie file, after doing install --reinstall pulseaudio and  reinstalling the removed packages, namely bluez, bluez-alsa,  bluez-gstreamer and pulseaudio-module-bluetooth.

Then, thinking that probably the only package somehow needed was pulseaudio-module-bluetooth (and I'm not even sure about that, because I have bluetooth removed from my system) I've removed again bluez, bluez-alsa,  bluez-gstreamer and everything is OK.

Probably just killing pulseaudio, deleting the .pulse directory and the .pulse-cookie file and restarting the system would have cured the issue.
It's not about the disk space, I'd rather like to keep my system clean and get rid of stuff I don't need.

---

