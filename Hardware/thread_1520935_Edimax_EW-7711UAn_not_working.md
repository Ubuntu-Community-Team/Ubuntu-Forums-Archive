---
title: "Edimax EW-7711UAn not working"
date: 2010-06-30
forum: Hardware
---

### Post by asmo on 2010-06-30
Currently installed Ubuntu 10.04 LTS Lucid Lynx 64bit version. My wireless isn't working I have no idea why the modules for it are installed even though the device doesn't seem to be recognised:

Device in bold:

```
bob@bob:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04f9:0033 Brother Industries, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1307:0330 Transcend Information, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
**Bus 001 Device 002: ID 7392:7711  **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Modules I think are connected to the device in bold:

```
bob@bob:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10802  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   278890  1 
**rt2870sta             525366  0 **
arc4                    1473  2 
[B]rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb[/B]
snd_hda_intel          25645  2 
snd_seq_dummy           1782  0 
**rt2x00lib              32133  2 rt2800usb,rt2x00usb**
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_oss            31219  0 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_usb_audio          92747  1 
snd_usb_lib            18978  1 snd_usb_audio
snd_seq_midi            5829  0 
[B]led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib[/B]
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            23388  2 snd_usb_lib,snd_seq_midi
snd_pcm                87850  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
ppdev                   6375  0 
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
snd_hwdep               6924  2 snd_hda_codec,snd_usb_audio
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_timer              23553  2 snd_pcm,snd_seq
bitblit                 5811  1 fbcon
**cfg80211              148386  2 rt2x00lib,mac80211**
v4l2_compat_ioctl32    12020  1 videodev
**crc_ccitt               1675  1 rt2800usb**
parport_pc             29958  1 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1565  1 bitblit
usblp                  12407  0 
snd                    70978  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_rawmidi,snd_pcm,snd_hwdep,snd_seq,snd_timer,snd_seq_device
fglrx                2353422  32 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
psmouse                64608  0 
serio_raw               4918  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
ohci1394               30260  0 
usb_storage            49833  1 
ieee1394               94675  1 ohci1394
ahci                   37646  2 
r8169                  39650  0 
mii                     5237  1 r8169
pata_atiixp             4209  0 

```

Any idea why its not working?? Any help appreciated cheers.

---

### Post by asmo on 2010-06-30
Nevermind sorted. Shouldn't have bothered asking.

---

### Post by B0rat on 2010-08-09
Perhaps you should post your solution! I found this post using Google... but it ain't that helpful tbh. :(

---

