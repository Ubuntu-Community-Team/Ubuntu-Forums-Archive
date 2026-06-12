---
title: "sound problem with &quot;CREATIVE SOUND BLASTER 5.1&quot;"
date: 2009-03-17
forum: Hardware
---

### Post by fahadrather on 2009-03-17
hi there..i installed ubuntu 8.10 but i am having sound issues...in fact there is no sound...i am using a creative sound blaster 5.1(no audigy,live,or any thing else)just sound blaster 5.1...i reinstalled ubuntu today but i encounter the same problem...i read somewhere that u need to enter the following codes to make your sound work 

sudo killall pulseaudio 
sudo alsa force-reload

and then reset everything to ALSA in sound settings. when i did this the sound did work,the sound in rear speakers was too low...but after restart the sound vanished and i had to retype the codes..:(.........i have other issues as well but lets solve one at a time.

---

### Post by caver1 on 2009-03-17
I am using Audigy 1 SB in Intrepid64 and pulse with no problems at all.
First thing to check. Open your Volume control by right clicking the speaker on your top panel. Click Open volume control.
click on the switches tab. Make sure that the Audigy Analog/Digital Output Jack is unchecked (empty) You should now have sound.
caver1

---

