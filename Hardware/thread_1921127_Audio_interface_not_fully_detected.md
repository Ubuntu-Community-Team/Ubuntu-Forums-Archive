---
title: "Audio interface not fully detected"
date: 2012-02-06
forum: Hardware
---

### Post by huwshimi on 2012-02-06
Hi,

I have a Presonus AudioBox 44vsl. After plugging it in it appears to be partially detected, but not enough that I can get sound in or out of it.

The interface does not appear under Sound Settings > Hardware. However it does appear as an interface in qjackctl.

'cat /proc/asound/cards' shows the correct interface:
```
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xb0900000 irq 47
 1 [VSL            ]: USB-Audio - AudioBox 44 VSL
                      PreSonus AudioBox 44 VSL at usb-0000:00:1d.7-1.2, high speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xb0840000 irq 48
```

and 'cat /proc/asound/modules' shows:
```
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel
```

but that's about the end of the good news.

'aplay -l' doesn't show the device:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

'arecord -l' doesn't either:
```
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Here are some more details that might help.

'lsusb':
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 05ac:0245 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 004: ID 194f:0102  
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
```

'lsmod | grep snd':
```
snd_seq_dummy          12798  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_cirrus    23965  1 
snd_hda_intel          33773  5 
snd_usb_audio         122982  0 
snd_hda_codec         127723  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_seq,snd_rawmidi
snd                    78855  22 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
```

'lspci |grep -i usb':
```
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
```

That's about everything I could think of that might be useful. Any suggestions for how to debug this much appreciated.

Thanks in advance.

Huw

---

### Post by huwshimi on 2012-02-16
Any suggestions?

---

