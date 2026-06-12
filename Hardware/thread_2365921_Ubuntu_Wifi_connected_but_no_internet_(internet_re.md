---
title: "Ubuntu Wifi connected but no internet (internet remains for short time)"
date: 2017-07-12
forum: Hardware
---

### Post by aahlaad.software on 2017-07-12
The basic problem is: **My laptop connects to a Wifi, but the internet works only for 30-60 seconds and then goes off**.

This same wifi works with many other system including my old Dell Inspiron laptop. Also my new Dell Vostro (Ubuntu 17.04) also works with many other Wifi networks, but this. I have referred few threads here and followed some of them:


[LIST]
[*][https://ubuntuforums.org/showthread.php?t=1985079](https://ubuntuforums.org/showthread.php?t=1985079)
[*][https://ubuntuforums.org/showthread.php?t=2352333](https://ubuntuforums.org/showthread.php?t=2352333)
[*][https://ubuntuforums.org/showthread.php?t=2343968](https://ubuntuforums.org/showthread.php?t=2343968)
[*][https://ubuntuforums.org/showthread.php?t=2192496](https://ubuntuforums.org/showthread.php?t=2192496)
[/LIST]

Here is an output from one of the thread on my terminal with the not-working wifi.

```
milind@Dell:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
Linux Dell 4.10.0-24-generic #28-Ubuntu SMP Wed Jun 14 08:14:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
milind@Dell:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Dell QCA9377 802.11ac Wireless Network Adapter [1028:1810]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci, wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0791]
    Kernel driver in use: r8169
    Kernel modules: r8169
milind@Dell:~$ iwconfig
enp3s0    no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"AAHLAAD_Production"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 8C:0C:90:7A:CE:58   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:21   Missed beacon:0


milind@Dell:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
milind@Dell:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  2
ccm                    20480  2
arc4                   16384  2
cmac                   16384  1
bnep                   20480  2
hid_rmi                24576  0
snd_hda_codec_hdmi     49152  1
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
dell_wmi               16384  0
dell_laptop            20480  0
dell_smm_hwmon         16384  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
rtsx_usb_ms            20480  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
memstick               16384  1 rtsx_usb_ms
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
wl                   6447104  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
dell_led               16384  1
dell_smbios            16384  3 dell_wmi,dell_led,dell_laptop
dcdbas                 16384  1 dell_smbios
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           167936  6
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
binfmt_misc            20480  1
snd_soc_skl            65536  0
snd_soc_skl_ipc        49152  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          36864  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ath10k_pci             45056  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ath10k_core           344064  1 ath10k_pci
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0
input_leds             16384  0
ath                    28672  1 ath10k_core
serio_raw              16384  0
snd_timer              32768  2 snd_seq,snd_pcm
mac80211              782336  1 ath10k_core
snd                    77824  19 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
soundcore              16384  1 snd
cfg80211              602112  4 wl,mac80211,ath,ath10k_core
shpchp                 36864  0
idma64                 20480  0
virt_dma               16384  1 idma64
btusb                  45056  0
mei_me                 40960  0
btrtl                  16384  1 btusb
mei                   102400  1 mei_me
intel_pch_thermal      16384  0
intel_lpss_pci         16384  0
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
int3403_thermal        16384  0
bluetooth             557056  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
int3402_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
mac_hid                16384  0
intel_lpss_acpi        16384  0
tpm_crb                16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           69632  2 acpi_als,kfifo_buf
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad              180224  0
intel_hid              16384  0
sparse_keymap          16384  2 dell_wmi,intel_hid
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
rtsx_usb_sdmmc         28672  0
usbhid                 53248  0
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
amdgpu               1564672  0
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
radeon               1507328  1
i915                 1449984  96
ttm                    98304  2 amdgpu,radeon
psmouse               139264  0
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        151552  3 amdgpu,radeon,i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
r8169                  81920  0
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  1
mii                    16384  1 r8169
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   352256  10 amdgpu,radeon,i915,ttm,drm_kms_helper
wmi                    16384  2 dell_wmi,dell_led
i2c_hid                20480  0
hid                   114688  4 i2c_hid,hid_generic,usbhid,hid_rmi
pinctrl_sunrisepoint    28672  0
video                  40960  3 dell_wmi,dell_laptop,i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   73728  0
milind@Dell:~$ 



```

---

