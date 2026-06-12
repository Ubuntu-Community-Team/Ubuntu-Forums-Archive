---
title: "Touchpad (SynPS/2 Synaptics TouchPad) recognized but not working in Lenovo Thinkpad"
date: 2018-09-12
forum: Hardware
---

### Post by poojasaxena on 2018-09-12
Hello,
yesterday I installed Ubuntu 16.04 LTS on Lenovo Thinkpad Carbon-6th. Since then, my touchpad is not working, though it is recognized. the external mouse works absolutely fine.
Here is the information on my hardware:
1. xinput
```
pooja@X1-Carbon-6:~$ xinput&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=13    [slave  keyboard (3)]

```

2. xinput --list-props 12
```
pooja@X1-Carbon-6:~$ xinput --list-props 12Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (266):    1
    Device Accel Constant Deceleration (267):    2.500000
    Device Accel Adaptive Deceleration (268):    1.000000
    Device Accel Velocity Scaling (269):    12.500000
    Synaptics Edges (292):    1574, 5370, 1350, 4502
    Synaptics Finger (293):    40, 40, 0
    Synaptics Tap Time (294):    180
    Synaptics Tap Move (295):    252
    Synaptics Tap Durations (296):    180, 180, 100
    Synaptics ClickPad (297):    1
    Synaptics Middle Button Timeout (298):    0
    Synaptics Two-Finger Pressure (299):    282
    Synaptics Two-Finger Width (300):    7
    Synaptics Scrolling Distance (301):    114, 114
    Synaptics Edge Scrolling (302):    0, 0, 0
    Synaptics Two-Finger Scrolling (303):    1, 1
    Synaptics Move Speed (304):    1.000000, 1.750000, 0.034874, 0.000000
    Synaptics Off (305):    2
    Synaptics Locked Drags (306):    0
    Synaptics Locked Drags Timeout (307):    5000
    Synaptics Tap Action (308):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (309):    1, 3, 0
    Synaptics Circular Scrolling (310):    0
    Synaptics Circular Scrolling Distance (311):    0.100000
    Synaptics Circular Scrolling Trigger (312):    0
    Synaptics Circular Pad (313):    0
    Synaptics Palm Detection (314):    0
    Synaptics Palm Dimensions (315):    10, 200
    Synaptics Coasting Speed (316):    20.000000, 50.000000
    Synaptics Pressure Motion (317):    30, 160
    Synaptics Pressure Motion Factor (318):    1.000000, 1.000000
    Synaptics Resolution Detect (319):    1
    Synaptics Grab Event Device (320):    0
    Synaptics Gestures (321):    1
    Synaptics Capabilities (322):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (323):    1, 1
    Synaptics Area (324):    0, 0, 0, 0
    Synaptics Soft Button Areas (325):    3472, 0, 4098, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (326):    28, 28
    Device Product ID (261):    2, 7
    Device Node (262):    "/dev/input/event5"

```

3. lsmod
```
pooja@X1-Carbon-6:~$ lsmod
Module                  Size  Used by
vboxdrv               471040  0
msr                    16384  0
rfcomm                 77824  0
bnep                   20480  2
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
btusb                  45056  0
videobuf2_memops       16384  1 videobuf2_vmalloc
btrtl                  16384  1 btusb
videobuf2_v4l2         24576  1 uvcvideo
btbcm                  16384  1 btusb
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
btintel                16384  1 btusb
snd_hda_codec_hdmi     49152  1
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
bluetooth             557056  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
media                  40960  2 uvcvideo,videodev
ecdh_generic           24576  1 bluetooth
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
arc4                   16384  2
nls_iso8859_1          16384  1
snd_soc_skl            90112  0
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_acpi           16384  1 snd_soc_skl
snd_soc_core          241664  1 snd_soc_skl
intel_rapl             20480  0
snd_compress           20480  1 snd_soc_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
iwlmvm                364544  0
mac80211              778240  1 iwlmvm
aesni_intel           188416  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
idma64                 20480  0
snd_hda_intel          40960  3
snd_seq_midi           16384  0
virt_dma               16384  1 idma64
iwlwifi               282624  1 iwlmvm
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_rawmidi            32768  1 snd_seq_midi
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
snd_hwdep              20480  1 snd_hda_codec
mei_me                 40960  0
input_leds             16384  0
joydev                 24576  0
thinkpad_acpi          94208  1
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
intel_wmi_thunderbolt    16384  0
wmi_bmof               16384  0
ucsi_acpi              16384  0
intel_lpss_pci         20480  0
processor_thermal_device    16384  0
typec_ucsi             28672  1 ucsi_acpi
serio_raw              16384  0
nvram                  16384  1 thinkpad_acpi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
mei                    90112  1 mei_me
intel_lpss             16384  1 intel_lpss_pci
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
shpchp                 36864  0
typec                  24576  1 typec_ucsi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  20 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,thinkpad_acpi,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
int3403_thermal        16384  0
soundcore              16384  1 snd
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
mac_hid                16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad              180224  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  1 uas
i915                 1630208  62
i2c_algo_bit           16384  1 i915
e1000e                249856  0
psmouse               147456  0
drm_kms_helper        172032  1 i915
ptp                    20480  1 e1000e
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
pps_core               20480  1 ptp
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme                   32768  0
thunderbolt           118784  0
nvme_core              61440  5 nvme
drm                   401408  7 i915,drm_kms_helper
wmi                    24576  2 wmi_bmof,intel_wmi_thunderbolt
video                  45056  2 thinkpad_acpi,i915
pinctrl_sunrisepoint    28672  0

```


4. grep -i touchpad /var/log/Xorg.0.log
```
pooja@X1-Carbon-6:~$ grep -i touchpad /var/log/Xorg.0.log[     5.873] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[     5.873] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     5.873] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[     5.873] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     5.873] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     5.873] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     5.873] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     5.952] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1266 - 5678 (res 0)
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1094 - 4758 (res 0)
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     5.952] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     5.952] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.020] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[     6.020] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     6.020] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     6.020] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     6.020] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     6.020] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     6.020] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     6.020] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     6.020] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.020] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     6.020] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
pooja@X1-Carbon-6:~$ 

```

There is one additional remark, the typing works fine with the keyboard. I meant the cursor remain stable. However, when I try these commands on the terminal,
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

the touchpad start to move around good, however scrolling does not work. And the worse one is that the writing text is a pain, because my cursor move left, right all randomly while typing. So I am not really keen to try these commands and anyways scrolling does not work. 

It is difficult for me to concentrate on my work without fixing this problem, if you have any ideas, what could go wrong, I would really appreciate that. 
Also, how could I change the value of this parameter (Synaptics Edge Scrolling) in 
```
xinput set-prop 12 302 1 1 1 
```
permanently?

Many thanks,
Pooja

---

