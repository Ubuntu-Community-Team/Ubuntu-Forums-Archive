---
title: "No visual effects anymore"
date: 2011-12-28
forum: Hardware
---

### Post by jimmydean886-2 on 2011-12-28
Hello, all!

I turned on my computer once to find that the visual effects not only in KDE-Plasma but also in Unity were turned off. I couldn't turn them back on, so I ran the Unity support test and got this output:
```
 Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: unable to create the OpenGL context
```This is the output from lsmod
```

Module                  Size  Used by
snd_hrtimer            12744  1 
bnep                   18436  2 
rfcomm                 47946  4 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
snd_atiixp_modem       19108  0 
snd_via82xx_modem      18825  0 
snd_intel8x0m          18970  0 
snd_ac97_codec        134826  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12730  1 snd_ac97_codec                                                                                                                                                  
parport_pc             36962  0                                                                                                                                                                 
ppdev                  17113  0                                                                                                                                                                 
dm_crypt               23199  0                                                                                                                                                                 
binfmt_misc            17540  1                                                                                                                                                                 
snd_hda_codec_conexant    62197  1                                                                                                                                                              
snd_hda_intel          33390  2                                                                                                                                                                 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel                                                                                                                            
snd_hwdep              13668  1 snd_hda_codec                                                                                                                                                   
snd_pcm                96714  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec                                                                     
arc4                   12529  2                                                                                                                                                                 
snd_seq_midi           13324  0                                                                                                                                                                 
snd_rawmidi            30547  1 snd_seq_midi                                                                                                                                                    
snd_seq_midi_event     14899  1 snd_seq_midi                                                                                                                                                    
joydev                 17693  0                                                                                                                                                                 
ath9k                 127538  0                                                                                                                                                                 
mac80211              462092  1 ath9k                                                                                                                                                           
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event                                                                                                                                 
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq                                                                                                                                     
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq                                                                                                                                
sp5100_tco             13791  0                                                                                                                                                                 
snd                    68266  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                                                                                              
i2c_piix4              13301  0                                                                                                                                                                 
ath9k_common           13839  1 ath9k
soundcore              12680  1 snd
ath9k_hw              312914  2 ath9k,ath9k_common
snd_page_alloc         18529  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199630  3 ath9k,mac80211,ath
edac_core              53746  0 
psmouse                73882  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
k10temp                13166  0 
shpchp                 37345  0 
sparse_keymap          13890  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon               1016211  2 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236290  4 radeon,ttm,drm_kms_helper
usbhid                 47198  0 
hid                    95463  1 usbhid
video                  19412  0 
i2c_algo_bit           13423  1 radeon
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci

```I tried using the drivers available through Jockey, but that messed up the various puzzle games that I play in so far as sometimes the screen would not refresh.

So, I purged these drivers according to the instructions on the ubuntu website, and still no effects. Anyone know anything that might help?

Thanks!

---

### Post by utnubuuser on 2011-12-28
not familiar at all with Plasma/KDE, but isn't there a "Desktop-Settings" somewhere that has a check-box for desktop-effects

---

### Post by MoreOrLess on 2011-12-28
Post your /var/log/Xorg.0.log

---

