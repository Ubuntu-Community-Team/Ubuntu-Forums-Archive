---
title: "cant get wwan to work"
date: 2012-09-22
forum: Hardware
---

### Post by jseagle62 on 2012-09-22
I have a CR48 with the Gobi2000 qualcomm card in it.  I have spent the better part of 4 hours trying suggestions from other posters trying to get this card to work...  Can someone help me get this done?  

lsmod output:


jimbo@CR-48:~$ lsmod
Module                  Size  Used by
qcserial               12702  0 
usb_wwan               19711  1 qcserial
usbserial              37116  2 qcserial,usb_wwan
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
rfcomm                 38125  8 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath9k                 103633  0 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17827  2 
bnep                   17785  2 
i915                  451053  3 
l2cap                  48656  16 rfcomm,bnep
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
ipheth                 13238  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 ath9k
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
psmouse                73312  0 
drm_kms_helper         40971  1 i915
videodev               75143  1 uvcvideo
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
drm                   184164  4 i915,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
tpm_tis                13993  0 
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
tpm                    21251  1 tpm_tis
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
tpm_bios               13460  1 tpm
video                  19112  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci


lsusb output:

jimbo@CR-48:~$ lsusb
Bus 005 Device 002: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:1297 Apple, Inc. 
Bus 001 Device 004: ID 04f2:b205 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1410:a014 Novatel Wireless 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


If you need more information, let me know.

---

### Post by jseagle62 on 2012-09-24
Bump...

---

