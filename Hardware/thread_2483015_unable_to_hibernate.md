---
title: "unable to hibernate"
date: 2023-01-17
forum: Hardware
---

### Post by stephenbbb on 2023-01-17
pm-hibernate makes the screen black, but does not turn of the fan. please, help with some tweaks in pm-utils.
my issue is not the grub setup. the laptop hibernates easily under windows.

```

System:
  Kernel: 5.15.0-56-generic x86_64 bits: 64 compiler: gcc v: 11.3.0 Desktop: Xfce 4.16.0
    tk: Gtk 3.24.23 wm: xfwm dm: LightDM Distro: Linux Mint 21 Vanessa base: Ubuntu 22.04 jammy
Machine:
  Type: Laptop System: ASUSTeK product: VivoBook 15_ASUS Laptop X540BA v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: X540BA v: 1.0 serial: <superuser required> UEFI: American Megatrends
    v: X540BA.303 date: 07/04/2019
Battery:
  ID-1: BAT0 charge: 6.8 Wh (25.3%) condition: 26.9/33.2 Wh (81.2%) volts: 10.8 min: 10.8
    model: ASUSTeK ASUS Battery serial: N/A status: Charging
CPU:
  Info: dual core model: AMD A9-9425 RADEON R5 5 COMPUTE CORES 2C+3G bits: 64 type: MCP
    arch: Excavator rev: 0 cache: L1: 192 KiB L2: 2 MiB
  Speed (MHz): avg: 3094 min/max: 1400/3100 boost: enabled cores: 1: 3094 2: 3094
    bogomips: 12376
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: ASUSTeK driver: amdgpu v: kernel
    ports: active: eDP-1 empty: DP-1,HDMI-A-1 bus-ID: 00:01.0 chip-ID: 1002:98e4
  Device-2: Chicony USB2.0 VGA UVC WebCam type: USB driver: uvcvideo bus-ID: 1-1.3:4
    chip-ID: 04f2:b64a
  Display: x11 server: X.Org v: 1.21.1.3 compositor: xfwm v: 4.16.1 driver: X:
    loaded: amdgpu,ati unloaded: fbdev,modesetting,vesa gpu: amdgpu display-ID: :0.0 screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96
  Monitor-1: eDP res: 1366x768 dpi: 101 diag: 394mm (15.5")
  OpenGL: renderer: AMD STONEY (LLVM 13.0.1 DRM 3.42 5.15.0-56-generic) v: 4.5 Mesa 22.0.5
    direct render: Yes

Drives:
  Local Storage: total: 223.57 GiB used: 19.54 GiB (8.7%)
  ID-1: /dev/sda vendor: Kingston model: SA400S37240G size: 223.57 GiB speed: 6.0 Gb/s
    serial: <filter>
Partition:
  ID-1: / size: 56.07 GiB used: 8.09 GiB (14.4%) fs: ext4 dev: /dev/sda5
  ID-2: /boot/efi size: 96 MiB used: 30.3 MiB (31.6%) fs: vfat dev: /dev/sda1
  ID-3: /home size: 83.67 GiB used: 11.42 GiB (13.6%) fs: ext4 dev: /dev/sda7
Swap:
  ID-1: swap-1 type: partition size: 8.67 GiB used: 0 KiB (0.0%) priority: -2 dev: /dev/sda6
Info:
  Processes: 226 Uptime: 2m Memory: 7.22 GiB used: 1.36 GiB (18.9%) Init: systemd v: 249
  runlevel: 5 Compilers: gcc: 11.3.0 alt: 11 Client: Unknown python3.10 client inxi: 3.3.13

```

the log does not show any errors 
```

Tue 17 Jan 2023 06:04:35 PM EST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux stephen-VivoBook-15-ASUS-Laptop-X540BA 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 22 19:54:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usbhid                 65536  0
snd_seq_dummy          16384  0
rfcomm                 81920  16
cmac                   16384  3
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 32768  6 algif_hash,algif_skcipher
bnep                   28672  2
zfs                  3825664  6
zunicode              348160  1 zfs
zzstd                 491520  1 zfs
zlua                  163840  1 zfs
zavl                   20480  1 zfs
icp                   323584  1 zfs
zcommon               106496  2 zfs,icp
znvpair                98304  2 zfs,zcommon
spl                   118784  6 zfs,icp,zzstd,znvpair,zcommon,zavl
nls_iso8859_1          16384  1
snd_hda_codec_generic   102400  1
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     77824  1
edac_mce_amd           36864  0
snd_hda_intel          53248  6
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         163840  3 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel
kvm_amd               155648  0
ccp                   102400  1 kvm_amd
joydev                 32768  0
snd_hda_core          110592  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_hwdep              16384  1 snd_hda_codec
uvcvideo              106496  0
kvm                  1028096  1 kvm_amd
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_pcm               143360  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
videobuf2_v4l2         32768  1 uvcvideo
videobuf2_common       77824  4 videobuf2_vmalloc,videobuf2_v4l2,uvcvideo,videobuf2_memops
input_leds             16384  0
videodev              258048  3 videobuf2_v4l2,uvcvideo,videobuf2_common
hid_multitouch         32768  0
btusb                  61440  0
btrtl                  24576  1 btusb
mc                     65536  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_seq_midi           20480  0
asus_nb_wmi            28672  0
serio_raw              20480  0
btbcm                  24576  1 btusb
snd_seq_midi_event     16384  1 snd_seq_midi
wmi_bmof               16384  0
btintel                40960  1 btusb
rtl8821ce            2056192  0
bluetooth             704512  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
fam15h_power           16384  0
k10temp                16384  0
snd_rawmidi            49152  1 snd_seq_midi
ecdh_generic           16384  2 bluetooth
ecc                    36864  1 ecdh_generic
cfg80211              974848  1 rtl8821ce
snd_seq                77824  3 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                   106496  21 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
asus_wireless          20480  0
8250_dw                16384  0
mac_hid                16384  0
soundcore              16384  1 snd
sch_fq_codel           20480  5
msr                    16384  0
parport_pc             49152  0
ppdev                  24576  0
lp                     28672  0
ramoops                32768  0
parport                69632  3 parport_pc,lp,ppdev
reed_solomon           28672  1 ramoops
pstore_blk             16384  0
pstore_zone            32768  1 pstore_blk
efi_pstore             16384  0
ip_tables              32768  0
x_tables               53248  1 ip_tables
autofs4                49152  2
btrfs                1556480  0
blake2b_generic        20480  0
xor                    24576  1 btrfs
zstd_compress         229376  1 btrfs
raid6_pq              122880  1 btrfs
libcrc32c              16384  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
amdgpu               9859072  16
iommu_v2               24576  1 amdgpu
gpu_sched              45056  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                    86016  2 amdgpu,drm_ttm_helper
drm_kms_helper        311296  1 amdgpu
mfd_aaeon              16384  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            20480  1 drm_kms_helper
asus_wmi               45056  2 asus_nb_wmi,mfd_aaeon
sparse_keymap          16384  1 asus_wmi
crct10dif_pclmul       16384  1
sysimgblt              16384  1 drm_kms_helper
crc32_pclmul           16384  0
fb_sys_fops            16384  1 drm_kms_helper
ghash_clmulni_intel    16384  0
sdhci_pci              69632  0
hid_generic            16384  0
platform_profile       16384  1 asus_wmi
cec                    61440  1 drm_kms_helper
cqhci                  36864  1 sdhci_pci
xhci_pci               24576  0
rc_core                65536  1 cec
ahci                   45056  4
aesni_intel           376832  4
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel
drm                   622592  12 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
sdhci                  81920  1 sdhci_pci
i2c_piix4              32768  0
libahci                45056  1 ahci
xhci_pci_renesas       20480  1 xhci_pci
wmi                    32768  3 asus_wmi,wmi_bmof,mfd_aaeon
i2c_hid_acpi           16384  0
i2c_hid                36864  1 i2c_hid_acpi
video                  61440  1 asus_wmi
hid                   151552  4 i2c_hid,usbhid,hid_multitouch,hid_generic
               total        used        free      shared  buff/cache   available
Mem:         7571628     2156540     3363724       34636     2051364     5095724
Swap:        9091068           0     9091068
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/40inputattach hibernate hibernate:
/usr/lib/pm-utils/sleep.d/40inputattach hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlp1s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Tue 17 Jan 2023 06:04:35 PM EST: performing hibernate


```

Thanks

---

