---
title: "Upgrading Wif Card"
date: 2011-11-19
forum: Hardware
---

### Post by insert username here on 2011-11-19
I am looking to upgrade my WiFi only card to support WiFi and Bluetooth.

I stumbled across an Intel Centrino N 1030. I am having trouble figuring out if it is compatible with my current set up.

I rather not get a Bluetooth dongle and If this new card will not work, would you recommend a good WiFi/Bluetooth combo card

[My current WiFi card]("http://i622.photobucket.com/albums/tt305/insertusernamehere3029/WifiCard.jpg")

Replacement Card:
[Ebay - Intel Centrino N 1030]("http://www.ebay.com/itm/230700990660?ssPageName=STRK:MEWAX:IT&_trksid=p3984.m1423.l2649#ht_3092wt_1398")

$ lsb_release -a
> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


$ uname -a
> Linux NV78-PC 2.6.35-31-generic #62-Ubuntu SMP Tue Nov 8 14:20:11 UTC 2011 x86_64 GNU/Linux



$ lspci -nnk | grep -iA2 net
> 04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
	Kernel driver in use: iwlagn
--
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:020e]
	Kernel driver in use: tg3



$ iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"LadyBug"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C0:C1:C0:53:65:CE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



lsmod
> Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  3 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
pci_stub                1622  1 
vboxpci                15608  0 
vboxnetadp              5838  0 
vboxnetflt             16638  0 
joydev                 11395  0 
vboxdrv              1854941  4 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300109  1 
arc4                    1497  2 
iwlagn                215351  0 
i915                  335073  5 
drm_kms_helper         32836  1 i915
iwlcore               139688  1 iwlagn
drm                   206198  5 i915,drm_kms_helper
mac80211              269644  2 iwlagn,iwlcore
snd_hda_intel          26147  4 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
uvcvideo               62411  0 
snd_seq_midi            5932  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd_rawmidi            22207  1 snd_seq_midi
v4l2_compat_ioctl32    12614  1 videodev
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64277  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
cfg80211              167809  3 iwlagn,iwlcore,mac80211
i2c_algo_bit            6208  1 i915
intel_agp              32334  2 i915
video                  22176  1 i915
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22370  2 
libahci                26148  1 ahci
tg3                   135736  0 


dmesg | grep iwl
> [   20.159358] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   20.159362] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   20.159448] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.159457] iwlagn 0000:04:00.0: setting latency timer to 64
[   20.159510] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   20.180833] iwlagn 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   20.180852] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.180990] iwlagn 0000:04:00.0: irq 46 for MSI/MSI-X
[   20.184783] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   20.195135] phy0: Selected rate control algorithm 'iwl-agn-rs'








Thank you for your time and please let me know if you need more information


Edit: fixed typos and broken links

---

### Post by insert username here on 2011-11-21
bump

---

### Post by wolfen69 on 2011-11-21
[http://www.intel.com/support/wireless/sb/cs-006408.htm](http://www.intel.com/support/wireless/sb/cs-006408.htm)

---

### Post by insert username here on 2011-11-23
awesome. thank you

---

