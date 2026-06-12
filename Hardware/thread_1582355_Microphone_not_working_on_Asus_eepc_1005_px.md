---
title: "Microphone not working on Asus eepc 1005 px"
date: 2010-09-26
forum: Hardware
---

### Post by psychok7 on 2010-09-26
hi guys, i have installed Ubuntu netbook edition 10.10 BETA on my asus eepc 1005px. Everything seems to work fine apart from the microphone. 

I have tried installing linux-backports-modules-alsa-maveric-generic to try correct it and no luck. 

I also tried installing padevchooser and i think i see some kind of input on the mic but when i open up skype nothing happens.

please help i really need the microphone working

---

### Post by 0N3 on 2010-09-26
Can you post a screenshot of your Sound preferences menu with the input tab opened?

---

### Post by psychok7 on 2010-09-26
> **0N3 said:**
> Can you post a screenshot of your Sound preferences menu with the input tab opened?

here is an attachment.. i realized the volume meter is only STATIC since i am hearing it on another pc when i call..just plain noise

---

### Post by 0N3 on 2010-09-26
you have it set as analog-stereo-output is there an option to set it to analog-stereo-duplex? analog-stereo-output im pretty sure if were using ur webcam and played music the device is configured to listen to your speakers and not you im no export but my mic doesnt work on analog-stereo-output it does when i play music it works super but if i talk it doesnt pick up what i say when i set it to analog-stereo-duplex it hears me talk no problems hope this helps

---

### Post by psychok7 on 2010-09-26
> **0N3 said:**
> you have it set as analog-stereo-output is there an option to set it to analog-stereo-duplex? analog-stereo-output im pretty sure if were using ur webcam and played music the device is configured to listen to your speakers and not you im no export but my mic doesnt work on analog-stereo-output it does when i play music it works super but if i talk it doesnt pick up what i say when i set it to analog-stereo-duplex it hears me talk no problems hope this helps

with padevchoose there no analog-stereo-duplex option. but with pavucontrol there is but still doesnt work. 

should i remove the alsa backports? any other ideias?

---

### Post by 0N3 on 2010-09-26
When i switch from analog-stereo-output to analog-stereo-duplex i have to reboot in order for it to work too dunno why :(
It's up to you what you want to remove might be worth a go removing it and would definitely reboot after each procedure it worked for me after days of pulling my hair out is there an option to choose device for sound input also?
Also maybe try 

sudo apt-get install gnome-alsa-mixer

Are you 32 or 64 bit?

---

### Post by 0N3 on 2010-09-26
sorry sudo apt-get install gnome-alsamixer

---

### Post by 0N3 on 2010-09-26
Just came across this Thread could be worth a look into it

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by casrenooij on 2010-10-11
Had the same problem. In Pulseaudio Volume control in the input devices tab unlock the channels for left and right microphone and set the volumes to unequal setting. Seems an odd way to solve a problem but it worked here.

hope this helps...

GF is happy ;)

---

