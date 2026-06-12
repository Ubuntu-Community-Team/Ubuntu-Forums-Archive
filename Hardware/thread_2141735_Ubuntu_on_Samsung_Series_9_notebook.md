---
title: "Ubuntu on Samsung Series 9 notebook"
date: 2013-05-03
forum: Hardware
---

### Post by bach on 2013-05-03
I am running Ubuntu Linux version 12.10 (64 bit) on a Samsung Series 9 ultrabook. Everything works fine, with two exceptions, namely: 1) The cursors sometimes erratically jumps to a different position when I am typing. I am sure that I don't the touchpad and I've checked the "Disable while typing" option in the touchpad (and mouse) panel. 2) The computer does not suspend when I close the lid even though this is the behavior indicated in the power panel. Any tips? Thank you. 

P.S. The kernel I am running: Linux darwin2 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:03:38 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

P.P.S. cribari@darwin2:~$ lsmod
Module                  Size  Used by
msr                    12909  0 
ppp_deflate            12951  0 
zlib_deflate           26915  1 ppp_deflate
bsd_comp               12922  0 
ppp_async              17414  0 
crc_ccitt              12708  1 ppp_async
option                 30142  0 
usb_wwan               20099  1 option
usbserial              42356  2 option,usb_wwan
usblp                  18141  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
usb_storage            48839  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
arc4                   12530  2 
samsung_laptop         14533  0 
btusb                  22475  0 
snd_hda_intel          33492  3 
joydev                 17458  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
psmouse                95595  0 
lpc_ich                17062  0 
microcode              22804  0 
serio_raw              13216  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 46620  16 
bnep                   18141  2 
bluetooth             209249  22 btusb,rfcomm,bnep
snd_timer              29426  2 snd_pcm,snd_seq
iwlwifi               386799  0 
parport_pc             32689  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17074  0 
mac80211              540032  1 iwlwifi
wmi                    19071  0 
i915                  520615  3 
cfg80211              206797  2 iwlwifi,mac80211
drm_kms_helper         49113  1 i915
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   288721  4 i915,drm_kms_helper
mac_hid                13206  0 
i2c_algo_bit           13414  1 i915
mei                    40691  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
video                  19391  2 samsung_laptop,i915
binfmt_misc            17501  1 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
ahci                   25721  2 
libahci                31192  1 ahci
r8169                  61651  0 
cribari@darwin2:~/Downloads/temp$ cd
cribari@darwin2:~$ lsmod
Module                  Size  Used by
msr                    12909  0 
ppp_deflate            12951  0 
zlib_deflate           26915  1 ppp_deflate
bsd_comp               12922  0 
ppp_async              17414  0 
crc_ccitt              12708  1 ppp_async
option                 30142  0 
usb_wwan               20099  1 option
usbserial              42356  2 option,usb_wwan
usblp                  18141  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
usb_storage            48839  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
arc4                   12530  2 
samsung_laptop         14533  0 
btusb                  22475  0 
snd_hda_intel          33492  3 
joydev                 17458  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
psmouse                95595  0 
lpc_ich                17062  0 
microcode              22804  0 
serio_raw              13216  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 46620  16 
bnep                   18141  2 
bluetooth             209249  22 btusb,rfcomm,bnep
snd_timer              29426  2 snd_pcm,snd_seq
iwlwifi               386799  0 
parport_pc             32689  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17074  0 
mac80211              540032  1 iwlwifi
wmi                    19071  0 
i915                  520615  3 
cfg80211              206797  2 iwlwifi,mac80211
drm_kms_helper         49113  1 i915
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   288721  4 i915,drm_kms_helper
mac_hid                13206  0 
i2c_algo_bit           13414  1 i915
mei                    40691  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
video                  19391  2 samsung_laptop,i915
binfmt_misc            17501  1 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
ahci                   25721  2 
libahci                31192  1 ahci
r8169                  61651  0 
cribari@darwin2:~$

---

