---
title: "Gateway NV59 Microphone not working"
date: 2010-12-11
forum: Hardware
---

### Post by robn30 on 2010-12-11
I have a Gateway NV59 and am having microphone issues, mic is not showing up  in the sound preferences, and therefore not working.  Is there anyway to  get it working?  Thanks.

uname -a
Linux rob-NV59 2.6.35-23-generic-pae #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010 i686 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272X Digital [ALC272X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272X

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#3 <==
Codec: Intel IbexPeak HDMI

---

### Post by robn30 on 2010-12-12
Bump. Anyone have any idea how to fix this issue.  Again my microphone does not even show up under System--->Preferences--->Sound.  Thanks again.

---

### Post by sfbriancl on 2011-03-14
I'm having the same issues with Mint.  I can get the audio kind of working with Cheese, but it sounds really bad.

When I go into the terminal and try to get the info on the audio name, it says there isn't anything at all there:
  
/dev/audio*: No such file or directory

Anybody care to hazard a guess?

---

### Post by mynameisfiber on 2011-06-23
Same problem but with an Acer TimelineX.

fiber@tachyon:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC271X
Codec: Intel IbexPeak HDMI

fiber@tachyon:~$ uname -a
Linux tachyon 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

fiber@tachyon:~$ lsmod | grep snd
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

---

