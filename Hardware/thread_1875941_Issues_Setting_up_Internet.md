---
title: "Issues Setting up Internet"
date: 2011-11-05
forum: Hardware
---

### Post by Kirby859 on 2011-11-05
Hey, I have a Sony VAIO VPCEL22FX laptop running Ubuntu 11.10 64-bit, and I'm having issues setting up my internet adapter. (edit: lolderp now I know my internet adapter) Windows' internet works fine. I'd be glad if someone helped me with this.

(sorry if this is the wrong forum, I just registered)

Oh yes, and lspci and lsmod outputs.
lsmod:
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
sp5100_tco             13791  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
binfmt_misc            17540  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 127538  0 
psmouse                73882  0 
mac80211              310872  1 ath9k
snd_rawmidi            30547  1 snd_seq_midi
serio_raw              13166  0 
i2c_piix4              13301  0 
k10temp                13166  0 
ath9k_common           13839  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
cfg80211              199587  3 ath9k,mac80211,ath
rts_pstor             445246  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon               1015995  3 
wmi                    19256  1 acer_wmi
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
video                  19412  0 
soundcore              12680  1 snd
i2c_algo_bit           13423  1 radeon
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
kirby859@kirby859-VPCEL22FX:~$ 
```and lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
kirby859@kirby859-VPCEL22FX:~$ 
```

---

