---
title: "GEForce 960, NVidia drivers only gives 1080p resolution on Vizio E-Series 4k UHD TV"
date: 2016-08-11
forum: Hardware
---

### Post by dean.w.schulze on 2016-08-11
My Ubuntu 15 system with a GEForce 960 and NVidia drivers will only give 1080p resolution on a Vizio E-Series 4k UHD LED TV (currently available at Costco).  Maybe it's because it is a LED TV, and not a monitor.  If anyone has this combination working at UHD I'd appreciate any solutions.


Does anyone have a 4K UHD monitor (or TV) working at UHD resolution with a GEForce 960 on Ubuntu 15?  If so, which monitor.  I'm looking for a 39" or slightly larger monitor or 4k UDH TV that works with this configuration.

---

### Post by papibe on 2016-08-11
Hi  dean.w.schulze.

Take a look at [this]("https://ubuntuforums.org/showthread.php?t=2332258") thread. Please post the same results are asked on post #2.

Als you could you tell us the exact model of your TV/Monitor (a link even better), and if it has other inputs, like display/port or DVI?

Regards.

---

### Post by dean.w.schulze on 2016-08-12
The Vizio LED TV doesn't have a model number that I can see.  The NVidia X Server Settings app shows it as a VIZ E43u-D2.  It has 4 HDMI ports and a (old school) component input.  No display port or DVI.

```

lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2960]
	Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2960]
	Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)


lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
nvidia_drm             45056  1
nvidia_modeset        765952  5 nvidia_drm
nvidia              11247616  82 nvidia_modeset
intel_rapl             20480  0
snd_hda_intel          36864  5
intel_powerclamp       16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
kvm_intel             167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm                   516096  1 kvm_intel
aesni_intel           167936  0
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
intel_lpss_pci         16384  0
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
nouveau              1388544  0
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
ttm                    94208  1 nouveau
drm_kms_helper        131072  3 i915,nouveau,nvidia_drm
drm                   360448  7 ttm,i915,drm_kms_helper,nouveau,nvidia_drm
wmi                    20480  2 mxm_wmi,nouveau
video                  40960  2 i915,nouveau
pinctrl_intel          20480  1 pinctrl_sunrisepoint


xrandr --q1
 SZ:    Pixels          Physical       Refresh
*0   3840 x 1080   (1204mm x 342mm )  *50  
 1   1920 x 1080   ( 602mm x 342mm )   51   52   53   54   55   56   57  
 2   1680 x 1050   ( 526mm x 333mm )   58  
 3   1440 x 900    ( 451mm x 285mm )   59  
 4   1280 x 1024   ( 401mm x 325mm )   60  
 5   1280 x 800    ( 401mm x 254mm )   61  
 6   1280 x 720    ( 401mm x 228mm )   62   63   64  
 7   1024 x 768    ( 321mm x 243mm )   65   66  
 8    800 x 600    ( 250mm x 190mm )   67   68  
 9    720 x 576    ( 225mm x 182mm )   69  
 10   720 x 480    ( 225mm x 152mm )   70  
 11   640 x 480    ( 200mm x 152mm )   71   72  
 12  1366 x 768    ( 428mm x 243mm )   73  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis


xrandr --q12
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  60.00    59.94    50.00    50.00    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       59.94    59.93  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 953mm x 543mm
   1920x1080     60.00*+  59.94    29.97    23.97    60.00  
   1280x720      59.94  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  

xvidtune -show
"3840x1080"   148.50   3840 2008 2052 2200   1080 1084 1089 1125 +hsync +vsync








```

---

### Post by dean.w.schulze on 2016-08-12
I've asked on the NVidia forums as well:

[https://forums.geforce.com/default/topic/957055/geforce-drivers/gtx-960-linux-driver-only-offers-1080p-resolution-for-a-4k-uhd-monitor/](https://forums.geforce.com/default/topic/957055/geforce-drivers/gtx-960-linux-driver-only-offers-1080p-resolution-for-a-4k-uhd-monitor/)

---

### Post by papibe on 2016-08-13
Are you using a HDMI 2.0 cable? (read the section "Does every HDMI Cable support 4K Ultra HD?" [here]("https://turbofuture.com/computers/do-i-need-hdmi-cable-4k-hdmi-20-guide"))

Regards.

---

### Post by dean.w.schulze on 2016-08-13
I'm using a DP to HDMI cable.  The HDMI port on the GTX 960 doesn't work.  Both screens go blank when I try to use the HDMI port.  After rebooting I can get one screen to come up, but the login prompt never displays.  Apparently it is trying to display it on the other screen.

---

