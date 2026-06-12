---
title: "Dell GM45 Graphics Bug"
date: 2015-03-03
forum: Hardware
---

### Post by Furbybrain on 2015-03-03
I'm having graphics bugs with my Intel Inspiron laptop on 14.10. [They look like this]("http://imgur.com/3pHLp7H"), and get worse as time goes on after bootup, sometimes forcing me to log out and back in. My laptop uses a GM45 Intel Chipset for graphics. I was told lsmod listed modules, but in my ignorance I couldn't tell which was the graphics driver. I was looking into updating the driver, but the website [https://01.org/linuxgraphics/](https://01.org/linuxgraphics/) says it only supports 14.04.

Here's an lsmod dump:
```
Module                  Size  Used by
bnep                   19543  2 
rfcomm                 69509  0 
bluetooth             446190  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
wl                   6367694  0 
gpio_ich               13579  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
snd_hda_codec_idt      63632  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_idt
dell_laptop            18227  0 
dcdbas                 14928  1 dell_laptop
coretemp               13441  0 
joydev                 17344  0 
serio_raw              13434  0 
snd_hda_intel          30379  3 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104102  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21093  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29513  2 snd_pcm,snd_seq
snd                    87611  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  917658  4 
cfg80211              510218  1 wl
drm_kms_helper         61627  1 i915
drm                   310919  6 i915,drm_kms_helper
i2c_algo_bit           13406  1 i915
soundcore              15052  2 snd,snd_hda_codec
shpchp                 37040  0 
wmi                    19193  1 dell_wmi
mac_hid                13227  0 
video                  20128  1 i915
cuse                   13445  3 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ums_realtek            18045  0 
uas                    23215  0 
usb_storage            66398  2 uas,ums_realtek
psmouse               106548  0 
ahci                   34062  2 
libahci                32424  1 ahci
sky2                   58156  0 


```

---

### Post by houstonbofh on 2015-03-03
video                  20128  1 i915

To start, try booting a LiveCD of 14.04.  I have found the LTS releases to be much more stable, and the 6 month releases to be more like beta status lately...  You may just want to move back.

Otherwise, you can try this thread.  [http://ubuntuforums.org/showthread.php?t=2266058](http://ubuntuforums.org/showthread.php?t=2266058)

---

### Post by Furbybrain on 2015-03-03
Thanks for finding that, I tried to search the forum but nothing came up. I obviously wasn't persistent enough. I've just followed the advice and I'll feedback whether the problem re-emerges or not.

---

### Post by Furbybrain on 2015-03-04
Unfortunately the problem has appeared again :( I may have to consider going back to 14.04.

I'm on x64 if that is likely to be an issue.

---

