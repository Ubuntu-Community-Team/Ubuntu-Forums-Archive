---
title: "No sound on 11.04 (or 10.10) with nVidia chipset"
date: 2011-09-09
forum: Hardware
---

### Post by Matt Gotts on 2011-09-09
Sorry if this has been dealt with a thousand times before, but I've got no sound from my install of Xubuntu.

I originally had 10.10 but updated to 11.04 to see if that would fix it, but no.  I've seen threads saying to allow user access to the audio group - I am and still nothing.  I've enabled all the various faders I can but no sound.

aplay -l gives:

```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

While aplay -L:

```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Front speakers
surround40:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    4.0 Surround output to Front and Rear speakers
surround41:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Direct sample mixing device
dmix:CARD=nForce2,DEV=2
    NVidia nForce2, NVidia nForce2 - IEC958
    Direct sample mixing device
dsnoop:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Direct sample snooping device
dsnoop:CARD=nForce2,DEV=2
    NVidia nForce2, NVidia nForce2 - IEC958
    Direct sample snooping device
hw:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Direct hardware device without any conversions
hw:CARD=nForce2,DEV=2
    NVidia nForce2, NVidia nForce2 - IEC958
    Direct hardware device without any conversions
plughw:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Hardware device with all software conversions
plughw:CARD=nForce2,DEV=2
    NVidia nForce2, NVidia nForce2 - IEC958
    Hardware device with all software conversions
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
rear:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC1
    Rear speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample mixing device
dmix:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample mixing device
dsnoop:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample snooping device
dsnoop:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample snooping device
hw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct hardware device without any conversions
hw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct hardware device without any conversions
plughw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Hardware device with all software conversions
plughw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Hardware device with all software conversions
```

I should point out that although I've listed the data above, I have no idea what it all means and only knew the commands via other threads.  Total noob here!

Aside from this all is OK - have had repeating boot issues but fixed those via other threads plus some support via my own thread.

Any suggestions much appreciated!

Cheers

Matt

---

### Post by Matt Gotts on 2011-09-15
Bump!  (hoping that someone can help!)

---

### Post by MrSpike16 on 2011-09-15
You have two active hardware sound devices.  Since >  Total noob here! I would suggest you remove one.

Turn off the on board one in BIOS or remove the PCI card from computer.  Your audio may start working for you.  If not check for muted outputs using a mixer.

I prefer GNOME ALSA Mixer myself.  If you still have no sound then it will at least make it much easier for others to assist you (with only one sound card).

---

### Post by Matt Gotts on 2011-09-19
Suddenly I was on the BBC website and a video made loads of noise!  Turns out the website I had been using as a reference has a problem on Linux in Chromium with no sound!!  Thanks for the help though, appreciated.

Regards

Matt

---

