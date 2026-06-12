---
title: "Plantronics 995"
date: 2010-08-26
forum: Hardware
---

### Post by dillzz on 2010-08-26
Has anybody had success with this wireless headset?  

[http://www.plantronics.com/north_america/en_US/products/computer/multi-use-computer-headsets/audio-995](http://www.plantronics.com/north_america/en_US/products/computer/multi-use-computer-headsets/audio-995)

---

### Post by dillzz on 2010-08-27
So the headset has arrived.  I am using kubuntu 10.04 x86_64.  I plugged the headset in and heard nothing, I then went to kde system settings --> multimedia and set the priority to this device as opposed to onboard audio.  I then set kmix to control master channel to this device and PCM.  

Everything worked as planned.  However, Whenever I opened firefox/chrome all audio was passed out the speakers instead of headset.  I then edited/created /etc/asound.conf to include the following:

pcm.!default {
    type hw
    card Audio
}
ctl.!default {
    type hw
    card Audio
}

All worked after a browser restart.  I then wanted to test recording of Mic.  So i issued:

arecord -r 44100 -f S16_LE -D hw:1,0 foo.wav;
mplayer -ao alsa:device=hw=1.0 foo.wav


The recording was crystal clear.  Questions are?  

Main reason I bought this was for gmail chat features, I installed the plugin and cannot record anything from MIC (tried all inputs on gmail side), nor can I hear any output.  

Seeing as this is a headset - this seems exhausting, are/is there any other solution/idea?

---

### Post by tgalati4 on 2010-08-27
arecord uses ALSA, I believe gmail chat uses pulseaudio.  Did you install all of the pulseaudio controls (such as pavucontrol)?  These settings are separate from ALSA and the application's level control.

---

### Post by dillzz on 2010-08-28
tgalati4,

Thank you for the insight.  I installed pavucontrol and pulseaudio and was able to get the more granular control.  I was able to get both firefox/chrome to play through headphones.  After initial setup I am now able to plug in the phones and audio goes to them, disconnect and comes through sound card.  

I did a reboot to ensure everything was initialized, kmix now looks a lot different and systemsettings shows just backend phonon server.  Not a big fan of pulse as it strips bass/treble and other things, luckily for my onboard, alsamixer still works.  At least we are working now....

As far as gmail calling landlines, I just had to set the defaults to the plantronics device and we are golden.  


thank you  - hope this helps the next poor soul...


-Dillzz

---

### Post by MorleyPotter on 2010-12-15
Has anyone had any success with Skype with this set up?

Thanks in advance

MorleyPotter

---

### Post by xanadux on 2011-03-23
Yes, this setup works fine with Skype.

---

### Post by zaazz on 2011-04-25
Thanks for this post. I got my headphones working with Kubuntu 10 using this information.

---

