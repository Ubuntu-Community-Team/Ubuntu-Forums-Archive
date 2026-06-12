---
title: "Asus Xonar DG sound card: microphone not working"
date: 2016-02-22
forum: Hardware
---

### Post by Fluggonaut on 2016-02-22
Hello,
I am running Kubuntu 15.10 with an Asus Xonar DG sound card and my microphone isn't working. Instead, it seems to use my system's sound output as input.

My AlsaInfo: [http://www.alsa-project.org/db/?f=0ac957ddf87a2a05421e6a2334e933ba057afd93](http://www.alsa-project.org/db/?f=0ac957ddf87a2a05421e6a2334e933ba057afd93)

The KDE Volume Control (pulseaudio?) says there is "no input device". Is the sound card incompatible or is my problem fixable?

---

### Post by Bucky Ball on 2016-02-22
Welcome. In Pulseaudio Volume Control at the 'Input' tab can you select your device in the 'Port' dropdown menu? Forget about the 'Playback' tab as you won't see anything there unless there is an audio stream present (audio input/output). 

Sounds like you might have the input port set to the internal microphone as device and not the external soundcard.

You seem a bit unsure, but make sure you are referring to Pulseaudio Volume Control. Launch it from the menu, not the speaker icon to make certain that is what you are diddling with.

See attached screenshot for what you should be looking at, or something like it. Where it says microphone in mine, if you click there do you get an option for your soundcard? If your card is recognised it should be available in the Port devices in those tabs.

You might post the output of:

```
lsusb
```

... between code tags if none of this helps.

---

### Post by Fluggonaut on 2016-02-22
That's exactly where it says "no input devices available", I attached a screenshot. It's in German, but you should be able to figure out what's going on.

```

$ lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c245 Logitech, Inc. G400 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Unsure how lsusb would help since I am trying to use the 3.5mm jack for my mic, but here it is.

---

### Post by Bucky Ball on 2016-02-23
So this a PCI soundcard in a desktop computer? Apologies for assuming it was a USB outboard audio interface ... :|

If it is a PCI card and it's saying 'no devices available' this would be a problem with not just the mic. Can you do anything with that soundcard? Output or input?

---

### Post by Fluggonaut on 2016-02-23
Yes, it's a PCI card.

Audio output works just fine, i haven't tested the other functions of the card besides the mic.
In Windows, the card works just fine, so we can assume that the card itself isn't broken.

---

### Post by Bucky Ball on 2016-02-23
Not broken, just not seen in Linux, or some of it. Knowing the card is fully functional we can be fairly certain it is software related (or this hardware is not getting on with another hardware component under Ubuntu).

So you're plugging in to the outputs of the card and getting audio, the card shows up in PAVControl under 'Playback> Port> Asus Xonar DG' (or something like it) when you are playing an audio stream, say playing an MP3, and that outputs to headphones or speaker via the output socket(s) of the sound card?

Just to confirm.

---

### Post by Fluggonaut on 2016-02-23
> **Bucky Ball said:**
> Knowing the card is fully functional
Glad to hear!

> **Bucky Ball said:**
> 
So you're plugging in to the outputs of the card and getting audio, the card shows up in PAVControl under 'Playback> Port> Asus Xonar DG' (or something like it) when you are playing an audio stream, say playing an MP3, and that outputs to headphones or speaker via the output socket(s) of the sound card?
Yes.

---

### Post by Bucky Ball on 2016-02-23
Plug in a mic, go to 'Recording' (Aufnahme) and there are no options? Strange that output works, input doesn't. 

You could try this as I notice you have the internal audio still enabled. Boot to the BIOS and see if there is an option to switch of the audio on the motherboard. There usually is somewhere in there. There could be some confusion between you internal MB audio card and the XG.

---

### Post by Fluggonaut on 2016-02-24
That's not internal audio, that's the HDMI audio from the graphics card (Radeon R9 270X). The onboard audio is already disabled in the UEFI.

---

### Post by Fluggonaut on 2016-03-03
So does nobody have an idea or a path to lead me to? :(

---

