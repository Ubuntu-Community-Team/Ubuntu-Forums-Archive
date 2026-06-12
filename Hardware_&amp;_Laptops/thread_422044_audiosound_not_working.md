---
title: "audio/sound not working"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by cchidamb on 2007-04-24
I just installed ubuntu 7.04 on my sony vaio laptop.  I couldn't get get my sound working. Looks like the driver is loaded successfully, and the sound card is correctly recognized. 

aplay -l returns

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice 

Part of 'lsmod' returns

snd_intel8x0           34204  2 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

In /etc/modules I've added the following entry at the bottom

intel-8x0 , and rebooted. Still no luck, I would appreciate if you anyone could help to get my sound workin on the latest ubuntu I've installed.

P.S: Sound card is working fine, bcz if I boot it on windows, I can hear the sound.

I went  to 'alsamixer' and made sure volume is up, and unmuted.

---

### Post by N'Jal on 2007-04-24
Same problem same hardware except we tried loading these modules instead, with no luck


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
snd-intel8x0
snd-pcm-oss
snd-mixer-oss
snd-seq-oss


Thanks

---

### Post by govi on 2007-04-24
type  'alsamixer' in the terminal, PCM is the main volume control, Front is your headphone volume control, surround is the speaker. press M to turn on/off the volume function. Press the UP/DOWN buttons to change the volume.

good luck!

---

### Post by cchidamb on 2007-04-25
Thank You for your reply. I tried alsamixer already, tried again after your reply. Still the same problem, couldn't hear any sound.

---

### Post by N'Jal on 2007-04-25
Can confirm, that does not solve the problem.

---

### Post by cchidamb on 2007-04-25
I tried adding the entries 

snd-intel8x0
snd-pcm-oss
snd-mixer-oss
snd-seq-oss

as suggested by you in /etc/modules, and rebooted the system. Still no sound.

---

### Post by mordur on 2007-04-27
I have exactly the same problem, only on a Dell inspiron 8600 with the same sound card. I have noticed that the sound card seems to work up until one logs in, at least the "drum" sound announcing the login prompt for Ubuntu plays loud and clear.
 
Has this issue not been resolved?

Mordur

---

### Post by mordur on 2007-04-27
The problem in my case was that the regular user was not a member of the audio group, so the user didn't have permission to access the necessary devices. I straced the amixer command and saw the Permission denied for using /dev/snd/controlC0 

Solution:

usermod -G audio username

And restart X
Solved this problem for me.

Hope this helps.

Mordur

---

