---
title: "Intel HD Audio not working in Hardy."
date: 2008-07-12
forum: Hardware
---

### Post by coolen on 2008-07-12
I've had this laptop for a couple of weeks now, and sound doesn't work at all. It seems to be detected, alsamixer sees it, but no sound.

I've searched high and low, tried every fix I could, and although many people have reported success with their cards using ALSA, none of them have worked for me.

One thing I've noticed which is odd is the codec (I'm not sure if that's the right term). Some commands say it's ALC889, others (including the Sound preferences) say ALC883.

Is it possible that my card isn't being detected properly? Can I somehow force one of these?

---

### Post by Dark_Stang on 2008-07-12
What does "lspci" show it is?

---

### Post by coolen on 2008-07-12
benji@sterrance:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I've searched for solutions related to that output and applied every one...no luck...

---

### Post by coolen on 2008-07-14
I set probe_make=8 in /etc/modprobe.d/alsa-base, and now get an error with alsamixer:


alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by coolen on 2008-07-14
I set probe_mask=1 in /etc/modprobe.d/alsa-base. I still get the error when opening alsamixer, but the Sound Preferences shows my card correctly and can attempt to play test sounds. Everything other than alsa and actual sound output works now, including Volume Control (which I think just handles all the same channels alsamixer does).

---

### Post by Daelyn on 2008-07-15
[http://ubuntuforums.org/showthread.php?t=643193](http://ubuntuforums.org/showthread.php?t=643193)

---

### Post by marrypret88 on 2008-07-15
I know this site for many foreigners, i from Japan 
   if the site  useful for me? [www.goonlinetv.com](www.goonlinetv.com) 
                               [www.onlinetvtoolbar.com](www.onlinetvtoolbar.com)

---

### Post by marrypret88 on 2008-07-15
Enjoy 1570 Channels worldwide [www.goonlinetv.com](www.goonlinetv.com)  
Download TV plugin for more stations [www.onlinetvtoolbar.com](www.onlinetvtoolbar.com)  ( It’s free )

---

