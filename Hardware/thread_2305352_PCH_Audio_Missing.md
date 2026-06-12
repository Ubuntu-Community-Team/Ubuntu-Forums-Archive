---
title: "PCH Audio Missing"
date: 2015-12-05
forum: Hardware
---

### Post by antar on 2015-12-05
Sound (speaker and headphone jacks) stopped working on my system a few days ago (Ubuntu 14.04). Digging into the problem, aplay -l shows no PCH device:

```

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
card 3: Device [USB Advanced Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

whereas it shows up under cat /proc/asound/cards:

```

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7a34000 irq 54
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7a30000 irq 52
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17
 3 [Device         ]: USB-Audio - USB Advanced Audio Device
                      C-Media Electronics Inc. USB Advanced Audio Device at usb-0000:00:14.0-3.2, ful
 4 [IVTV0          ]: CX2341[56] - IVTV-0
                      CX2341[56] #0 Hauppauge WinTV PVR-150 TV/FM Radio/Line-In Capture

```

I've gone through the complete sound troubleshooting guide (the results of running the alsa-info script are [here]("http://pastebin.com/78P80dSh")).

So far, the main troubleshooting step I've tried is adding the following line to /etc/modprobe.d/alsa-base.conf (to no avail):

```

options snd-hda-intel model=pch position_fix=1

```

Likely relevant: I'm getting audio packages from the alsa-daily ppa.

---

### Post by antar on 2015-12-08
Been updating daily and still no audio... Has no one encountered anything like this before? Is it possible something's gone wrong with the hardware?

---

### Post by Yellow Pasque on 2015-12-09
These messages might give you something to google:
```
[    2.848202] snd_hda_codec_realtek hdaudioC1D2: ALC1150: SKU not ready 0x00000000
[    2.869073] snd_hda_codec_generic: probe of hdaudioC1D2 failed with error -16
[    2.869076] hdaudio hdaudioC1D2: Unable to bind the codec
```

---

