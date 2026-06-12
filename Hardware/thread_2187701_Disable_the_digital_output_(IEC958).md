---
title: "Disable the digital output (IEC958)"
date: 2013-11-13
forum: Hardware
---

### Post by Bubba_Jackson on 2013-11-13
Hey guys,

I have a question: is it possible to disable the digital playback device on a sound card? I'm testing an application and it produces a problem only on this kind of hardware (the app is functioning as it should on other PCs with only analog playback devices), so I'm trying to see if this is the issue. Is there any way of disabling this playback device? I've tried muting the S/PDIF PCM in alsamixer, tried upgrading the kernel, but to no avail. 

Thanks in advance!

aplay -l
```
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci | grep -i audio
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```

lsmod
```

Module                  Size  Used bybinfmt_misc             6523  1
nls_cp437               4919  1
cifs                  249186  2
snd_hda_codec_via      27111  1
fbcon                  35102  71
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2
snd_hda_codec          74297  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47295  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0
i915                  290772  2
parport_pc             25962  1
joydev                  8740  0
psmouse                63677  0
serio_raw               3978  0
atl1c                  27955  0
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm_kms_helper         29329  1 i915
lp                      7060  0
drm                   163779  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0
hid                    67288  1 usbhid

```

uname -r
```
2.6.32-49-generic
```

---

