---
title: "FIFINE K669B USB microphone does not work on Ubuntu 20.04"
date: 2020-06-08
forum: Hardware
---

### Post by carcamovski on 2020-06-08
I have bought a FIFINE K669B USB microphone. Ubuntu 20.04 it is able  to detect the USB microphone, however if I go to pavucontrol settings  and select the microphone as input device, it doesn't detect any signal  from it. In fact it does not show the bar where you can see if there is  any input sound. I have also tried the microphone using another  applications like Zoom or Discord, but even if you turn the volume of  the microphone to the max the OS does not receive any signal.  Additionally, the mic works when the system boots and then the mic is  connected. However, it does not work when the mic is kept connected  after reboot.
  What would be the steps to make the USB microphone work on Ubuntu?
  Cheers
  Info: arecord -L


```
sysdefault:CARD=Device
    USB PnP Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Front speakers
surround21:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Hardware device with all software conversions
usbstream:CARD=Device
    USB PnP Audio Device
    USB Stream Output
```


lsmod


```
lsmod|grep snd
snd_hda_codec_hdmi     61440  1
snd_usb_audio         258048  2
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hda_codec_via      20480  1
snd_rawmidi            36864  1 snd_usbmidi_lib
snd_hda_codec_generic    81920  1 snd_hda_codec_via
snd_seq_device         16384  1 snd_rawmidi
mc                     53248  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
snd_timer              36864  1 snd_pcm
snd                    90112  22 snd_hda_codec_generic,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
```

---

