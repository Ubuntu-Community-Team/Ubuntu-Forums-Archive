---
title: "Subwoofer problems Vostro 5470"
date: 2014-08-24
forum: Hardware
---

### Post by rogerio-pld on 2014-08-24
I recently bought a Dell Vostro 5470, which comes with a subwoofer and a ALC290 card. I also have an Inspiron 1564 that has a nice audio volume and good quality. My expectations were that the Vostro should sound louder and better than the Inspiron, because it has a newer sound card plus the subwoofer.
After some research I found [this]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1211920") bug, reporting no audio from subwoofer. I did some tests playing low frequencies, and that is not my problem, I can hear very clear and loud the subwoofer.
The problem is that I constantly hear noise from the subwoofer even with headphones, sounds like static noise with some glitches.


Any thoughts?
```

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC290 Analog [ALC290 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
**aplay -L**
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
equal
plugequal
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=HDMI,DEV=0
    HDA Intel HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA Intel HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA Intel HDMI, HDMI 2
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Hardware device with all software conversions
sysdefault:CARD=PCH
    HDA Intel PCH, ALC290 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC290 Analog
    Hardware device with all software conversions

```

---

### Post by vicente-luchi on 2014-08-30
Hi Rogerio, I also have a Vostro 5470, and was having the same problem as you. I tried a lot of things to solve the subwoofer noise, then found this: [https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Pops_when_starting_and_stopping_playback](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Pops_when_starting_and_stopping_playback). Note that I have done this in 14.10 (Ubuntu, not Kubuntu, Xubuntu,...), but I think it should work on the 14.04.
I was also using laptop_mode_tools to save battery power, so I disabled the power save for the sound card there too.

---

### Post by Azshaari on 2014-10-19
Hi,
Im currently an owner of a Vostro 5470 with ubuntu 14.04.1LTS  (instead of the default 12.04it came with) and I have solved this issue :)
I looked a while several forums and stumbled upon a commit with info about this

The useful files were found at
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

Use this files at your own responsability.
In my case, this managed to detect my subwoofer and significantly increase the output volume.

I also created a thread about this for any other doubts or constructive addendums, since the Dell-specific forum wont be supported for long, and I did not find an answer there.
[http://ubuntuforums.org/showthread.php?t=2249148](http://ubuntuforums.org/showthread.php?t=2249148)
Greetings

---

