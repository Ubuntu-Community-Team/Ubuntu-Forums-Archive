---
title: "Asus UL80JT Win7 Dual Boot (Will Not Suspend)"
date: 2011-03-05
forum: Hardware
---

### Post by christopher5g on 2011-03-05
I am trying to get my UL80JT as in order as I can.

I have tried a few fixes but nothing specific to my problem has been posted, so here it goes.

I have tried creating a [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]**/etc/pm/config.d/unload_modules.sh** and had added

#!/bin/bash
[/FONT][/FONT][/COLOR][COLOR=#FF0000]**SUSPEND_MUDULES="**[/COLOR][COLOR=#FF0000][B]auth9k"
SUSPEND_MUDULES="usbhid"[/B][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana][/FONT][/FONT][/COLOR]

So far nothing...

ubuntu@UL80JT:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
vboxnetadp              5764  0 
vboxnetflt             19131  0 
vboxdrv              1817384  2 vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    15451  4 
nvidia              10221046  42 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                    1497  2 
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
ath9k                 101858  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common            6874  1 ath9k
psmouse                62080  0 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ath9k_hw              314731  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
mac80211              267099  2 ath9k,ath9k_common
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
asus_laptop            16668  0 
uvcvideo               62379  0 
cfg80211              170485  4 ath9k,ath9k_common,ath,mac80211
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
serio_raw               4910  0 
intel_agp              32334  0 
v4l2_compat_ioctl32    12614  1 videodev
sparse_keymap           3837  1 asus_laptop
lp                     10201  0 
led_class               3393  2 ath9k,asus_laptop
video                  22176  0 
output                  2527  1 video
joydev                 11395  0 
parport                37032  3 parport_pc,ppdev,lp
reiserfs              245000  3 
usbhid                 42030  0 
hid                    84710  1 usbhid
usb_storage            50436  1 
ahci                   22210  4 
atl1c                  34955  0 
libahci                26148  1 ahci
ubuntu@UL80JT:~$ 

If anyone needs more info just let me know, any help would be appreciated!

---

