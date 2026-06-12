---
title: "Really weak wireless signal"
date: 2012-09-02
forum: Hardware
---

### Post by bucket_brigade on 2012-09-02
On my Lenovo ThinkPad Edge 330 laptop the wireless signal is really weak. The other laptop I have in the same room picks up strong signal from my wifi router but the new one drops the connection constantly and is barely useable.

```

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```

I have installed the drivers provided by realtek and they seem to be loaded fine 

```

r8168                 244911  0 

```

How do I make sure it uses this very driver?

The full lsmod output is below

```

Module                  Size  Used by
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
nvidia              12319264  0 
snd_hda_intel          33773  3 
arc4                   12529  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts_pstor             445196  0 
iwlwifi               332525  0 
thinkpad_acpi          81819  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13253  0 
acer_wmi               28418  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
sparse_keymap          13890  1 acer_wmi
serio_raw              13211  0 
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 acer_wmi
i915                  472941  2 
btusb                  18288  2 
mei                    41616  0 
bluetooth             180104  23 rfcomm,bnep,btusb
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
lp                     17799  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
soundcore              15091  1 snd
i2c_algo_bit           13423  1 i915
parport                46562  3 parport_pc,ppdev,lp
nvram                  14413  1 thinkpad_acpi
video                  19596  1 i915
r8168                 244911  0 


```

---

### Post by ahallubuntu on 2012-09-02
Looks like you have an Intel wireless card, not a Realtek card.  (You have a Realtek wired ethernet card, though.)  The iwlwifi module (you have it loaded) is used for the Intel wireless card.

One thing that seems to improve Intel wireless card connections is to disable "N" connection speeds.  Details here:

[http://ubuntuforums.org/showthread.php?t=1978457](http://ubuntuforums.org/showthread.php?t=1978457)

I have several Ubuntu laptop/netbooks with Intel cards and don't need to do this.  I consider "N" speed essential (I regularly copy lots of data to/from my server wirelessly), but if all you do is Internet stuff slowing down to "G" speed probably won't cause you much issue.

---

### Post by bucket_brigade on 2012-09-02
I tried this
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

Let's see if this does anything. So far so good though. However the signal still is shown as really weak. From what I understand this is a temporary workaround and not a real solution.

---

### Post by Carl.Spackler on 2012-09-07
Two things additional:

Does it have weak wifi with other access points?

Have you tried a live CD from another distribution or another OS on this laptop?

I checked the Lenovo website and if this is a stock e330, the Intel wifi card is not a 5Ghz version but does include bluetooth.

---

