---
title: "Sound Card Digital Out - HP laptop"
date: 2008-05-27
forum: Hardware
---

### Post by mszargar on 2008-05-27
I have an old Compaq nx7010 that I use, with a HP PR1006 port replicator, as a multimedia center at home. 

I am using the IEC958 output on my SoundMax integrated audio card made by Analog Devices to direct PCM signals to my amplifier through SPDIF. I have turned on and chosen IEC958 on ALSA as the default, and have included the following lines to my asound.conf file:

pcm_slave.sndsl {
    pcm iec958
    rate 48000
}

pcm.iec958_48 {
    type rate
    slave sndsl
}

to set the default sample rate to 48khz, because apparently this is the only sampling rate my soundcard supports for SPDIF out. So, ALSA is doing an automatic upsampling to 48khz each time I play a music. The problem is that the quality of the sound is really mediocre. I don't have this problem on windows as I am using my soundcard's original drivers and proprietary mixer, but apparently resampling is not such a simple job, and ALSA is not good at it. Do I have any other choice or any alternative solution too attain a better sound quality on ubuntu on my SPDIF-out?

---

### Post by mszargar on 2008-05-27
I changed the question because I succeeded installing the device. Now is there any suggestion for the new problem?

Thanks...

---

### Post by mszargar on 2008-05-28
Any comment is welcome... I am just trying to change platform completely.

---

