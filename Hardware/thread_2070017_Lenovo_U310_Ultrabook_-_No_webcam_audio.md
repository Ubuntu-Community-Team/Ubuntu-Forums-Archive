---
title: "Lenovo U310 Ultrabook - No webcam audio"
date: 2012-10-11
forum: Hardware
---

### Post by brianfast on 2012-10-11
Hey I have a lenovo u310. It has a "Lenovo EasyCamera". This camera should have a microphone, and it worked in windoze.

I can see the video in Guvcview, but I do not get any audio. I tried looking at alsa-mixer, but none of the audio inputs seem to respond to sound in the room.

When I set the input sound in guvcview to "default" i can hear some sound. But in skype (the only application that matters) when I try to select audio I can only select pulse audio. Pulse audio only sees one input, and it fails to carry sound.

Here is my lmod:```
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
usb_storage            49198  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17693  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62358  1 
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97362  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
iwlwifi               396989  0 
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 iwlwifi
soundcore              15091  1 snd
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  473240  4 
drm_kms_helper         46978  1 i915
r8169                  62099  0 
drm                   242038  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
video                  19596  1 i915
```

---

