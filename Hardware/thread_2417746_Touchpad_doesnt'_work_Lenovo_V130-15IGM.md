---
title: "Touchpad doesnt' work Lenovo V130-15IGM"
date: 2019-04-26
forum: Hardware
---

### Post by ascvfx2 on 2019-04-26
Hi! I have latest Ubuntu 18.04 LTS on this laptop and everything is fine, except touchpad - it does not work at all. I'm complete noob on Linux systems and i have no idea what to do. Any help?

---

### Post by cruzer001 on 2019-04-26
Sorry to say, but sounds like this bug report.

[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/1789252](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/1789252)

[https://forum.manjaro.org/t/lenovo-ideapad-330-touchpad-not-working/50764/12](https://forum.manjaro.org/t/lenovo-ideapad-330-touchpad-not-working/50764/12)

---

### Post by mörgæs on 2019-04-27
18.04 is not latest, it's two generations old. 

For hardware as new as your Lenovo I would first of all test how it works in a live boot of 19.04.

---

### Post by ascvfx2 on 2019-04-27
Yes, i have tried 19.04, but nothing changes, unfortunately.

---

### Post by jeremy31 on 2019-04-27
Please post results from terminal for ```
cat /proc/cmdline; dmesg | grep -i elan
```

---

### Post by ascvfx2 on 2019-04-27
> **jeremy31 said:**
> Please post results from terminal for ```
cat /proc/cmdline; dmesg | grep -i elan
```

Here it is:
```

~$ cat /proc/cmdline; dmesg | grep -i elan
BOOT_IMAGE=/boot/vmlinuz-4.18.0-15-generic root=UUID=3t21e947-3hf8-t32g-209v-c4207r2602xa ro quiet splash vt.handoff=1
[   13.902099] i2c_hid i2c-ELAN061A:00: i2c-ELAN061A:00 supply vdd not found, using dummy regulator
```

---

### Post by jeremy31 on 2019-04-27
For a test we can do ```
sudo sed -i 's/ELAN060C/ELAN061A/' /lib/modules/$(uname -r)/kernel/drivers/input/mouse/elan_i2c.ko
sudo depmod -a
```
Reboot

---

### Post by ascvfx2 on 2019-04-27
> **jeremy31 said:**
> For a test we can do ```
sudo sed -i 's/ELAN060C/ELAN061A/' /lib/modules/$(uname -r)/kernel/drivers/input/mouse/elan_i2c.ko
sudo depmod -a
```
Reboot

Thx for the tip, but it had no effect though.

---

### Post by jeremy31 on 2019-04-27
Post results for ```
lsmod; modinfo elan_i2c; dmesg | grep -i elan
```

---

### Post by ascvfx2 on 2019-04-27
> **jeremy31 said:**
> Post results for ```
lsmod; modinfo elan_i2c; dmesg | grep -i elan
```

```
lsmod; modinfo elan_i2c; dmesg | grep -i elan
Module                  Size  Used by
ccm                    20480  6
rfcomm                 77824  4
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
snd_hda_codec_conexant    24576  1
intel_telemetry_pltdrv    20480  0
intel_punit_ipc        16384  1 intel_telemetry_pltdrv
intel_telemetry_core    16384  1 intel_telemetry_pltdrv
intel_pmc_ipc          20480  1 intel_telemetry_pltdrv
x86_pkg_temp_thermal    16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
snd_soc_skl           102400  0
snd_soc_skl_ipc        61440  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_acpi           16384  1 snd_soc_skl
snd_soc_core          229376  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           81920  7 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_skl
uvcvideo               94208  0
kvm_intel             208896  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_hwdep              20480  1 snd_hda_codec
videobuf2_memops       16384  1 videobuf2_vmalloc
arc4                   16384  2
spi_pxa2xx_platform    24576  0
snd_pcm                98304  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
kvm                   626688  1 kvm_intel
snd_seq_midi           16384  0
8250_dw                16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
videobuf2_v4l2         24576  1 uvcvideo
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_rawmidi            32768  1 snd_seq_midi
iwlmvm                376832  0
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
mac80211              802816  1 iwlmvm
joydev                 24576  0
aesni_intel           200704  4
aes_x86_64             20480  1 aesni_intel
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  40960  2 videodev,uvcvideo
iwlwifi               299008  1 iwlmvm
processor_thermal_device    16384  0
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
input_leds             16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
serio_raw              16384  0
input_polldev          16384  0
snd_timer              32768  2 snd_seq,snd_pcm
wmi_bmof               16384  0
ideapad_laptop         32768  0
mei_me                 40960  0
idma64                 20480  6
btusb                  45056  0
btrtl                  16384  1 btusb
virt_dma               16384  1 idma64
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
btbcm                  16384  1 btusb
btintel                20480  1 btusb
intel_lpss_pci         20480  0
cfg80211              667648  3 iwlmvm,iwlwifi,mac80211
bluetooth             552960  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
intel_lpss             16384  1 intel_lpss_pci
ecdh_generic           24576  1 bluetooth
intel_soc_dts_iosf     16384  1 processor_thermal_device
sparse_keymap          16384  1 ideapad_laptop
soundcore              16384  1 snd
mei                    98304  1 mei_me
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
i915                 1740800  11
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
r8169                  86016  0
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
drm                   458752  5 drm_kms_helper,i915
i2c_hid                20480  0
ahci                   40960  2
wmi                    24576  2 wmi_bmof,ideapad_laptop
hid                   122880  3 i2c_hid,usbhid,hid_generic
libahci                32768  1 ahci
pinctrl_geminilake     24576  0
video                  45056  2 ideapad_laptop,i915
pinctrl_intel          20480  1 pinctrl_geminilake
filename:       /lib/modules/4.18.0-15-generic/kernel/drivers/input/mouse/elan_i2c.ko
license:        GPL
description:    Elan I2C/SMBus Touchpad driver
author:         Duson Lin <dusonlin@emc.com.tw>
srcversion:     B11147E9E357B56EA8683B4
alias:          i2c:elan_i2c
alias:          acpi*:ELAN1000:*
alias:          acpi*:ELAN0622:*
alias:          acpi*:ELAN061D:*
alias:          acpi*:ELAN061C:*
alias:          acpi*:ELAN0618:*
alias:          acpi*:ELAN0612:*
alias:          acpi*:ELAN0611:*
alias:          acpi*:ELAN061A:*
alias:          acpi*:ELAN060B:*
alias:          acpi*:ELAN0609:*
alias:          acpi*:ELAN0608:*
alias:          acpi*:ELAN0605:*
alias:          acpi*:ELAN0602:*
alias:          acpi*:ELAN0600:*
alias:          acpi*:ELAN0100:*
alias:          acpi*:ELAN0000:*
depends:        
retpoline:      Y
intree:         Y
name:           elan_i2c
vermagic:       4.18.0-15-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
[   14.459657] i2c_hid i2c-ELAN061A:00: i2c-ELAN061A:00 supply vdd not found, using dummy regulator

```

---

### Post by jeremy31 on 2019-04-27
Check ```
mokutil --sb-state
```
If it says Secure Boot is enabled, reboot and disable Secure Boot
Then in terminal do
```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/mouse-4.18.git
sudo dkms add ./mouse-4.18
sudo dkms install mouse/1.0
```
Reboot

---

### Post by ascvfx2 on 2019-04-27
I have this:
```
mokutil -sb-state
~$ mokutil -sb-state
mokutil: invalid option -- 'b'
mokutil: invalid option -- '-'
Usage:
  mokutil OPTIONS [ARGS...]
```
i don't have Secure Boot in BIOS settings, if it's necessary

and this:
```
sudo apt install git build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build-essential' has no installation candidate
E: Unable to locate package dkms

```

---

### Post by jeremy31 on 2019-04-27
Should have been ```
mokutil --sb-state
```
Also try ```
sudo apt update
```
before running the other commands

---

### Post by ascvfx2 on 2019-04-27
Much obliged, it works now! Right-click is recognizes as left-click, but i already found solution via GNOME Tweaks, now it works properly. Thanks again!

---

