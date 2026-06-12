---
title: "Sony Vaio VPC-Z13 Fn brightness keys and slider not working"
date: 2016-08-08
forum: Hardware
---

### Post by Paloseco on 2016-08-08
My notebook is a Sony Vaio VPCZ13M9, which has two graphic cards (hybrid graphics). I've set the VGA switching mode in the BIOS to STATIC, so I choose in the hardware button which graphics I want to use when powering on the computer. Currently I'm on the nVidia GeForce GT 330m
My ubuntu version is 16.04.1 LTS.

To control the screen brightness there's the Fn+F5 to decrease or Fn+F6 to increase it. When I press the combination, the slider appears moving in the corner of the screen, however the screen brightness doesn't change. The same happens if I change the brightness from System Preferences.

Outputs with [COLOR="#0000CD"]**VGA Switching Policy set to STATIC**[/COLOR] on the BIOS and using [COLOR="#FF0000"]**nVidia Geforce GT 330m**[/COLOR] gpu with the physical switch (position SPEED):

```
root@ubuntu:~# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=efa3614c-4cb5-42ba-8eb3-e1c88afde1a6 ro --verbose nosplash debug

```
```
root@ubuntu:~# lspci -k | grep -A2 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT216M [GeForce GT 330M] (rev a2)
	Subsystem: Sony Corporation GT216M [GeForce GT 330M]
	Kernel driver in use: nouveau

```
```
root@ubuntu:~# for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
8
3
3
/sys/class/backlight/nv_backlight
100
70
70

```
```
root@ubuntu:~# lsmod
Module                  Size  Used by
arc4                   16384  2
iwldvm                233472  0
snd_hda_codec_hdmi     53248  4
intel_powerclamp       16384  0
uvcvideo               90112  0
mac80211              737280  1 iwldvm
coretemp               16384  0
kvm_intel             172032  0
kvm                   536576  1 kvm_intel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
irqbypass              16384  1 kvm
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
joydev                 20480  0
snd_hda_intel          36864  5
iwlwifi               200704  1 iwldvm
input_leds             16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
shpchp                 36864  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                24576  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 36864  0
soundcore              16384  1 snd
mei                    98304  1 mei_me
mac_hid                16384  0
sony_laptop            61440  0
tpm_infineon           20480  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
uas                    24576  0
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
usb_storage            69632  4 uas
nouveau              1495040  6
i2c_algo_bit           16384  1 nouveau
ttm                    94208  1 nouveau
drm_kms_helper        147456  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
e1000e                237568  0
sysimgblt              16384  1 drm_kms_helper
mxm_wmi                16384  1 nouveau
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  0
sdhci_pci              28672  0
ptp                    20480  1 e1000e
intel_ips              20480  0
sdhci                  45056  1 sdhci_pci
libahci                32768  1 ahci
drm                   360448  9 ttm,drm_kms_helper,nouveau
psmouse               126976  0
pps_core               20480  1 ptp
fjes                   28672  0
video                  40960  2 sony_laptop,nouveau
wmi                    20480  2 mxm_wmi,nouveau

```
```
root@ubuntu:~# pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/22706087/
```

---

### Post by Paloseco on 2016-08-08
Ok, tried [Brightness Controller]("http://lordamit.github.io/Brightness/") and it works witht he nVidia 330m, but I need to launch the application to access the slider. I would like to make it work directly with the Fn keys.

```
sudo add-apt-repository ppa:apandada1/brightness-controller
sudo apt-get update
sudo apt-get install brightness-controller
```

---

### Post by Paloseco on 2016-08-08
More information. Surprisingly with the integrated graphics it works. There are two minor issues that I've found tough:

1) The brightness increase and decrease steps are way too much. From maximum brightness, going a single step down (Fn+F5) there is too much difference in brightness. Indeed it needs refinement
2) The maximum brightness that the Fn+F6 can set it not the maximum available:
```
# cat /sys/class/backlight/intel_backlight/actual_brightness 
3484
# cat /sys/class/backlight/intel_backlight/max_brightness 
4882

```
It's possible, however, to set the brightness to the maximum even if the ubuntu interface does not allow it:
```
# cat /sys/class/backlight/intel_backlight/max_brightness > /sys/class/backlight/intel_backlight/brightness
```

---

### Post by Paloseco on 2016-08-08
Outputs with [COLOR="#0000CD"]**VGA Switching Policy set to STATIC**[/COLOR] on the BIOS and using [COLOR="#FF0000"]**Integrated graphics**[/COLOR] gpu with the physical switch (position STAMINA):

```
root@ubuntu:~# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=efa3614c-4cb5-42ba-8eb3-e1c88afde1a6 ro --verbose nosplash debug

```
```
root@ubuntu:~# lspci -k | grep -A2 VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Sony Corporation Core Processor Integrated Graphics Controller
	Kernel driver in use: i915

```
```
root@ubuntu:~# for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/intel_backlight
4882
3484
3484

```
```
root@ubuntu:~# lsmod
Module                  Size  Used by
arc4                   16384  2
iwldvm                233472  0
uvcvideo               90112  0
mac80211              737280  1 iwldvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
intel_powerclamp       16384  0
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
coretemp               16384  0
kvm_intel             172032  0
kvm                   536576  1 kvm_intel
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
iwlwifi               200704  1 iwldvm
input_leds             16384  0
joydev                 20480  0
snd_hda_intel          36864  3
irqbypass              16384  1 kvm
serio_raw              16384  0
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
snd_hda_core           73728  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
shpchp                 36864  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 36864  0
lpc_ich                24576  0
mei                    98304  1 mei_me
soundcore              16384  1 snd
sony_laptop            61440  0
mac_hid                16384  0
tpm_infineon           20480  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
i915                 1208320  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
uas                    24576  0
mxm_wmi                16384  0
e1000e                237568  0
ahci                   36864  0
sdhci_pci              28672  0
psmouse               126976  0
usb_storage            69632  4 uas
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
intel_ips              20480  0
sdhci                  45056  1 sdhci_pci
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
drm                   360448  5 i915,drm_kms_helper
fjes                   28672  0
wmi                    20480  1 mxm_wmi
video                  40960  2 i915,sony_laptop

```
```
root@ubuntu:~# pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/22729319/
```

---

