---
title: "Toshiba Sattelite sound problem"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by bfskinner on 2007-07-04
I read through the sound guide posted somewehre in these forums, and I managed to get my sound card installed, and everything unmuted. 

aplay -l gave me this 

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Which seems to be fine.... nothing is muted, volumes are up.. checked the hardware volume control... yet still no sound. Any advice?

---

### Post by bfskinner on 2007-07-05
Bump, I miss my music

---

### Post by bfskinner on 2007-07-06
Bump

---

### Post by EndPerform on 2007-07-06
What model is your laptop?  Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

I have a P105-6227 and it brought me sound.

---

### Post by bfskinner on 2007-07-08
A105-s2236... it's a POS but it was free. Everything seems fine and installed but I have no sound, not even ambient noise coming out of the speakers(which these tend to produce a lot of).

---

### Post by EndPerform on 2007-07-09
> **bfskinner said:**
> A105-s2236... it's a POS but it was free. Everything seems fine and installed but I have no sound, not even ambient noise coming out of the speakers(which these tend to produce a lot of).

Yeah, mine was completely silent too until I followed the instructions in the thread I had posted.  It may work for you, but I know there are also others that had some issues with toshiba...  search the forum and I think you might come across what you need.

---

### Post by stchman on 2007-07-09
> **bfskinner said:**
> I read through the sound guide posted somewehre in these forums, and I managed to get my sound card installed, and everything unmuted. 

aplay -l gave me this 

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Which seems to be fine.... nothing is muted, volumes are up.. checked the hardware volume control... yet still no sound. Any advice?

I have an A135-S2246 and this worked for me:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Look at the first section.

---

