---
title: "dell 6000 dock, GTX 1650 card, impossible to add a 3rd screen, no possibility to add"
date: 2021-01-26
forum: Hardware
---

### Post by gregory-fr-44 on 2021-01-26
I have my laptop screen + 1 Acer screen (connected to my D6000) which works very well, I would like to add two more screens (identical to the 1st acer) but they are not detected by ubuntu?
what should I do?

My config : 
```

Pc : Dell XPS 15
Ubuntu : 20.10
Dock : Dell D6000
graphic Card : NVIDIA Corporation TU117M [GeForce GTX 1650 Mobile / Max-Q]

```


xandr :


```

DP-1-2 disconnected (normal left inverted right x axis y axis)
DP-1-3 disconnected (normal left inverted right x axis y axis)

```

```

lspci -vnn | grep -A12 '\''[030[02]\]' | grep -Ei "vga|3d|display|kernel"
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 630 (Mobile) [8086:3e9b] (prog-if 00 [VGA controller])
    Kernel driver in use: i915
    Kernel modules: i915
01:00.0 3D controller [0302]: NVIDIA Corporation TU117M [GeForce GTX 1650 Mobile / Max-Q] [10de:1f91] (rev a1)
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```

```

> uname -a
Linux anubis 5.8.0-38-generic #43-Ubuntu SMP Tue Jan 12 12:42:13 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```


```

> xrandr
Screen 0: minimum 8 x 8, current 4480 x 1440, maximum 32767 x 32767
eDP-1-1 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   3840x2160     60.00 +  59.98    59.97  
   3200x1800     59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95* 
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1-1 connected primary 1920x1080+2560+166 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       66.67    59.94  
   720x400       70.08  
DP-1-2 disconnected (normal left inverted right x axis y axis)
DP-1-3 disconnected (normal left inverted right x axis y axis)


```

```

> dpkg -l | grep -v ^ii
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom                                        Version                             Architecture Description
+++-==========================================-===================================-============-===============================================================================================================================================================================================================================================
rc  linux-image-5.4.0-54-generic               5.4.0-54.60                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-29-generic               5.8.0-29.31                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-31-generic               5.8.0-31.33                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-33-generic               5.8.0-33.36                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-34-generic               5.8.0-34.37                         amd64        Signed kernel image generic
rc  linux-modules-5.4.0-54-generic             5.4.0-54.60                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-29-generic             5.8.0-29.31                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-31-generic             5.8.0-31.33                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-33-generic             5.8.0-33.36                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-34-generic             5.8.0-34.37                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-54-generic       5.4.0-54.60                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-29-generic       5.8.0-29.31                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-31-generic       5.8.0-31.33                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-33-generic       5.8.0-33.36                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-34-generic       5.8.0-34.37                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP


```
```

> ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001F91sv00001028sd00000905bc03sc02i00
vendor   : NVIDIA Corporation
model    : TU117M [GeForce GTX 1650 Mobile / Max-Q]
driver   : nvidia-driver-460 - distro non-free recommended
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-450 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
```

> dpkg -l | grep nvidia
ii  libnvidia-cfg1-450:amd64                   450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-450                       450.102.04-0ubuntu0.20.10.1         all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-450:amd64                450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA libcompute package
ii  libnvidia-compute-450:i386                 450.102.04-0ubuntu0.20.10.1         i386         NVIDIA libcompute package
ii  libnvidia-decode-450:amd64                 450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-450:i386                  450.102.04-0ubuntu0.20.10.1         i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-450:amd64                 450.102.04-0ubuntu0.20.10.1         amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-450:i386                  450.102.04-0ubuntu0.20.10.1         i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-450:amd64                  450.102.04-0ubuntu0.20.10.1         amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-450:amd64                   450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-450:i386                    450.102.04-0ubuntu0.20.10.1         i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-450:amd64                     450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-450:i386                      450.102.04-0ubuntu0.20.10.1         i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-450:amd64                   450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-450:i386                    450.102.04-0ubuntu0.20.10.1         i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-450                   450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA compute utilities
ii  nvidia-dkms-450                            450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA DKMS package
ii  nvidia-driver-450                          450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-450                   450.102.04-0ubuntu0.20.10.1         amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-450                   450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.15                              all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            440.82-0ubuntu1                     amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-450                           450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18build1                          all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-450              450.102.04-0ubuntu0.20.10.1         amd64        NVIDIA binary Xorg driver

```
```

> lsmod | sort
ac97_bus               16384  1 snd_soc_core
acpi_pad              184320  0
acpi_thermal_rel       16384  1 int3400_thermal
aesni_intel           372736  8
af_alg                 28672  6 algif_hash,algif_skcipher
ahci                   40960  0
algif_hash             16384  1
algif_skcipher         16384  1
aufs                  262144  0
autofs4                45056  2
bluetooth             602112  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
bnep                   24576  2
bridge                200704  1 br_netfilter
br_netfilter           28672  0
btbcm                  16384  1 btusb
btintel                28672  1 btusb
btrtl                  24576  1 btusb
btusb                  57344  0
ccm                    20480  6
cdc_acm                40960  0
cdc_mbim               20480  0
cdc_ncm                45056  1 cdc_mbim
cdc_wdm                28672  1 cdc_mbim
cec                    53248  2 drm_kms_helper,i915
cfg80211              782336  3 iwlmvm,iwlwifi,mac80211
cmac                   16384  3
coretemp               20480  0
crc32_pclmul           16384  0
crct10dif_pclmul       16384  1
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel
crypto_simd            16384  1 aesni_intel
dcdbas                 20480  1 dell_smbios
dell_laptop            28672  0
dell_smbios            28672  2 dell_wmi,dell_laptop
dell_smm_hwmon         24576  0
dell_smo8800           20480  0
dell_wmi               20480  0
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
drm                   565248  13 vmwgfx,drm_kms_helper,nvidia_drm,i915,ttm
drm_kms_helper        225280  3 vmwgfx,nvidia_drm,i915
ecc                    32768  1 ecdh_generic
ecdh_generic           16384  2 bluetooth
ee1004                 20480  0
efi_pstore             16384  0
exfat                  77824  1
fb_sys_fops            16384  1 drm_kms_helper
ghash_clmulni_intel    16384  0
glue_helper            16384  1 aesni_intel
hid                   135168  4 i2c_hid,usbhid,hid_multitouch,hid_generic
hid_generic            16384  0
hid_multitouch         28672  0
i2c_algo_bit           16384  1 i915
i2c_hid                28672  0
i2c_i801               32768  0
i2c_smbus              20480  1 i2c_i801
i915                 2269184  4
idma64                 20480  0
input_leds             16384  0
int3400_thermal        20480  0
int3403_thermal        20480  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
intel_cstate           20480  0
intel_hid              20480  0
intel_lpss             16384  1 intel_lpss_pci
intel_lpss_pci         20480  0
intel_pch_thermal      16384  0
intel_powerclamp       20480  0
intel_rapl_common      28672  2 intel_rapl_msr,processor_thermal_device
intel_rapl_msr         20480  0
intel_soc_dts_iosf     20480  1 processor_thermal_device
intel_wmi_thunderbolt    20480  0
ip_tables              32768  0
iwlmvm                405504  0
iwlwifi               364544  1 iwlmvm
joydev                 28672  0
kvm                   724992  1 kvm_intel
kvm_intel             282624  0
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_sof,dell_laptop
libahci                36864  1 ahci
libarc4                16384  1 mac80211
libcrc32c              16384  2 nf_conntrack,nf_nat
llc                    16384  2 bridge,stp
lp                     20480  0
mac80211              917504  1 iwlmvm
mac_hid                16384  0
mc                     57344  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
mei                   110592  3 mei_hdcp,mei_me
mei_hdcp               24576  0
mei_me                 40960  1
mii                    16384  1 usbnet
Module                  Size  Used by
mxm_wmi                16384  0
nf_conntrack          147456  5 xt_conntrack,nf_nat,xt_nat,nf_conntrack_netlink,xt_MASQUERADE
nf_conntrack_netlink    49152  0
nf_defrag_ipv4         16384  1 nf_conntrack
nf_defrag_ipv6         24576  1 nf_conntrack
nf_nat                 49152  3 xt_nat,nft_chain_nat,xt_MASQUERADE
nfnetlink              16384  4 nft_compat,nf_conntrack_netlink,nf_tables
nf_tables             196608  159 nft_compat,nft_counter,nft_chain_nat
nft_chain_nat          16384  8
nft_compat             20480  21
nft_counter            16384  40
nls_iso8859_1          16384  1
nvidia              19746816  477 nvidia_uvm,nvidia_modeset
nvidia_drm             49152  8
nvidia_modeset       1183744  6 nvidia_drm
nvidia_uvm           1024000  0
nvme                   45056  2
nvme_core             110592  4 nvme
overlay               126976  1
parport                65536  3 parport_pc,lp,ppdev
parport_pc             45056  0
pinctrl_cannonlake     36864  0
pinctrl_intel          28672  1 pinctrl_cannonlake
ppdev                  24576  0
processor_thermal_device    24576  0
psmouse               159744  0
rapl                   20480  0
rc_cec                 16384  0
rc_core                53248  3 rc_cec,cec
rfcomm                 81920  4
rtsx_pci               90112  1 rtsx_pci_sdmmc
rtsx_pci_sdmmc         28672  0
sch_fq_codel           20480  2
serio_raw              20480  0
snd                    94208  33 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
snd_compress           28672  1 snd_soc_core
snd_hda_codec         143360  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   131072  1
snd_hda_core           94208  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_ext_core       32768  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_intel          53248  3
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_intel_dspcfg       24576  3 snd_hda_intel,snd_sof_pci,snd_sof_intel_hda_common
snd_pcm               118784  10 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_soc_acpi           16384  3 snd_soc_acpi_intel_match,snd_sof_intel_hda_common,snd_sof_intel_byt
snd_soc_acpi_intel_match    45056  2 snd_sof_pci,snd_sof_intel_hda_common
snd_soc_core          278528  3 snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_sof               122880  4 snd_sof_pci,snd_sof_intel_hda_common,snd_sof_intel_byt,snd_sof_intel_ipc
snd_sof_intel_byt      20480  1 snd_sof_pci
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_intel_hda_common    77824  1 snd_sof_pci
snd_sof_intel_ipc      20480  1 snd_sof_intel_byt
snd_sof_pci            24576  0
snd_sof_xtensa_dsp     16384  2 snd_sof_intel_hda_common,snd_sof_intel_byt
snd_timer              40960  2 snd_seq,snd_pcm
snd_usb_audio         286720  6
snd_usbmidi_lib        36864  1 snd_usb_audio
soundcore              16384  1 snd
sparse_keymap          16384  2 intel_hid,dell_wmi
stp                    16384  1 bridge
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
thunderbolt           208896  0
ttm                   102400  1 vmwgfx
typec                  53248  2 typec_displayport,typec_ucsi
typec_displayport      16384  1
typec_ucsi             32768  1 ucsi_acpi
uas                    28672  1
ucsi_acpi              16384  0
usbhid                 57344  0
usbnet                 49152  2 cdc_mbim,cdc_ncm
usb_storage            73728  1 uas
uvcvideo               98304  0
veth                   28672  0
video                  49152  3 dell_wmi,dell_laptop,i915
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_vmalloc      20480  1 uvcvideo
videodev              245760  3 videobuf2_v4l2,uvcvideo,videobuf2_common
virt_dma               20480  1 idma64
vmwgfx                323584  0
vmw_vmci               77824  1 vmw_vsock_vmci_transport
vmw_vsock_vmci_transport    32768  0
vsock                  45056  1 vmw_vsock_vmci_transport
wmi                    32768  6 intel_wmi_thunderbolt,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor,mxm_wmi
wmi_bmof               16384  0
x86_pkg_temp_thermal    20480  0
xfrm_algo              16384  1 xfrm_user
xfrm_user              36864  1
xhci_pci               20480  0
xhci_pci_renesas       20480  1 xhci_pci
x_tables               45056  7 xt_conntrack,nft_compat,xt_tcpudp,xt_addrtype,xt_nat,ip_tables,xt_MASQUERADE
xt_addrtype            16384  2
xt_conntrack           16384  3
xt_MASQUERADE          20480  4
xt_nat                 16384  5
xt_tcpudp              20480  7

```

---

