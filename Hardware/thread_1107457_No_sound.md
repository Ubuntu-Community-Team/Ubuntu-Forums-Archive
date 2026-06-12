---
title: "No sound"
date: 2009-03-26
forum: Hardware
---

### Post by wleejolly on 2009-03-26
I hate to post this because I know just how many "no sound" posts there are, as I've been searching for them for hours and trying everything I could find with no luck.

I'm running 8.10 and over a month ago, I would have sound for about 3 days, sometimes over a week and then it would just stop working, but a reboot would fix it.  I could never find what caused the problem, but for the past month or so it was good so I just forgot about it.  But today I have no sound and it will not come back no matter how often I reboot, or what changes I make.

I've tried following that very long detailed post about configuring pulseaudio

I've tried sudo killallpulseaudio and audo alsa force-reload

I've tried removing pulseaudio and installing esound, 

I've tried recompiling my alsa drivers, 

I've checked my PCM and line volumes to make sure they were up in alsamixer, 

I've tried changing System>Preferences>Sound settings, from autodetect, to alsa, to pulseaudio, and esd. 

I've followed this tutorial [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and did the getting alsa drivers from a fresh kernel 

I can boot from a LiveCD and I do get audio then, so I know it's not a hardware issue.  

Right now, I have removed pulseaudio and installed esound, but it's still not working.  Very frustrating.

I'll do whatever it takes to get this working, any more ideas?

Here's some outputs:
lspci:
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If I do sudo modprobe snd-intel8x0 it just returns with no messages as if it loaded, but still no sound.

---

### Post by wleejolly on 2009-03-26
and just upgraded ALSA to 1.0.19 [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) , still no sound

---

### Post by wleejolly on 2009-03-26
I just went back to pulseaudio and followed these directions to the letter and still no sound: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I end up with (from his appendix):
The application **does not** play audio and **does** list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.

not sure about the bug in pulseaudio, but it didnt work with esound either

ALSA kernel module and libraries were just upgraded, so shouldnt be this right?

PCM/Master volume muted, I double checked that using alsamixer -Dhw and they are all fine

---

### Post by wleejolly on 2009-03-27
I just upgraded to 9.04 and the install was smooth, but still...no...sound!  ARRGGG!  I have no idea what to do next.  I know this CAN work because it had worked in the past for a year (albeit with some issues here and there)

---

### Post by wleejolly on 2009-03-27
Is a complete reinstall really the only solution?  I would have thought the upgrade would have fixed it.

---

### Post by wleejolly on 2009-03-27
Not sure how I got here, but it's actually encouraging to finally see something that looks wrong, because up until now everything looked fine (to me) it just didn't work.  Now when do aplay -l, I get an output specifying a modem:

**** List of PLAYBACK Hardware Devices ****
card 0: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and when I do alsamixer -Dhw, I only get options for the modem (caller I, and off hook).  Any idea how to fix this?

---

