---
title: "No sound at all ATI Radeon built in card"
date: 2010-12-26
forum: Hardware
---

### Post by djcrash1981 on 2010-12-26
I've just installed my PC with the latest Ubuntu Release 10.10 and I've just found out that I don't have sound, at all.

I'm attaching the lshw output so you can see what I have.

I've tried to set the Audio properties to the different audio cards that the system have detected.

And finally I've added the  ppa:ubuntu-x-swat/x-updates to install the fglrx driver without luck.

I really hope someone can help me because I want to use this PC as a media center, and without sound is not usefull.

Another glitch that I've found is that any video that is played, it appears like it was in fast forward, and I can't find what is doing this.

Thanks for the support.

Regards

---

### Post by djcrash1981 on 2011-01-10
Here is more information about the problem.

***_aplay -l_***
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
[B]tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0[/B]


***_aplay -L_***
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC662 rev1 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC662 rev1 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC662 rev1 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC662 rev1 Digital
    Hardware device with all software conversions
[B]hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions[/B]

And _[here]("http://www.alsa-project.org/db/?f=0af2b46aa904dd2ec32152a9f8b9bc8af4ab3cc6")_ is the report with the alsa script

I hope with this information someone can help me to diagnose the problem.

---

### Post by gar37bic on 2013-03-26
I don't know if you solved your audio problem, but I had a similar problem.  On a new install of 12.10 (Kubuntu), after a raft of updates the sound stopped working.  No errors, everything seemed to work but no sound came out.  After rummaging around for a while, and installing the pulseaudio sound control app, I discovered that the ATI Radeon Catalyst drivers for my video cards had changed the sound output from analog stereo to go through the ATI video and out to HDMI.  I was able to change this back to analog stereo in the pulseaudio control panel.  I may have been able to do that from the System Settings as well, but I think I tried and failed.

---

### Post by coffeecat on 2013-03-26
Back to sleep, old thread.

---

