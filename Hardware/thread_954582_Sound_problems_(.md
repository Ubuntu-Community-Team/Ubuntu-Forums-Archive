---
title: "Sound problems :("
date: 2008-10-21
forum: Hardware
---

### Post by faiz1985 on 2008-10-21
Hi everyone, I jus installed Ubuntu 8.04 on my laptop, everything looked grea, and jus wen I was on the verge of kicking out my windows OS, I realised tht audio is not working in Ubuntu :(
Since im totally new to Linux OS's, can anybody Plzzzzzzzzzzzz help me in getting the audio to work.
BTW, I use a HCL B3008 laptop which has a "Realtek ALC 660 24-bit, High Definition Audio controller".

---

### Post by tuxxy on 2008-10-21
Can you hear the test sound file play located at **system > prefs > sound** also try it with ALSA as output device

---

### Post by faiz1985 on 2008-10-21
Nope, unable to hear the test sound at tht location..Tried wit ALSA as output device too, but no luck..

---

### Post by buixuanduong1983 on 2008-10-21
Try this command in Terminal (Applications/Accessories/Terminal):
aplay -l
to see what you get.
(This command gives list of playback device)

---

### Post by faiz1985 on 2008-10-21
This is the output i get-

faisel@faisel-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
faisel@faisel-laptop:~$

---

### Post by buixuanduong1983 on 2008-10-21
Try righ-click the volume icon (next to the clock), Open volume control, and see if some slider is muted. Also check in System/Administration/Hardware device to see if you have some proprietary drive not yet installed. One more thing I can think of is restart your system. Or use the Live CD to see if you can get the audio.

---

### Post by faiz1985 on 2008-10-21
Hi,
I checked for volume properties, nothing is muted as such...Tried restarting the system too, dint work either..
I checked in system/administration/Hardware drivers, thr r jus 2 device drivers-
1. Atheros Hardware Acess layer(HAL)
2. Support for Atheros 802.11 wireless LAN cards
both hav a green light next to them..
As far as i know(I could be wrong), both the abov things hav nothing to do with audio right? How do I go abt getting some audio stuff installed here?(if tht has t be done)
Also, Can u pls enlighten me how to use the live CD to get the audio working.. Im totally new to Ubuntu so i really dunno the a-b-c's.. Thanks again :)

---

### Post by markbuntu on 2008-10-21
You probably need to set some option for that ALC861. There are some guides to doing that here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

Be sure to look through the threads, there may be a soecific solution for you hiding in there somehwere if the OP does not fix you up. You can also try this:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

