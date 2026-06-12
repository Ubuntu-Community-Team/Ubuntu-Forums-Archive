---
title: "Sound Issues with Ubuntu 10.10 upgrade"
date: 2010-12-17
forum: Hardware
---

### Post by Trilby on 2010-12-17
I've just up graded from 64 Bit Ubuntu 10.04 to 10.10 on my Acer laptop. Everything works fine except for sound. The internal speakers outright don't work. I've managed to get some external speakers of mine to work by changing the Sound Preferences >> Hardware >> Profile settings, but none of these setting allow me to use my laptop's own speakers.

Can anyone help me?
Thanks,
Trilby

---

### Post by Trilby on 2010-12-18
This may help:

```

:~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:47 memory:f0a00000-f0a03fff


```

As may this:

```

:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50372  0 
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   299524  1 
joydev                 11363  0 
arc4                    1497  2 
snd_hda_intel          26019  6 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
i915                  332088  3 
iwlagn                202721  0 
snd_pcm                89104  4 snd_hda_intel,snd_hda_codec
drm_kms_helper         32836  1 i915
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
drm                   206161  4 i915,drm_kms_helper
iwlcore               146875  1 iwlagn
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  3 snd_seq_midi,snd_seq_midi_event
mac80211              266657  2 iwlagn,iwlcore
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              170293  3 iwlagn,iwlcore,mac80211
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
snd                    64117  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms               8667  0 
psmouse                62080  0 
serio_raw               4910  0 
memstick               10185  1 jmb38x_ms
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
soundcore               1240  1 snd
lp                     10201  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
output                  2527  1 video
intel_agp              32144  2 i915
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
ahci                   21857  0 
tg3                   135768  0 
libahci                26199  4 ahci
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci


```

---

### Post by kostkon on 2010-12-18
Try deleting the your .pulse folder, i.e.:
```
rm ~/.pulse
```
then logout and login and test/configure your sound again.

---

### Post by Trilby on 2010-12-18
> **kostkon said:**
> Try deleting the your .pulse folder, i.e.:
```
rm ~/.pulse
```
then logout and login and test/configure your sound again.

This didn't do anything so I tried:
```
rm -r ~/.pulse
```
which got rid of the folder.

However, after rebooting, my sound problems remain unresolved.

---

### Post by echogene on 2010-12-22
When I was having trouble with my sound at one point, something someone said about alsamixer fixed it.  Run 'alsamixer' in the terminal and check the sound levels in that.  Try moving them up and down and see if that makes a difference.  Escape is the button to quit it.

---

### Post by Trilby on 2010-12-22
> **echogene said:**
> When I was having trouble with my sound at one point, something someone said about alsamixer fixed it.  Run 'alsamixer' in the terminal and check the sound levels in that.  Try moving them up and down and see if that makes a difference.  Escape is the button to quit it.

Alas, I've have already tried this. Just spent another fruitless few minutes playing with it. Nothing there to suggest anything is muted or otherwise disabled that shouldn't be.

---

### Post by echogene on 2010-12-23
The only other potentially useful thing that worked for me when my sound went at other times was when I compiled the ALSA drivers from scratch.  I think I followed this: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) .  I was a bit more of a noob at the time, so I avoided doing it as it looked scary, but it worked for me twice when my sound went.  The third time was, as said before, just fixed by alsamixer.

---

### Post by Trilby on 2011-01-03
> :shock: Ok, the bizarrest thing just happened.
I booted Windows to see if my speakers still worked there -- They did. Having established that and, not having any reason to be using Windows, I rebooted to Ubuntu with the aim of doing something useful, leaving my external speakers unplugged from the laptop. Imagine then, how surprised I was when I heard Ubuntu's little drum sound on boot-up. I don't know how but somehow my internal speakers work again yet I cannot see how booting Windows would fix anything.

I just hope it lasts.

Thanks for all your help,
Trilby

UPDATE: My internal speakers didn't work again today so I repeated yesterday's experiment. I would seem that my internal speakers only work if I boot Windows first and then restart to Ubuntu. I can't see why this should be though. I'm going to see if they work when I boot from a live disk. If that works I'll proceed to a fresh install.

---

