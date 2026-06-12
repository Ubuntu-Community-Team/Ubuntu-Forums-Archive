---
title: "Resume fails from suspend/hibernate: Asus U50F"
date: 2010-10-14
forum: Hardware
---

### Post by Nullifi3d on 2010-10-14
Hi folks,

Yes, there are a lot of posts on this problem. Yes, I've been researching the problem for several weeks regarding this problem. I'm coming here because I've lost patience with the issue and cannot find any resolutions.

```
sudo s2ram -i
This machine can be identified by:
    sys_vendor   = "ASUSTeK Computer Inc.        "
    sys_product  = "U50F"
    sys_version  = "1.0       "
    bios_version = "U50F.202"

```

Suspend and hibernate seem to work correctly from what I can tell, but resume fails no matter what I do. I've tried following the S2RAM guide on debugging suspend issues, but nothing seems to work. If I boot with the following options:

```
vga=normal nomodeset init=/bin/bash
```

/sys and /proc are already mounted. Doing a ```
echo mem > /sys/power/state
``` puts the machine into a suspended/hibernated state, but I'm left with a display that is on, undimmed, and with a flashing cursor (only a single flashing cursor at upper left, no other characters displayed).

I also had the same issue in 10.04. I first upgraded to 10.10, then did a clean install of 10.10 - nothing changed. I also ran Fedora 13 on this machine, with 2.6.32 and 2.6.35, both of which had the same issue (if I recall correctly).

If anyone can help, or if you perhaps need more information on my system, feel free to reply/ask.

```

nullifi3d@nullifi3d-mobi:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
06:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

```

nullifi3d@nullifi3d-mobi:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  2 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11363  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_conexant    37356  1 
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
ath9k                 101730  0 
snd_seq_midi            5932  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314699  2 ath9k,ath9k_common
snd_rawmidi            22207  1 snd_seq_midi
ath                    10413  2 ath9k,ath9k_hw
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
mac80211              266657  2 ath9k,ath9k_common
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
jmb38x_ms               8667  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
memstick               10185  1 jmb38x_ms
snd                    64117  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_ips              13252  0 
asus_laptop            16668  0 
sparse_keymap           3837  1 asus_laptop
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
i915                  330249  8 
drm_kms_helper         32836  1 i915
drm                   206161  4 i915,drm_kms_helper
ahci                   21857  0 
i2c_algo_bit            6208  1 i915
libahci                26167  3 ahci
video                  22176  1 i915
output                  2527  1 video
sdhci_pci               7765  0 
jme                    33058  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  3 ath9k,asus_laptop,sdhci
mii                     5261  1 jme
intel_agp              32080  2 i915

```

---

### Post by pizzystrizzy on 2010-10-14
I have the exact same problem, and my similar efforts to solve the problem have also failed.

---

### Post by Nullifi3d on 2010-10-19
Bump.

---

