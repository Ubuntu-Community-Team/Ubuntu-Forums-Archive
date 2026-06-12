---
title: "onboard sound problems"
date: 2005-11-10
forum: General Help
---

### Post by gillano on 2005-11-10
i'm still pretty new to ubuntu, so far it is working great but....

i am runnig an Asus P5GL with Intel onboard sound, there is no sound when i play cds or mp3s, or anything else, but there is sound when i log in and start up, the  mixer is not muted the cables are all hooked up, the speakers are working fine, i installed automatix, (which solved some other probs), i have dowloaded the alsa diver, but not installed it yet, i guess that is what i need, i don't really know what i am doing yet, does anyone have any ideads?? i don't have a linux book yet what should i read

---

### Post by manicka on 2005-11-10
If you have some systems sounds then that is a good sign. Have a look at the volume control manager and see if anything is muted. 

What programs are you using to play mp3's etc. You may just need to change the sound engine that these programs use.

---

### Post by gillano on 2005-11-10
i am using totem to play mp3s, just checked and now there is sounds, but it is kinda distorted and there is a high pitch whineey noise on top of it all(kinda painful to listen to), but still no cd audio, i must have someting hooked up wrong with that



what is the best free mp3 played to get????



thanx in advace for all the help

---

### Post by gillano on 2005-11-10
so i was just playing a cd and when i opened alsa mixer to try and get the dstotion to go away the audio cut out the visulization is still running though

i think i'll reboot and try again

---

### Post by manicka on 2005-11-10
[QUOTE=gillano]i am using totem to play mp3s, just checked and now there is sounds, but it is kinda distorted and there is a high pitch whineey noise on top of it all(kinda painful to listen to), but still no cd audio, i must have someting hooked up wrong with that

what is the best free mp3 played to get????
[/QUOTE]

Open the volume Control panel by right clicking on the volume icon on the panel and choosing 'Open Volume Control'

Check that your PCM level isn't to high as this can dause distortion.

I prefer amaroK to play music, while others prefer rhythmbox and xmms, to name a few. Open Synaptic Package Manager and search for audio software. Install some and try a few to see which one you like.

---

### Post by gillano on 2005-11-11
actually cds are playing now  i really and not sure what i changed (it was a late night last night)   but there is the same distorted noise with cds 



i'm almost there!!!!!

---

### Post by gillano on 2005-11-11
ok every time i reboot i can play cd's and mp3's but as soon as  i open the volume control audio shuts OFF   i can't get the high pitch sound to go away but the distortion is reduced now (pcm control, guessing blindly and rebooting)

---

### Post by manicka on 2005-11-11
Set the PCM at about 70%

---

### Post by gillano on 2005-11-15
set pcm at 70% and it only made things quieter ather is no more ditorion but there is a high pitch sound llike it is mixed with the sound it comes from the left more than the right

and ther is still the problem with the sound cutting out as soon as i open the mixer is there another mixer that i can use instead????

---

### Post by GIBson3 on 2005-12-06
I've been Having this issue with the "Intel 82801BD-ICH2 (Alsa mixer)" media adaptor with reqular audio play back (IE: Music (MP3/CDA/ETC))  in games it's fine >.<  as soon as I set my "Multimedia Systems setup" back to ESD Audio is clean and clear, I have a feeling this is more an ALSA/Driver issue than it is an Ubuntu problem.

Hope this helps.

---

