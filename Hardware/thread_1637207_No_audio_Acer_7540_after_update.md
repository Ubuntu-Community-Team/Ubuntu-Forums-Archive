---
title: "No audio Acer 7540 after update"
date: 2010-12-04
forum: Hardware
---

### Post by jamezelle on 2010-12-04
Ok I've been running 10.04 ultimate edition 2.7

which is a modded lucid build

no problems with audio until the latest update-manager update. Really didnt check if pulseaudio or alsa were updated, and I did the update about 2 days ago and didn't run any apps to notice no sound.

Ill list some debug info

```


jamezelle@jamezelle-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


#############################################################

jamezelle@jamezelle-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0000000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfdec000 irq 19

#############################################################

jamezelle@jamezelle-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
kvm_amd                36942  0 
kvm                   285887  1 kvm_amd
dm_crypt               13043  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279040  1 
joydev                 11072  0 
snd_hda_intel          25773  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_dummy           1782  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
arc4                    1473  2 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71251  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
uvcvideo               62595  0 
soundcore               8052  1 snd
videodev               40518  1 uvcvideo
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ath9k                 329117  0 
v4l1_compat            15495  2 uvcvideo,videodev
mac80211              238896  1 ath9k
edac_core              45423  0 
ath                     9723  1 ath9k
i2c_piix4               9639  0 
serio_raw               4918  0 
shpchp                 33711  0 
cfg80211              148725  3 ath9k,mac80211,ath
lp                      9336  0 
parport                37160  2 ppdev,lp
acer_wmi               15829  0 
v4l2_compat_ioctl32    11764  1 videodev
edac_mce_amd            9278  0 
led_class               3764  2 ath9k,acer_wmi
dm_raid45              75532  0 
xor                     4685  1 dm_raid45
usbhid                 41084  0 
hid                    83472  1 usbhid
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
radeon                740890  2 
ttm                    60847  1 radeon
usb_storage            49961  1 
drm_kms_helper         30742  1 radeon
video                  20623  0 
output                  2503  1 video
ahci                   37870  3 
drm                   198948  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
tg3                   122382  0 
ramzswap                7857  1 
xvmalloc                5054  1 ramzswap
lzo_decompress          2533  1 ramzswap
lzo_compress            2325  1 ramzswap

###########################################################

jamezelle@jamezelle-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

can't think of anymore debug info that would be needed please let me know. thanks

PS: of course, no my speakers are not muted.

---

