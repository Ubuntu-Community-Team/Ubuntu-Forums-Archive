---
title: "Issues with 13.10 and Display Link"
date: 2014-02-21
forum: Hardware
---

### Post by smitht on 2014-02-21
I've been trying for days to get a USB display link monitor up and running and it is not working. I read that after 13.04 the drivers were supposed to be built in to the kernel, however, I get nothing. Of note, the USB hub on the monitor is working as I can plug a USB drive into it and it comes up. But I get no video.

```
Linux ubuntu-box 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
[  593.580800] usb 4-3: new SuperSpeed USB device number 2 using xhci_hcd
[  593.597443] usb 4-3: New USB device found, idVendor=17e9, idProduct=430f
[  593.597447] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  593.597450] usb 4-3: Product: Kensington USB3.0 Video Adapter
[  593.597453] usb 4-3: Manufacturer: DisplayLink
[  593.597455] usb 4-3: SerialNumber: 10009938
```

```
box:~$ lsmod
Module                  Size  Used by
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_usb_audio         149162  0 
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_usbmidi_lib        25070  1 snd_usb_audio
nls_utf8               12557  0 
hfsplus               102763  0 
usb_storage            62062  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
joydev                 17377  0 
glue_helper            13990  1 aesni_intel
hid_generic            12548  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
dcdbas                 14847  0 
arc4                   12608  2 
snd_hda_intel          48171  3 
ath9k                 155779  0 
snd_hda_codec         188738  1 snd_hda_intel
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102033  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
mei_me                 18421  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
i915                  661261  3 
mac80211              597268  1 ath9k
psmouse                97655  0 
cfg80211              480503  3 ath,ath9k,mac80211
drm_kms_helper         52710  1 i915
drm                   297056  4 i915,drm_kms_helper
mei                    77782  1 mei_me
snd                    69141  17 snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13413  0 
soundcore              12680  1 snd
microcode              23576  0 
lpc_ich                21080  0 
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
video                  19318  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  2 
r8169                  67581  0 
libahci                31928  1 ahci
mii                    13934  1 r8169
```

---

### Post by Mark Phelps on 2014-02-21
Sorry, but the news is not encouraging:  [https://wiki.archlinux.org/index.php/DisplayLink]("https://wiki.archlinux.org/index.php/DisplayLink")

---

