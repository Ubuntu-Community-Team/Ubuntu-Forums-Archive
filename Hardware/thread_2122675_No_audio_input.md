---
title: "No audio input"
date: 2013-03-05
forum: Hardware
---

### Post by Serdar on 2013-03-05
Hi everybody,
Before I kindly ask for your help, I would like to give you some background and info about my system.

I have installed ubuntu 12.10 64 bit from the Ubuntu minimal cd. Then I installed
```
sudo apt-get install xorg
sudo apt-get install gnome-core --no-install-recommends
sudo reboot
```
I've had "output" and "input" devices on the sound settings and it was working. Then I added my other software such as web browser, office etc, reboot the machine and I lost both input and output devices. (Get dummy sound device in the output section)

I fixed the "output sound problem" with creating /.asoundrc file.
first checked my output sound devices with 
```
aplay -l
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
from results I tested my sound devices with 
```
aplay -D plughw:2,7 /usr/share/sounds/alsa/Front_Center.wav
``` 
it took few attempts to get the sound from the same device :)
this is how my /.asoundrc file looks like
```
defaults.pcm.card 0
defaults.pcm.device 7
defaults.ctl.card 2
```
[B]anyway after the reboot /.asoundrc file fixed the output sound problem and now I can see and use my sound device on the sound settings
but it caused another problem, now I lost the input device,[/B] there is not even a dummy device. see below alsa mixer and gnome sound control pictures
[ATTACH=CONFIG]239816[/ATTACH][ATTACH=CONFIG]239817[/ATTACH]
Below is the recording devices' list, and I have a web cam that I would like to use for input(which was there before that dummy device appeared on the output section)
```
arecord -L
```
```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
usb
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=2
    HDA Intel, ALC1200 Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=2
    HDA Intel, ALC1200 Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=2
    HDA Intel, ALC1200 Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=2
    HDA Intel, ALC1200 Analog
    Hardware device with all software conversions
sysdefault:CARD=V1
    Default Audio Device
front:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    Front speakers
surround40:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    Direct sample mixing device
dsnoop:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    Direct sample snooping device
hw:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    Direct hardware device without any conversions
plughw:CARD=V1,DEV=0
    VF0680 Live! Cam Socialize HD 1, USB Audio
    Hardware device with all software conversions
```
I tried to fix the input problem adding below lines to /.asoundrc file but it did not worked, so what am I missing?
```
defaults.pcm.card 0
defaults.pcm.device 7
defaults.ctl.card 2

pcm.usb
{
    type iec958
    card VF0680
}

pcm.!default
{
    type asym
    playback.pcm
    {
        type plug
        slave.pcm "dmix"
    }
    capture.pcm
    {
        type plug
        slave.pcm "usb"
    }
}
```

Thank you for your help in advance and sorry for the long detailed thread,
SC

---

### Post by Serdar on 2013-03-06
Hi again,
I am giving more details;
I have been trying different solutions for this problem and I deleted my /.asoundrc file and reboot my pc. And all my devices came back again and everything is working again as before. Now I know time to time I am loosing all my devices on the list and get a dummy sound devices. it is random. I still do not know what is causing this problem. 
SC

---

