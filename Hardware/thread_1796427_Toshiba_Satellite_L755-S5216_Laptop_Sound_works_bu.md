---
title: "Toshiba Satellite L755-S5216 Laptop: Sound works but earphone jack doesn't"
date: 2011-07-03
forum: Hardware
---

### Post by tmowad on 2011-07-03
Hey guys

Here's my issue -- 
earphone jack doesn't work in Ubuntu 11.04, but it works in Windows 7.  

If I plug in the earphones, the sound keeps playing out of the speakers.  

Here's the output of
> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

[http://www.alsa-project.org/db/?f=e9a3cf4f390988c4eb20fc7e8d26a6ea91d6f1b6](http://www.alsa-project.org/db/?f=e9a3cf4f390988c4eb20fc7e8d26a6ea91d6f1b6)

Here is lsmod output:
> Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
joydev                 17606  0 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33211  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
rtl8192ce             123008  0 
rtlwifi                85089  1 rtl8192ce
i915                  514985  3 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              294370  2 rtl8192ce,rtlwifi
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
cfg80211              178528  2 rtlwifi,mac80211
snd                    67382  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
psmouse                73535  0 
soundcore              12680  1 snd
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
sparse_keymap          13898  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
libahci                26642  1 ahci
atl1c                  41171  0 Any help is greatly appreciated!
--Tom

---

### Post by tmowad on 2011-07-03
I guess this seems weird:

> 
!!ALSA Version !!------------  

Driver version:     1.0.23 
Library version:    1.0.24.1 
Utilities version:  1.0.24.2


---

### Post by tmowad on 2011-07-03
Not sure if this stuff will help, looked for what packages I might need to change if those versions shouldn't be different...

> 
tmowad@tomslaptop:~$ dpkg -l|grep 1.0.24
ii  alsa-base                                                      1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-utils                                                     1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  intel-gpu-tools                                                1.0.2+git20100324-0ubuntu1                 tools for debugging the Intel graphics driver
ii  lib32asound2                                                   1.0.24.1-0ubuntu5                          shared library for ALSA applications (32 bit)
ii  libasound2                                                     1.0.24.1-0ubuntu5                          shared library for ALSA applications
ii  libasound2-plugins                                             1.0.24-0ubuntu2                            ALSA library additional plugins
ii  linux-sound-base                                               1.0.24+dfsg-0ubuntu1                       base package for ALSA and OSS sound systems
ii  modemmanager                                                   0.4+git.20110124t203624.00b6cce-2ubuntu1   D-Bus service for managing modems


> 
ii  libsndfile1                                                    1.0.23-1build1                             Library for reading/writing audio files


---

### Post by eholly on 2011-07-06
I have the same problem (earphones silent in 11.4 and fine in windows) on my Toshiba L755 S5216.

Is there any help for this??

            E Holly

---

### Post by lidex on 2011-07-06
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by eholly on 2011-07-07
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Thanks lidex



That worked great.

          E Holly

---

### Post by tmowad on 2011-07-19
Worked for me too thanks lidex :-)

---

