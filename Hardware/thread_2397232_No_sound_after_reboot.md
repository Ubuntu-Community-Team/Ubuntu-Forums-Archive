---
title: "No sound after reboot"
date: 2018-07-26
forum: Hardware
---

### Post by edwinricethe4th on 2018-07-26
I'm relatively new to the forums although I have been experimenting off and on with linux systems for years. Please forgive any etiquitte mistakes. :P I have been addressing this issue for what seems like a week to no avail. So, I was hoping someone more experienced in the overwhelming world of audio backends could help.

Briefly, after sometime modifying the settings in alsamixer & pavucontrol in addition to the system settings, I managed to finally produce sound from my hardware. However, a reboot reverted all of that hardwork. I'll post the few things I've learned to post in searching various topics among these forums and others.

I'm running KDE Neon, dual booting with Windows 10, and the sound card is a [URL="http://support.creative.com/Products/ProductDetails.aspx?catID=1&prodID=14000&prodName=X-Fi%20Fatal1ty"]Creative Soundblaster model.
[/URL]
```

uname -r

```
returns:
```

4.15.0-29-generic

```

```

aplay -l

```
returns:
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

cat /proc/asound/cards

```
returns:
```

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7510000 irq 39
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17
 2 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xf7304000 irq 18
 3 [U0x46d0x825    ]: USB-Audio - USB Device 0x46d:0x825
                      USB Device 0x46d:0x825 at usb-0000:00:1a.0-1.2, high speed

```

```

sudo lsmod | grep snd

```
returns:
```

snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    98304  1
snd_hda_codec_ca0132    61440  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_usb_audio         196608  1
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hda_intel          40960  4
snd_hda_codec         126976  5 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_ca0132,snd_hda_codec_realtek
snd_hda_core           81920  6 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_ca0132,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_hda_codec,snd_usb_audio
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  24 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_ca0132,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd

```

I've currently installed alsa and pulseaudio in a desparate attempt to strike lucky. If I've forgotten anything - which I'm sure I have - I'll be happy to provide it. Thank you in advance!

EDIT 1:

Pulseaudio also shows output in pavucontrol.

---

### Post by Yellow Pasque on 2018-07-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

