---
title: "sound trouble on toshiba with intel sound chip"
date: 2009-03-28
forum: Hardware
---

### Post by attendedsky on 2009-03-28
I know there have been a lot of posts on this topic before and a lot of people seem to have fixed there problem following those posts. But unfortunately, I have not been able to get sound on my laptop even after browsing through hundreds of posts and trying various combinations of edits to the "alsa-base" file.

I have a toshiba R25-S3503 tablet-laptop with a dual boot system of win XP and ubuntu 8.10. Below are some details of my system:

```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
lspci
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


I updated to the latest version of alsa and have tried adding various combinations of "options snd-hda-intel model=xxxx" (where xxxx represents different model names) to the "alsa-base" file in the "modprobe.d" directory. (including "probe_mask") but to no avail.
I also tried the "backports" method that I found on a couple of posts and that didnot help either.
Also all the posts that I have gone through, no one seemed to have the exact combination of hardware that I have, so maybe I have a weird combination that just doesn't want to work on ubuntu. (Sound works fine on XP).
My tablet pen is also not working, but that is not so important for me right now (I will do more search on that later, but if sumone wants to help with that too - even better!)
I am fairly new to linux, so any help would be greatly appreciated.

---

### Post by MasterSander on 2009-03-28
Have you also tried the option auto? Because that worked for me (I also have a crappy intel card :D) And turn everything open in the volume manager afterwards, because my pc speakers are labeled as surround and I have headphones and pc speakers at the same time.

---

### Post by attendedsky on 2009-03-28
Solved!
As I said before, I have a dual boot system with win XP on it too. Turns out that the sound was muted in windows and thus it wasn't letting sound work on ubuntu either. I booted into windows, unmuted the sound, and rebooted back into ubuntu and was greeted with the drumroll! :-)
so windows can give trouble even when it's not running - who would have guessed! 

And thanks for the reply MasterSander, I did try the auto option before but that didn't work either at that time.

Now onto the tablet pen!

---

