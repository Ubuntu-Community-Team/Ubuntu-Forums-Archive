---
title: "No sound"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by lassel on 2005-07-07
Hi,

I am pretty happy with my ubuntu install except for the fact that I get no sound at all.
I have been reading through the forums and googled around quite a lot. I spent 4-5 hours on it total - and I just don't know how to get though this. I'll try to provide everything I know below. I hope that there is a kind soul out there who can point me in the right direction.

My machine dual-boots with windows and sound is fine there, so the most trivial "plugged-in" issue should be out of the way.

If I play a random mp3 file in totem I get no sound at all. I don't get an error message either. xmms and music player gives the same picture.

I am sure there is waaay too much useless info below. I just hope that someone can make heads and tails of it from what I write.

Running alsamixer I see that:
Card: SiS SI7012
Chip: C-Media Electronics CMI9761 
- all channels are turned up pretty loud.
- the gnome sound widget is also turned up to the top.

lsof:
```
root@luke:/home/lasse # lsof /dev/dsp
root@luke:/home/lasse #
root@luke:/home/lasse # lsof /dev/snd/*
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 6893 lasse   35u   CHR  116,0      6609 /dev/snd/controlC0
root@luke:/home/lasse #

```

my esd.conf file
```

root@luke:/home/lasse # cat /etc/esound/esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

and esd is running
```

lasse     6785     1  0 18:34 ?        00:00:04 /usr/bin/esd -terminate -nobeeps -as 2 -d default -spawnfd 18

```

I have asound.conf like suggested here:
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

lsmod | grep snd
```

snd_intel8x0           32416  1
snd_ac97_codec         74208  1 snd_intel8x0
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10080  1 snd
snd_page_alloc          9796  2 snd_intel8x0,snd_pcm

```

---

### Post by amohanty on 2005-07-07
Is this a PCI sound card or the mobo onboard ac-97 stuff??

Also install gamix (easier to handle than alsamixer) and check the settings for each of the inputs that gamix shows you.

---

### Post by varunus on 2005-07-07
Do you have libesd-alsa0 installed?  If not, I'd suggest installing it with that sound card.  I have the same card, and sound works for me.  What happens when you type:

```
aplay /usr/share/sounds/startup.wav
``` 

into a console?

---

### Post by lassel on 2005-07-07
Thank you for your suggestions.

I have a on-motherboard sound. I am not 100% sure what it is, windows reports it as C-media, but I can\t seem to find a serial number. I think the one alsa detected might be right. Inside the bios it refers to it as AC 97 sound.

I already installed esd-alsa0
- I can't be totally sure, but I think that BEFORE I installed that package I got a very short "bump" sound in my speakers when I rebooted. I don't get that anymore.

I installed gamixer and made sure everything is turned all the way up. I attached a screenshot of it.

I turned the PC Speaker all the way up. Now I get a beep sound from my speakers when i press backspace in a terminal window. Wierd huh?

aplay tells my that it plays a sound, but I hear no sound.

---

### Post by lassel on 2005-07-07
Just checked again:

Windows tells me that:

Audio Controller: SiS 7012 Series Audio Controller
Audio CODEC: CMI9739A

I don't know that windows means by a CODEC in this context. Kinda wierd though that the chipset alsa reports is a CMI97**61**A.
Could that mean anything?

Thank you for reading.

---

### Post by lassel on 2005-07-08
I thought I had been through all the "i get no sound" thread. But there were just heaps and heaps. Finally I tried searching for my chipset name and I got this:

[http://ubuntuforums.org/showthread.php?t=41732&highlight=CMI9761](http://ubuntuforums.org/showthread.php?t=41732&highlight=CMI9761)

> I got my sound to work...finally. I muted IEC958 Capture Monitor with Alsa Mixer GUI, and now I have sound, and I didn't even have to reboot.

That did the trick!
Belongs to a FAQ somewhere.

---

### Post by spudley on 2005-08-21
Just wondering if anyone has other ideas on the no sound issues presented here...  I've tried all the above, but get errors like this:

from aplay (cmd line)
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave

Volume control (gui)
No volume control elements and/or devices found.

Music Player won't even load now.

multimedia systems selector:
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'


When I try alsa mixer GUI (to try an idea from a previous message),  I get this error:
alsamixer: function snd_ctl_open failed for default: No such file or directory.



Any help would be really appreciated... I just replaced my Ubuntu system from an AMD 1.2GHz  (sound worked there) to to this newer P4 box and would really like it to work!

---

### Post by junghwanee on 2005-11-27
I did it, I had the same problem, but now i am with the sounds. I simply disabled the capture thing with Alsamixergui. Just type "alsamixergui" in the terminal.:D

also if you have the problem with low volumes. Try to increase the VIA DXS.
have fun

---

