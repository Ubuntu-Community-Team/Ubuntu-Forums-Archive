---
title: "Bluetooth adapter not detected anywhere"
date: 2019-03-04
forum: Hardware
---

### Post by jk1999 on 2019-03-04
Hi,
I have a Fujitsu Lifebook P8010 (old, I know). Recently I installed Ubuntu 18.10 on it and it won't detect built-in Bluetooth adapter. It's not disabled in BIOS and the wireless switch is set to on.
Here is some additional info:
```

$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
14:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

$ sudo lsusb
Bus 002 Device 003: ID 0ac8:3343 Z-Star Microelectronics Corp. Sirius USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ sudo lsmod
Module                  Size  Used by
acpi_call              16384  0
ccm                    20480  6
uvcvideo               98304  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  40960  2 videodev,uvcvideo
coretemp               16384  0
kvm_intel             208896  0
joydev                 20480  0
kvm                   622592  1 kvm_intel
irqbypass              16384  1 kvm
arc4                   16384  2
input_leds             16384  0
serio_raw              16384  0
iwl4965               114688  0
pcmcia                 57344  0
iwlegacy               98304  1 iwl4965
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
mac80211              794624  2 iwl4965,iwlegacy
snd_hda_intel          40960  3
yenta_socket           49152  0
snd_hda_codec         126976  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_realtek
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_hda_core           81920  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
cfg80211              663552  3 iwl4965,iwlegacy,mac80211
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  16 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
fujitsu_laptop         20480  0
sparse_keymap          16384  1 fujitsu_laptop
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
crypto_simd            16384  0
cryptd                 24576  1 crypto_simd
glue_helper            16384  0
aes_x86_64             20480  6
algif_skcipher         16384  0
af_alg                 24576  1 algif_skcipher
dm_crypt               40960  1
gpio_ich               16384  0
i915                 1740800  18
firewire_ohci          40960  0
psmouse               151552  0
ahci                   40960  2
sdhci_pci              36864  0
libahci                32768  1 ahci
i2c_algo_bit           16384  1 i915
firewire_core          65536  1 firewire_ohci
lpc_ich                24576  0
crc_itu_t              16384  1 firewire_core
drm_kms_helper        172032  1 i915
cqhci                  24576  1 sdhci_pci
sdhci                  53248  1 sdhci_pci
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   458752  7 drm_kms_helper,i915
sky2                   61440  0
video                  45056  2 fujitsu_laptop,i915

$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

$ dmesg | grep Blue
[  912.184829] Bluetooth: Core ver 2.22
[  912.184885] Bluetooth: HCI device and connection manager initialized
[  912.184894] Bluetooth: HCI socket layer initialized
[  912.184899] Bluetooth: L2CAP socket layer initialized
[  912.184913] Bluetooth: SCO socket layer initialized

$ hcitool dev
Devices:





```
Thank you in advance

---

