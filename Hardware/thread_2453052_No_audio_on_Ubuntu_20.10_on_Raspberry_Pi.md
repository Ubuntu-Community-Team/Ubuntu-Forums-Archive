---
title: "No audio on Ubuntu 20.10 on Raspberry Pi"
date: 2020-11-02
forum: Hardware
---

### Post by AndrewWalker on 2020-11-02
I've installed Ubuntu on my Raspberry Pi 4 and all is working well except I have no sound. I'm using the Plasma desktop and I have dual monitors with video via HDMI to DVI adaptor cables as my monitors don't have HDMI input. The sound is supplied by the AUX output on the Raspberry Pi and should play via the cable to my monitor but I get no sound, I know the setup works on the Rasbian setup but not on Ubuntu.
My aplay -l is as follows
```
fred@fred-RaspPi:/boot$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: b1 [bcm2835 HDMI 1], device 0: bcm2835 HDMI 1 [bcm2835 HDMI 1]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: b2 [bcm2835 HDMI 2], device 0: bcm2835 HDMI 2 [bcm2835 HDMI 2]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: Headphones [bcm2835 Headphones], device 0: bcm2835 Headphones [bcm2835 Headphones]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
fred@fred-RaspPi:/boot$ 

```
Most of the suggestions online seem to be related to the Raspbian distro but none of the fixes relate to Ubuntu. Does anyone have any suggestions? Alsamixer only shows one device as shown here
```
Card: bcm2835 Headphones                                                                                            F1:  Help               &#9474;
&#9474; Chip: Broadcom Mixer                                                                                                F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                                            F6:  Select sound card  &#9474;
&#9474; Item: Headphone [dB gain: 0.30]                                                                                     Esc: Exit
```
so I think it's an alsa set up issue.

---

### Post by adriano8 on 2021-04-04
I have same problem.
I'm using KDE Plasma as GUI and after started pulseaudio the sound devices show up.

Try run on a terminal "pulseaudio --start" or check if the pulseaudio service was started on login.

---

