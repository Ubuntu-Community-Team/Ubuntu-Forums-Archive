---
title: "Totem/gstreamer high cpu usage"
date: 2008-11-05
forum: General Help
---

### Post by Angelbeast on 2008-11-05
Hello again. I have been noticing some high cpu usage the past few days while watching video in totem with gstreamer. Up to 80%. Has anyone else been having this problem? If so how do i fix it? I'm using Ubuntu 8.10 on an HP DV8000. Thanks in advance for any help.

---

### Post by Angelbeast on 2008-11-05
*bump*

---

### Post by Angelbeast on 2008-11-05
*bump bump*

Anyone?

---

### Post by Gausian on 2008-11-05
What kind of file are you playing?  I just checked a 720p .mkv video in both mplayer and totem and they both used about 50% to play the video.

---

### Post by Angelbeast on 2008-11-05
> **Gausian said:**
> What kind of file are you playing?  I just checked a 720p .mkv video in both mplayer and totem and they both used about 50% to play the video.

all i have tried so far are avi and audio files and the audio files seem to play fine

---

### Post by Angelbeast on 2008-11-06
*BUMP*

Come on no one has any ideas? *LOL*...

I did try a fresh install but it's still going up to between 70 and 75 percent ... 

Does ANYONE have ANY ideas? I could really use the help :-)

---

### Post by Angelbeast on 2008-11-06
Oh and i even tried disabling the plugins in totem with no luck

---

### Post by Angelbeast on 2008-11-06
*bUmp*
*bUmp*

---

### Post by ethoms on 2008-11-25
I've got the same problem on my laptop running Ubuntu 8.10 using Totem, it's a bit jumpy too. On same machine, the same file plays perfectly with low cpu in SMPlayer and VLC player. Also, it plays fine on my desktop. Tried switching between alsa and oss mixers, no difference.

My laptop (cpu 100% playing) has ATI radeon xpress 200m with latest fglrx whilst   my desktop (plays fine) is an nVidia Geforce with proprietary drivers.

I'm just going to check what plugins are installed on desktop and copy that package list to laptop.

Anybody know how to start debugging these kind of issues??

---

### Post by ethoms on 2008-11-26
OK, done some more investigating. Ignore my comments about mplayer and vlc player, although I could have sworn at the time they used much less cpu, now it appears they are also using very high cpu (but play smoother).

It seems it's the proprietary ati driver (fglrx). It's clear cut, uninstall and totem uses 20% cpu, install and it uses 80-100%. I'm using synaptic to install package: xorg-driver-fglrx, version: 2:8.543-0ubuntu4.

Anybody know more about this, I'm guess it's quite a common issue given the amount of ATI graphics card owners.

---

