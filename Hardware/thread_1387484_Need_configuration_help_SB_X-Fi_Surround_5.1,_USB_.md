---
title: "Need configuration help: SB X-Fi Surround 5.1, USB Audio"
date: 2010-01-21
forum: Hardware
---

### Post by terp4life2001 on 2010-01-21
I've got an Acer Aspire Revo (Nvidia-ION platform) and I couldn't get it's onboard HDMI port to do surround sound. I'm pretty sure that I determined it to be unsupported, so I grabbed a USB Sound Blaster X-Fi adapter, but I can't get it to work either.

I'm trying to get all 5.1 channels to work over the SPDIF port. It's going directly into a receiver from the sound card.

I can get sound out of front left, front center and front right, but none of the rear channels or the sub woofer.

I've tried a variety of .asoundrc files and tried testing with 'speaker-test' as well as mplayer. I've also tried using pulseaudio and I've tried every option in the pulseaudio mixer.

I followed the ALSA debug guide, but it didn't help me.

aplay seems to display the device correctly and 'snd-usb-audio' gets loaded. alsamixer on the other hand shows- 

rwlove@lefteye:~$ alsamixer -c 1
No mixer elems found

which I find strange... I've scoured the internet and tried everything I could find. Unfortunately most posts are regarding the PCI versions of this sound card series.

My distro is mythbuntu 9.10 (karmic), but my guess is that this is universal to all karmic releases.

Any suggestions on how to get all channels over SPDIF working would be very appreciated.

Thanks,

//Rob

rwlove@lefteye:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: S51 [SB X-Fi Surround 5.1], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: S51 [SB X-Fi Surround 5.1], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

rwlove@lefteye:~$ aplay -L
front:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    Front speakers
surround40:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=S51,DEV=0
    SB X-Fi Surround 5.1, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

---

### Post by terp4life2001 on 2010-01-24
rwlove@lefteye:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

rwlove@lefteye:~$ speaker-test -c 6 -D iec958:CARD=S51 -t wav

speaker-test 1.0.20

Playback device is iec958:CARD=S51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 87381
Period size range from 48 to 43690
Using max buffer size 87380
Periods = 4
was set period_size = 21845
was set buffer_size = 87380
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE

This only gives output on front right and front left, but the terminal output goes much faster than the audio. The terminal will have cycled through all 6 channels, while the audio is playing on one of the channels...

rwlove@lefteye:~$ speaker-test -c 6 -D pulse -t wav

speaker-test 1.0.20

Playback device is pulse
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE

The timing is better with pulse. The terminal doesn't show speaker-test moving to the next channel until the audio has completed on the current channel. Still now sound out of the rear channels.

rwlove@lefteye:~$ ls .asoundrc /etc/asoundrc
ls: cannot access .asoundrc: No such file or directory
ls: cannot access /etc/asoundrc: No such file or directory

---

### Post by ceminino on 2010-02-12
did you figure out how to have the surround?

---

### Post by terp4life2001 on 2010-02-12
> **ceminino said:**
> did you figure out how to have the surround?

Unfortunately, no. I was only ever able to get the front three channels. I returned the sound device to the store for a refund.

---

### Post by ceminino on 2010-02-12
how did you manage the front three? I'm still stuck with just left and right :/

---

### Post by terp4life2001 on 2010-02-12
> **ceminino said:**
> how did you manage the front three? I'm still stuck with just left and right :/

I'm really not going to be able to help much. It has been a few weeks since I looked at it and I didn't take notes. When I look at my bash history on that box I can see I was running speaker-test a lot. This looks like the most likely command, but I was playing with a lot of options in the mixer(s), .asoundrc and module options-

speaker-test -c 6 -D iec958:CARD=S51 -t wav

BTW: I was going through SPDIF

---

### Post by ceminino on 2010-02-12
ok thanks, I'm also trying with S/PDIF, it works fine with zindowz though :/

---

### Post by ceminino on 2010-02-17
after trying for hours (and hours...), I've learned it was pointless since the alsa driver doesn't support surround yet...

[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=xfi](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=xfi)

---

### Post by pkchips on 2010-05-06
Surround sound can be achieved with PulseAudio driver, I remember doing it a long time ago in 9.04. However, it makes programs buggy - you get clicks for example when you shift position in a movie, and every now and then the movie runs out of sync with the sound.

To find out how to do it, do some more searching about pulseaudio and surround sound.

I wanted to know if the situation had been improved in 10.04?

---

