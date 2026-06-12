---
title: "USB Audio JBL Quantum 810 problems"
date: 2022-06-24
forum: Hardware
---

### Post by bgre0000 on 2022-06-24
Hi,

I have trouble getting the USB dongle for the Quantum 810 headset to work.

After I plug in the dongle and start `pavucontrol`, pavucontrol needs unusually long to connect to the pulseaudio demon. When finally done, it does not show the devices. (The headset acts as two sound devices, one for chat and one for playback).

I tried searching for this specific error as well as with more generic terms but found only a few very old threads with solutions that are not applicable to today's systems.

I do not know any further. Any suggestion is welcome!

`aplay -l` detects the card
```

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC256 Analog [ALC256 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Wireless [JBL Quantum810 Wireless], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Wireless [JBL Quantum810 Wireless], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

but speaker-test can not use it:
```
$ speaker-test -D plughw:CARD=Wireless,DEV=0

speaker-test 1.2.6

Playback device is plughw:CARD=Wireless,DEV=0
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy

$ speaker-test -D plughw:CARD=Wireless,DEV=1

speaker-test 1.2.6

Playback device is plughw:CARD=Wireless,DEV=1
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 96000
Period size range from 48 to 48000
Using max buffer size 96000
Periods = 4
Unable to set hw params for playback: Broken pipe
Setting of hwparams failed: Broken pipe


```

`dmesg -wT` gives some first insights
```

[Fri Jun 24 17:11:43 2022] usb 1-2: new full-speed USB device number 8 using xhci_hcd
[Fri Jun 24 17:11:43 2022] usb 1-2: New USB device found, idVendor=0e8d, idProduct=0003, bcdDevice= 1.00
[Fri Jun 24 17:11:43 2022] usb 1-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Fri Jun 24 17:11:43 2022] cdc_acm 1-2:1.0: ttyACM0: USB ACM device
[Fri Jun 24 17:11:43 2022] usb 1-2: USB disconnect, device number 8
[Fri Jun 24 17:11:44 2022] usb 1-2: new high-speed USB device number 9 using xhci_hcd
[Fri Jun 24 17:11:44 2022] usb 1-2: New USB device found, idVendor=0ecb, idProduct=2069, bcdDevice= 1.00
[Fri Jun 24 17:11:44 2022] usb 1-2: New USB device strings: Mfr=4, Product=5, SerialNumber=0
[Fri Jun 24 17:11:44 2022] usb 1-2: Product: JBL Quantum810 Wireless
[Fri Jun 24 17:11:44 2022] usb 1-2: Manufacturer: Harman International Inc
[Fri Jun 24 17:11:44 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
[Fri Jun 24 17:11:44 2022] usb 1-2: 3:1: cannot set freq 48000 to ep 0x2
[Fri Jun 24 17:11:44 2022] usb 1-2: Found post-registration device assignment: 0ecb2069:02
[Fri Jun 24 17:11:44 2022] hid-generic 0003:0ECB:2069.0006: hiddev1,hidraw4: USB HID v1.10 Device [Harman International Inc JBL Quantum810 Wireless] on usb-0000:03:00.3-2/input5
[Fri Jun 24 17:11:44 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
[Fri Jun 24 17:11:44 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
[Fri Jun 24 17:11:45 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
[Fri Jun 24 17:11:45 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
[Fri Jun 24 17:11:45 2022] usb 1-2: 1:1: cannot set freq 48000 to ep 0x1
... this message is repeated about 15 times per seconds
[Fri Jun 24 17:14:26 2022] usb 1-2: USB disconnect, device number 9
[Fri Jun 24 17:14:26 2022] usb 1-2: 1:1: usb_set_interface failed (-19)
[Fri Jun 24 17:14:26 2022] usb 1-2: 1:0: usb_set_interface failed (-19)

```

lsusb:
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1358:c123 Realtek Bluetooth Radio
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 13d3:56f9 IMC Networks ov9734_azurewave_camera
Bus 001 Device 004: ID 27c6:5110 Shenzhen Goodix Technology Co.,Ltd. Goodix Fingerprint Device 
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 009: ID 0ecb:2069 Harman International Inc JBL Quantum810 Wireless
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy

```

lsmod
```
Module                  Size  Used by
snd_usb_audio         344064  1
snd_usbmidi_lib        45056  1 snd_usb_audio
snd_rawmidi            49152  1 snd_usbmidi_lib
snd_seq_device         16384  1 snd_rawmidi
option                 61440  0
usb_wwan               24576  1 option
usbserial              57344  2 usb_wwan,option
cdc_acm                40960  0
ccm                    20480  9
rfcomm                 81920  16
xt_conntrack           16384  1
nft_chain_nat          16384  3
xt_MASQUERADE          20480  1
nf_nat                 49152  2 nft_chain_nat,xt_MASQUERADE
nf_conntrack_netlink    49152  0
nf_conntrack          167936  4 xt_conntrack,nf_nat,nf_conntrack_netlink,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
xfrm_user              40960  1
xfrm_algo              16384  1 xfrm_user
nft_counter            16384  15
xt_addrtype            16384  2
nft_compat             20480  4
nf_tables             241664  43 nft_compat,nft_counter,nft_chain_nat
nfnetlink              20480  4 nft_compat,nf_conntrack_netlink,nf_tables
br_netfilter           28672  0
bridge                299008  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
cmac                   16384  3
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 32768  6 algif_hash,algif_skcipher
overlay               147456  0
bnep                   28672  2
intel_rapl_msr         20480  0
snd_ctl_led            24576  0
intel_rapl_common      36864  1 intel_rapl_msr
binfmt_misc            24576  1
snd_hda_codec_realtek   151552  1
snd_hda_codec_generic   102400  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     73728  1
edac_mce_amd           36864  0
kvm_amd               151552  0
rtw88_8822ce           16384  0
nls_iso8859_1          16384  1
kvm                  1003520  1 kvm_amd
rtw88_8822c           503808  1 rtw88_8822ce
snd_hda_intel          53248  5
snd_intel_dspcfg       28672  1 snd_hda_intel
rapl                   20480  0
uvcvideo              106496  0
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
rtw88_pci              32768  1 rtw88_8822ce
btusb                  61440  0
snd_hda_codec         155648  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
rtw88_core            253952  2 rtw88_pci,rtw88_8822c
huawei_wmi             20480  0
btrtl                  24576  1 btusb
ledtrig_audio          16384  3 snd_ctl_led,snd_hda_codec_generic,huawei_wmi
videobuf2_vmalloc      20480  1 uvcvideo
snd_hda_core          110592  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
btbcm                  24576  1 btusb
sparse_keymap          16384  1 huawei_wmi
wmi_bmof               16384  0
videobuf2_memops       20480  1 videobuf2_vmalloc
btintel                40960  1 btusb
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
efi_pstore             16384  0
serio_raw              20480  0
hid_multitouch         28672  0
mac80211             1228800  2 rtw88_pci,rtw88_core
videobuf2_v4l2         32768  1 uvcvideo
snd_pci_acp5x          20480  0
videobuf2_common       77824  4 videobuf2_vmalloc,videobuf2_v4l2,uvcvideo,videobuf2_memops
bluetooth             688128  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_pcm               139264  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
videodev              249856  3 videobuf2_v4l2,uvcvideo,videobuf2_common
snd_rn_pci_acp3x       20480  0
st_accel_i2c           20480  0
snd_timer              40960  1 snd_pcm
st_sensors_i2c         16384  1 st_accel_i2c
ecdh_generic           16384  2 bluetooth
mc                     65536  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
input_leds             16384  0
snd_pci_acp3x          20480  0
joydev                 32768  0
k10temp                16384  0
ecc                    36864  1 ecdh_generic
cfg80211              958464  2 rtw88_core,mac80211
st_accel               28672  1 st_accel_i2c
snd                   102400  24 snd_ctl_led,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
st_sensors             28672  3 st_accel_i2c,st_accel
industrialio_triggered_buffer    16384  1 st_accel
kfifo_buf              16384  1 industrialio_triggered_buffer
soundcore              16384  2 snd_ctl_led,snd
libarc4                16384  1 mac80211
industrialio           90112  5 industrialio_triggered_buffer,st_sensors,kfifo_buf,st_accel_i2c,st_accel
ccp                   102400  7 kvm_amd
mac_hid                16384  0
sch_fq_codel           20480  1
dm_multipath           40960  0
scsi_dh_rdac           20480  0
scsi_dh_emc            16384  0
scsi_dh_alua           20480  0
ipmi_devintf           20480  0
ipmi_msghandler       122880  1 ipmi_devintf
msr                    16384  0
parport_pc             49152  0
ppdev                  24576  0
lp                     28672  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               53248  5 xt_conntrack,nft_compat,xt_addrtype,ip_tables,xt_MASQUERADE
autofs4                49152  2
btrfs                1527808  0
blake2b_generic        20480  0
zstd_compress         229376  1 btrfs
dm_crypt               53248  1
raid10                 69632  0
raid456               163840  0
async_raid6_recov      24576  1 raid456
async_memcpy           20480  2 raid456,async_raid6_recov
async_pq               24576  2 raid456,async_raid6_recov
async_xor              20480  3 async_pq,raid456,async_raid6_recov
async_tx               20480  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              122880  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  5 nf_conntrack,nf_nat,btrfs,nf_tables,raid456
raid1                  49152  0
raid0                  24576  0
multipath              20480  0
linear                 20480  0
usbhid                 65536  0
amdgpu               9723904  23
iommu_v2               24576  1 amdgpu
gpu_sched              45056  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                    86016  2 amdgpu,drm_ttm_helper
drm_kms_helper        307200  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            20480  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
cec                    61440  1 drm_kms_helper
hid_generic            16384  0
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           376832  12
crypto_simd            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
nvme                   45056  3
rc_core                65536  1 cec
i2c_hid_acpi           16384  0
xhci_pci               24576  0
i2c_hid                32768  1 i2c_hid_acpi
drm                   606208  17 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
nvme_core             126976  4 nvme
i2c_piix4              28672  0
xhci_pci_renesas       20480  1 xhci_pci
wmi                    32768  2 huawei_wmi,wmi_bmof
video                  53248  0
hid                   147456  4 i2c_hid,usbhid,hid_multitouch,hid_generic

```

---

### Post by #&amp;thj^% on 2022-06-24
Have you tried with just Bluetooth?
Something to look over: [https://atish3604.medium.com/solved-bluetooth-headset-mic-not-working-detected-in-ubuntu-20-04-86a5236444d0](https://atish3604.medium.com/solved-bluetooth-headset-mic-not-working-detected-in-ubuntu-20-04-86a5236444d0)
It still works for 22.04 as well.
I'm afraid just using the Dongle is hopeless ATM.

---

### Post by bgre0000 on 2022-06-24
Thanks.
After some work (including the switch to pipewire) I got it to work with bluetooth. 

But, as expected, the audio quality over BT with a handsfree profile is unsatisfactory. 

I still hope that there will be a solution with the dongle. (Because is specifically bought this headset to avoid BT)

---

### Post by wawangholanda on 2023-01-23
> **bgre0000 said:**
> Thanks.
After some work (including the switch to pipewire) I got it to work with bluetooth. 

But, as expected, the audio quality over BT with a handsfree profile is unsatisfactory. 

I still hope that there will be a solution with the dongle. (Because is specifically bought this headset to avoid BT)

I use KDE plasma WayLand on fedora 37,  sound menu show all optional output sound from JBL quantum 810. But when i use fedora with gnome, it's just bluetooth only.
I haven't tried ubuntu with kde (kubuntu), but ubuntu with gnome only showed bluetooth only when i tested on ubuntu version 18.04, 20.04 & 22.04.

---

