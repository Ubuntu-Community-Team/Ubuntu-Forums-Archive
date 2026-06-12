---
title: "microphone doesn't work from ubuntu 15.10 Audio device:Intel Corporation 82801H"
date: 2016-08-22
forum: Hardware
---

### Post by spidduz on 2016-08-22
Hello all
I have some problem with Ubuntu 15.10 and Ubuntu 16.04
The audio device Intel Corporation 82801H works perfectly with ubuntu 14.10. 
i try to install the new version and it seems that the microphone doesn't work.
when i lanch arecord -vv -fdat stackoverflow.wav, the result is 0%.


:~# lsmod
Module                  Size  Used by
gpio_ich               16384  0
ppdev                  20480  0
coretemp               16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  0
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
input_leds             16384  0
joydev                 20480  0
lpc_ich                24576  0
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
parport_pc             32768  0
parport                49152  2 ppdev,parport_pc
soundcore              16384  1 snd
shpchp                 36864  0
8250_fintek            16384  0
mac_hid                16384  0
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
i915                 1134592  3
psmouse               126976  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        131072  1 i915
e1000e                237568  0
pata_acpi              16384  0
drm                   360448  5 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp

can someone help me ?

Thanks 
Andrea

---

