---
title: "Audio mixer Rodecaster Pro work on Ubuntu 20.04 playing distorted sound"
date: 2021-05-03
forum: Hardware
---

### Post by otacke on 2021-05-03
I want to use a Rodecaster Pro mixer to run my audio. It runs fine on my laptop, but not on my desktop (both running Ubuntu 20.04 with kernel 5.8.18).


On my desktop, the input from microphones are working, but sound output is played very slow and distorted as if sampled down - interestingly media playback e.g. from YouTube is slowed down on my screen as well. Never seen something like that before :-)


**tl;dr**
Currently, the best hint I have and that I am investigating: The Rodecaster Pro seems be able to handle audio set to 24bit, 48kHz only. While the Linux kernel sets the 48kHz in some extra quirk handler for the Rodecaster Pro, I assume that I need to reconfigure ALSA in some way to meet the 24bit requirement (although I don't know why it's working on my laptop without any problems, just not on my desktop).


Current status: I have been trying to play a wav (encoded in 48000kHz in PCM 32 bit little endian format) sample via [FONT=courier new]aplay[/FONT] using


```
aplay -f S32_LE -c 2 -r 48000 -D hw:x ~/sample.wav

```

where x is the appropriate card number and the rest of the arguments meet the Rodecaster's specification. It's playing fine on the laptop, but distorted on the desktop. It is possible that on one of them, ALSA is doing or not doing some resampling (either breaking something on the desktop or fixing something on the laptop)? As far as I understand, this should not be the case since I am not using the plug plugin, correct? So, must there be something happening between ALSA and the Rodecaster, probably something USB related?


**Observations**


**dmesg -w**
I ran *dmesg -w* on both my machines when plugging in the Rodecaster, but everything that was loaded on the one machine was loaded on the other as well.


**sudo udevadm monitor**
*desktop*
```

KERNEL[1865.590942] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4 (usb)
KERNEL[1865.601419] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0 (usb)
KERNEL[1865.612569] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007 (hid)
KERNEL[1865.612799] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/usbmisc/hiddev3 (usbmisc)
KERNEL[1865.612974] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007/hidraw/hidraw6 (hidraw)
KERNEL[1865.613056] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007 (hid)
KERNEL[1865.613151] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0 (usb)
KERNEL[1865.616426] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1 (usb)
KERNEL[1865.677444] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5 (sound)
KERNEL[1865.677677] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/pcmC5D0p (sound)
KERNEL[1865.677912] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/pcmC5D0c (sound)
KERNEL[1865.678075] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/controlC5 (sound)
KERNEL[1865.678150] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1 (usb)
KERNEL[1865.678230] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.2 (usb)
KERNEL[1865.678271] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.2 (usb)
KERNEL[1865.678306] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.3 (usb)
KERNEL[1865.678342] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.3 (usb)
KERNEL[1865.678383] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4 (usb)
UDEV  [1865.689608] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4 (usb)
UDEV  [1865.693927] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0 (usb)
UDEV  [1865.695025] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.3 (usb)
UDEV  [1865.696323] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007 (hid)
UDEV  [1865.696398] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1 (usb)
UDEV  [1865.697069] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.2 (usb)
UDEV  [1865.697653] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.3 (usb)
UDEV  [1865.698513] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/usbmisc/hiddev3 (usbmisc)
UDEV  [1865.699314] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.2 (usb)
UDEV  [1865.699793] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5 (sound)
UDEV  [1865.699910] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007/hidraw/hidraw6 (hidraw)
KERNEL[1865.701496] change   /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5 (sound)
UDEV  [1865.701919] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0/0003:19F7:0011.0007 (hid)
UDEV  [1865.702558] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/pcmC5D0p (sound)
UDEV  [1865.703109] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/pcmC5D0c (sound)
UDEV  [1865.703403] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.0 (usb)
UDEV  [1865.707163] add      /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5/controlC5 (sound)
UDEV  [1865.708834] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1 (usb)
UDEV  [1865.712130] bind     /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4 (usb)
UDEV  [1865.714516] change   /devices/pci0000:00/0000:00:02.1/0000:16:00.0/usb1/1-4/1-4:1.1/sound/card5 (sound)

```


*laptop*
```

KERNEL[73.917616] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1 (usb)
KERNEL[73.918469] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[73.918672] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1 (usb)
KERNEL[73.918782] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2 (usb)
KERNEL[73.918889] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.3 (usb)
KERNEL[73.919019] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1 (usb)
UDEV  [73.935752] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1 (usb)
UDEV  [73.953007] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2 (usb)
KERNEL[73.956636] add      /module/snd_usbmidi_lib (module)
UDEV  [73.957630] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.3 (usb)
KERNEL[73.961972] add      /module/hid (module)
KERNEL[73.962835] add      /bus/hid (bus)
KERNEL[73.962873] add      /class/hidraw (class)
UDEV  [73.966103] add      /bus/hid (bus)
KERNEL[73.972181] add      /module/snd_usb_audio (module)
UDEV  [73.973275] add      /module/hid (module)
UDEV  [73.974278] add      /module/snd_usb_audio (module)
KERNEL[73.975143] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2 (usb)
KERNEL[73.975886] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.3 (usb)
KERNEL[73.975924] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2 (sound)
KERNEL[73.976038] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/pcmC2D0p (sound)
UDEV  [73.977321] add      /module/snd_usbmidi_lib (module)
KERNEL[73.977364] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/pcmC2D0c (sound)
UDEV  [73.977407] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1 (usb)
KERNEL[73.977435] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/controlC2 (sound)
KERNEL[73.977470] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1 (usb)
KERNEL[73.977489] add      /bus/usb/drivers/snd-usb-audio (drivers)
KERNEL[73.979239] add      /module/usbhid (module)
UDEV  [73.981525] add      /module/usbhid (module)
UDEV  [73.981982] add      /bus/usb/drivers/snd-usb-audio (drivers)
KERNEL[73.984631] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001 (hid)
KERNEL[73.984795] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[73.984915] add      /bus/usb/drivers/usbhid (drivers)
UDEV  [73.985188] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0 (usb)
UDEV  [73.987952] add      /class/hidraw (class)
UDEV  [73.989622] add      /bus/usb/drivers/usbhid (drivers)
UDEV  [73.998682] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1 (usb)
UDEV  [74.002632] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2 (sound)
UDEV  [74.007862] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2 (usb)
UDEV  [74.008550] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.3 (usb)
UDEV  [74.011974] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/pcmC2D0p (sound)
UDEV  [74.013611] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/pcmC2D0c (sound)
KERNEL[74.013656] change   /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2 (sound)
KERNEL[74.015404] add      /module/hid_generic (module)
KERNEL[74.015782] add      /class/usbmisc (class)
KERNEL[74.016175] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/usbmisc/hiddev0 (usbmisc)
KERNEL[74.016485] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001/hidraw/hidraw0 (hidraw)
KERNEL[74.016799] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001 (hid)
KERNEL[74.017129] add      /bus/hid/drivers/hid-generic (drivers)
UDEV  [74.017415] add      /module/hid_generic (module)
UDEV  [74.017632] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001 (hid)
UDEV  [74.019223] add      /bus/hid/drivers/hid-generic (drivers)
UDEV  [74.020516] add      /class/usbmisc (class)
UDEV  [74.023101] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0 (usb)
UDEV  [74.028094] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/usbmisc/hiddev0 (usbmisc)
UDEV  [74.030285] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2/controlC2 (sound)
UDEV  [74.035919] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1 (usb)
UDEV  [74.038564] add      /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001/hidraw/hidraw0 (hidraw)
UDEV  [74.041016] bind     /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:19F7:0011.0001 (hid)
UDEV  [74.045640] change   /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/sound/card2 (sound)

```


**lsmod**
*desktop*
```

Module                  Size  Used by
xt_conntrack           16384  2
xt_MASQUERADE          20480  2
nf_conntrack_netlink    49152  0
nfnetlink              20480  2 nf_conntrack_netlink
xfrm_user              36864  1
xfrm_algo              16384  1 xfrm_user
xt_addrtype            16384  2
iptable_filter         16384  1
iptable_nat            16384  1
nf_nat                 49152  2 iptable_nat,xt_MASQUERADE
nf_conntrack          147456  4 xt_conntrack,nf_nat,nf_conntrack_netlink,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
libcrc32c              16384  2 nf_conntrack,nf_nat
bpfilter               16384  0
br_netfilter           28672  0
bridge                212992  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
overlay               122880  0
nls_iso8859_1          16384  1
edac_mce_amd           32768  0
snd_hda_codec_ca0132   114688  1
snd_hda_codec_hdmi     61440  2
snd_usb_audio         286720  8
snd_hda_intel          53248  10
kvm                   729088  0
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         143360  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_ca0132
snd_hda_core           94208  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_ca0132
uvcvideo               98304  0
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
rapl                   20480  0
videobuf2_vmalloc      20480  1 uvcvideo
snd_seq_midi           20480  0
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
videobuf2_v4l2         28672  1 uvcvideo
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
videobuf2_common       57344  2 videobuf2_v4l2,uvcvideo
input_leds             16384  0
snd_pcm               118784  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core,snd_hda_codec_ca0132
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
videodev              245760  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mousedev               20480  0
joydev                 28672  0
snd_timer              40960  2 snd_seq,snd_pcm
mc                     57344  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
xpad                   40960  0
snd                    94208  48 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_ca0132,snd_rawmidi
ff_memless             20480  1 xpad
wmi_bmof               16384  0
blackmagic_io        1904640  1
k10temp                20480  0
efi_pstore             16384  0
ccp                   102400  0
soundcore              16384  1 snd
mac_hid                16384  0
nvidia_uvm           1011712  0
sch_fq_codel           20480  2
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  2 iptable_filter,iptable_nat
x_tables               45056  5 xt_conntrack,iptable_filter,xt_addrtype,ip_tables,xt_MASQUERADE
autofs4                45056  2
dm_crypt               53248  1
hid_generic            16384  0
usbhid                 57344  0
hid                   135168  2 usbhid,hid_generic
nvidia_drm             53248  8
nvidia_modeset       1183744  14 nvidia_drm
amdgpu               5853184  3
crct10dif_pclmul       16384  1
iommu_v2               20480  1 amdgpu
crc32_pclmul           16384  0
gpu_sched              36864  1 amdgpu
nvidia              19771392  634 nvidia_uvm,nvidia_modeset
ghash_clmulni_intel    16384  0
i2c_algo_bit           16384  1 amdgpu
ttm                   106496  1 amdgpu
aesni_intel           372736  2
drm_kms_helper        225280  2 amdgpu,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
crypto_simd            16384  1 aesni_intel
sysimgblt              16384  1 drm_kms_helper
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel
fb_sys_fops            16384  1 drm_kms_helper
glue_helper            16384  1 aesni_intel
cec                    53248  1 drm_kms_helper
rc_core                53248  1 cec
r8169                  94208  0
drm                   557056  17 gpu_sched,drm_kms_helper,amdgpu,nvidia_drm,ttm
realtek                24576  1
i2c_piix4              28672  0
ahci                   40960  3
xhci_pci               20480  0
libahci                36864  1 ahci
xhci_pci_renesas       20480  1 xhci_pci
wmi                    32768  1 wmi_bmof
video                  49152  0
backlight              24576  3 video,amdgpu,drm
gpio_amdpt             20480  0
gpio_generic           20480  1 gpio_amdpt

```


*laptop*
```

Module                  Size  Used by
hid_generic            16384  0
usbhid                 57344  0
snd_usb_audio         282624  2
hid                   131072  2 usbhid,hid_generic
snd_usbmidi_lib        36864  1 snd_usb_audio
rfcomm                 81920  4
ccm                    20480  6
cmac                   16384  3
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 28672  6 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
videodev              245760  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     57344  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
intel_rapl_common      28672  1 intel_rapl_msr
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
x86_pkg_temp_thermal    20480  0
iwldvm                241664  0
intel_powerclamp       20480  0
snd_hda_codec_hdmi     61440  1
mac80211              917504  1 iwldvm
snd_hda_intel          53248  4
coretemp               20480  0
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
libarc4                16384  1 mac80211
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
iwlwifi               364544  1 iwldvm
snd_pcm               118784  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
kvm_intel             282624  0
btusb                  57344  0
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
btrtl                  24576  1 btusb
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
btbcm                  16384  1 btusb
btintel                28672  1 btusb
joydev                 28672  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
kvm                   729088  1 kvm_intel
snd_timer              40960  2 snd_seq,snd_pcm
bluetooth             626688  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
at24                   24576  0
mei_me                 40960  0
rapl                   20480  0
cfg80211              782336  3 iwldvm,iwlwifi,mac80211
intel_cstate           20480  0
input_leds             16384  0
serio_raw              20480  0
ecdh_generic           16384  2 bluetooth
mei                   110592  1 mei_me
snd                    94208  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
ecc                    32768  1 ecdh_generic
soundcore              16384  1 snd
tpm_infineon           20480  0
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               45056  1 ip_tables
autofs4                45056  2
dm_crypt               49152  1
rtsx_pci_sdmmc         28672  0
i915                 2273280  17
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  10
crypto_simd            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
i2c_algo_bit           16384  1 i915
drm_kms_helper        225280  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               159744  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
cec                    53248  2 drm_kms_helper,i915
ahci                   40960  3
i2c_i801               32768  0
rc_core                53248  1 cec
libahci                36864  1 ahci
i2c_smbus              20480  1 i2c_i801
r8169                  94208  0
xhci_pci               20480  0
rtsx_pci               90112  1 rtsx_pci_sdmmc
drm                   561152  10 drm_kms_helper,i915
lpc_ich                24576  0
xhci_pci_renesas       20480  1 xhci_pci
realtek                24576  1
wmi                    32768  0
video                  49152  1 i915

```


**aplay --dump-hw-params -D hw:x -t raw /dev/zero**

Running
```

pulseaudio -k
aplay --dump-hw-params -D hw:x -t raw /dev/zero

```
where x is the respective card number yields the same for the desktop and the laptop:


```

Playing raw data '/dev/zero' : Unsigned 8 bit, Rate 8000 Hz, Mono
HW Params of device "hw:x":
--------------------
ACCESS:  MMAP_INTERLEAVED RW_INTERLEAVED
FORMAT:  S32_LE
SUBFORMAT:  STD
SAMPLE_BITS: 32
FRAME_BITS: 64
CHANNELS: 2
RATE: 48000
PERIOD_TIME: (166 1365334)
PERIOD_SIZE: [8 65536]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: (333 2730667)
BUFFER_SIZE: [16 131072]
BUFFER_BYTES: [128 1048576]
TICK_TIME: ALL
--------------------
aplay: set_params:1343: Sample format non available
Available formats:
- S32_LE

```

I have already found out that *aplay -f S32_LE -c 2 -r 48000 -D hw:x ~/sample.wav* needs to be used to run a sample ... Still distorted sound.


**More details**

[LIST]
[*]I have already tried to use different USB ports, 2.0 and 3.0, etc. Didn't make a difference.
[*]I have disabled other audio devices via *pavucontrol* - to no avail.
[*]I have disabled the motherboard's audio card and I have removed all other audio output interfaces physically - removed a Soundblaster and my graphics card that could output audio via HDMI. Didn't make a difference.
[*]I have booted a plain Ubuntu 21.04 from a pen drive (with not other audio hardware inside) - didn't work.
[*]I killed pulse audio (*pulseaudio -k*) and ran a wav sample using *aplay*. Sound is still distorted.
[*]The Rodecaster Pro registers as a USB HID device, but does not support the UAC2_CS_RANGE usb function call. That's why special handling was introduced to the Linux kernal ([https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/sound/usb/format.c?h=v5.8#n412](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/sound/usb/format.c?h=v5.8#n412)), but that's fine - well, listed in pulse audio at least.
[*]My Rodecaster Pro runs firmware 2.1.1, but that's should not be relevant, since it's working on my laptop.
[/LIST]

---

### Post by otacke on 2021-05-06
I have meanwhile filed a bug report at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1927255](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1927255).

---

### Post by jacobpfeifer on 2021-10-11
This sounds very similar to the issue I faced over [here]("https://forum.level1techs.com/t/rodecaster-pro-bad-audio-out/170601").  I fixed the issue by using a pcie usb card. It seems there's some kind  of bad interaction between an amd chipset usb port and the rodecaster  pro so using a pcie card bypasses the amd usb chipset.

---

