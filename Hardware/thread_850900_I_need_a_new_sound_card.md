---
title: "I need a new sound card"
date: 2008-07-06
forum: Hardware
---

### Post by harvodan on 2008-07-06
Hello.

My favourite sound card, a sound blaster live (emu10k1) recently died on me after a long period of service. I'm running Ubuntu 8.04, and I'm looking for a cheap-ish replacement. Only thing I require is that the card be able to allow more than one program at a time, eg, totem + wine or skype, to use sound. At the moment, I'm looking at the 
Aopen Cobra AW-850D Deluxe, which uses the CMI8738 chip. Any idea if this will fulfill my requirements? 

I really don't care about things like 5.1 sound or eax support, I just want a sound card that will allow multiple apps using sound at one time.

---

### Post by DJ-Dark on 2008-07-06
Check [http://www.newegg.com](http://www.newegg.com) if you ever need anything for a computer check there and its awesome.

---

### Post by kostkon on 2008-07-06
> **harvodan said:**
> Hello.

My favourite sound card, a sound blaster live (emu10k1) recently died on me after a long period of service. I'm running Ubuntu 8.04, and I'm looking for a cheap-ish replacement. Only thing I require is that the card be able to allow more than one program at a time, eg, totem + wine or skype, to use sound. At the moment, I'm looking at the 
Aopen Cobra AW-850D Deluxe, which uses the CMI8738 chip. Any idea if this will fulfill my requirements? 

I really don't care about things like 5.1 sound or eax support, I just want a sound card that will allow multiple apps using sound at one time.
Don't worry, the problem with many sounds at the same time was solved with *PulseAudio*. Thus, even if the driver for this card does not support its hardware mixer or if its mixer is very limited (e.g. only 2 channels) then with *PulseAudio* will be able to have many sounds at the same time. 

You can follow [this how-to thread]("http://ubuntuforums.org/showthread.php?t=789578") to better set up *PulseAudio* in your system.

---

### Post by harvodan on 2008-07-06
Thanks, will look into that, PulseAudio was supposed to be a big deal in hardy, but only partly implemented if I remember correctly.

---

### Post by harvodan on 2008-07-06
Sorry Kostkon, that guide didn't work for my onboard audio, which is an ALC888 nvidia chip. Anyone have any luck with the CMI8738 under PulseAudio or otherwise?

---

### Post by harvodan on 2008-07-07
Got PulseAudio working acceptably with my ALC888. I have to preface all commands like wine with padsp, also for games like ut2004, but it mostly works. Also got skype working by selecting pulse as my output device and ringing device. Needed to set the mic as hardware though.

---

### Post by harvodan on 2008-07-07
Got the onboard sound working using pulse audio. Also got skype co-operating with it after awhile. I needed to set the output and ringing devices to pulse and leave the mic as it was.

---

