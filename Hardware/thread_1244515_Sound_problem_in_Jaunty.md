---
title: "Sound problem in Jaunty"
date: 2009-08-19
forum: Hardware
---

### Post by kirbyboy on 2009-08-19
Hi, i have a hp pavilion-dv6 1270ss, and installed recently Jaunty.
The sound didn't worked so i tried ALL i found in the web, included deleting pulseaudio and installing OSS 4, but like it didn't work, i reinstalled pulseaudio to try some solutions again.  The problem i have now is that pulseaudio doesn't recognize me the sound cards i had before(it saids null device).  How can i "reinstall" the sound cards in pulseaudio?

---

### Post by kirbyboy on 2009-08-19
I could "reinstall" the sound cards following the next guide:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
using the next command:
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
it restores the modules to the official ubuntu core.

Following the guide, it says i should submit a bug, should i do it?

---

### Post by Yellow Pasque on 2009-08-19
Did you try editing /etc/modprobe.d/alsa-base.conf and adding model=hp-dv5 to the snd-hda-intel options?

---

### Post by kirbyboy on 2009-09-17
Yes.  Now i'm trying to install the new alsa drivers, i think i install them correctly, but the computer says i use the .18 version(the new version is the .21).

---

### Post by Yellow Pasque on 2009-09-17
> **kirbyboy said:**
> Yes.  Now i'm trying to install the new alsa drivers, i think i install them correctly, but the computer says i use the .18 version(the new version is the .21).
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

