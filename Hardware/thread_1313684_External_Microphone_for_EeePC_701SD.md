---
title: "External Microphone for EeePC 701SD"
date: 2009-11-03
forum: Hardware
---

### Post by BradP on 2009-11-03
Prior to Ubuntu 9.10, I could never get the external microphone to be recognized for the EeePC 701SD to be recognized.  Even when I plugged a microphone into the 1/8 in. jack, it still used the built-in microphone. I tried all the solutions I could find.

I recently did a fresh install of Ubuntu 9.10 Netbook Remix on my EeePC 701SD.  The external microphone jack still did not work.  However, I found that the post for the EeePC 900a at [http://ubuntuforums.org/showthread.php?t=1289061]("http://ubuntuforums.org/showthread.php?t=1289061") also works for the 701SD.

For me, I just changed the delivered line in /etc/modprobe.d/alsa-base.conf of:
[COLOR="Red"]options snd-hda-intel power_save=10 power_save_controller=N[/COLOR]
to
[COLOR="Lime"]options snd-hda-intel index=0 model=quanta power_save=10 power_save_controller=N[/COLOR]

One restart later, and all was good.

Just wanted to share this if others were having the same frustration I was with the 701SD.

---

### Post by keith56 on 2009-11-06
I am brand new to the forum.  i am using Eeebuntu 3.01 NBR on an Asus EeePC 701SD 8G and your advice got my external microphone working after several days of research.  My alsa-base.conf did not have any snd-hda option line so I just added "options snd-hda-intel index=0 model=quanta" and alsamixer now has all the options I need.  Thank you,

---

