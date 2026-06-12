---
title: "Keyboard Backlight VAIO SVS13"
date: 2013-04-27
forum: Hardware
---

### Post by sochin on 2013-04-27
Hi, 

I've installed 12.10 on a new Vaio SVS13 A290X.

I would like to disable the keyboard backlight, viz:

[http://www.sony-mea.com/support/faq/400592](http://www.sony-mea.com/support/faq/400592)

but haven't found how to achieve this in 12.10.

Thanks.

---

### Post by Toz on 2013-04-27
Does this file exist in your system:
```
/sys/devices/platform/sony-laptop/kbd_backlight
```

If so, what is its value:
```
cat /sys/devices/platform/sony-laptop/kbd_backlight
```

If its not 0, try echoing 0 into it to see if it turns off the keyboard backlight:
```
echo 0 | sudo tee /sys/devices/platform/sony-laptop/kbd_backlight
```

---

### Post by sochin on 2013-04-27
> **Toz said:**
> Does this file exist in your system:
```
/sys/devices/platform/sony-laptop/kbd_backlight
```


No, that file doesn't exist:
sony-laptop> ls /sys/devices/platform/sony-laptop/
battery_care_health   driver    power      thermal_control   touchpad
battery_care_limiter  modalias  subsystem  thermal_profiles  uevent

---

### Post by Toz on 2013-04-27
How about in /sys/class/leds:
```
ls /sys/class/leds
```
...anything there about keyboard backlight?

Also, what modules are loaded:
```
lsmod
```

---

### Post by sochin on 2013-04-27
> **Toz said:**
> How about in /sys/class/leds:
```
ls /sys/class/leds
```
...anything there about keyboard backlight?

Also, what modules are loaded:
```
lsmod
```

Hmm, this is Greek to me:
phy0-led> cd /sys/class/leds
leds> ll
total 0
lrwxrwxrwx 1 root root 0 Apr 27 11:05 phy0-led -> ../../devices/pci0000:00/0000:00:1c.0/0000:02:00.0/leds/phy0-led

leds> cd phy0-led
phy0-led> ll
total 0
-rw-r--r-- 1 root root 4096 Apr 27 11:09 brightness
lrwxrwxrwx 1 root root    0 Apr 27 11:09 device -> ../../../0000:02:00.0
-r--r--r-- 1 root root 4096 Apr 27 11:09 max_brightness
drwxr-xr-x 2 root root    0 Apr 27 11:09 power
lrwxrwxrwx 1 root root    0 Apr 27 08:50 subsystem -> ../../../../../../class/leds
-rw-r--r-- 1 root root 4096 Apr 27 11:09 trigger
-rw-r--r-- 1 root root 4096 Apr 27 08:50 uevent


phy0-led> lsmod
Module                  Size  Used by
usb_storage            48834  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
parport_pc             32689  0 
rfcomm                 46620  0 
ppdev                  17074  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
nls_iso8859_1          12714  1 
tpm_infineon           17537  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
coretemp               13401  0 
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_hda_intel          33492  3 
kvm                   414071  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12530  2 
ghash_clmulni_intel    13221  0 
snd_hwdep              17699  1 snd_hda_codec
aesni_intel            51038  3 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
microcode              22804  0 
nouveau               896008  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                18681  0 
i915                  520615  3 
iwlwifi               386799  0 
sony_laptop            54040  0 
ttm                    83596  1 nouveau
mac_hid                13206  0 
drm_kms_helper         49113  2 nouveau,i915
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   288721  6 nouveau,i915,ttm,drm_kms_helper
mac80211              540032  1 iwlwifi
psmouse                95595  0 
rtsx_pci_ms            13012  0 
i2c_algo_bit           13414  2 nouveau,i915
mxm_wmi                13022  1 nouveau
soundcore              15048  1 snd
wmi                    19071  2 nouveau,mxm_wmi
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
cfg80211              206797  2 iwlwifi,mac80211
memstick               16555  1 rtsx_pci_ms
mei                    40691  0 
lpc_ich                17062  0 
video                  19391  2 nouveau,i915
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
rtsx_pci_sdmmc         17476  0 
rtsx_pci               33452  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25721  4 
libahci                31192  1 ahci
r8169                  61651  0

---

### Post by Toz on 2013-04-27
```
$ modinfo sony-laptop 
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/platform/x86/sony-laptop.ko
version:        0.6
license:        GPL
description:    Sony laptop extras driver (SPIC and SNC ACPI device)
author:         Stelian Pop, Mattia Dongili
srcversion:     B1FE420593DBF709FFDA964
alias:          acpi*:SNY6001:*
alias:          acpi*:SNY5001:*
depends:        
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           debug:set this to 1 (and RTFM) if you want to help the development of this driver (int)
parm:           no_spic:set this if you don't want to enable the SPIC device (int)
parm:           compat:set this if you want to enable backward compatibility mode (int)
parm:           mask:set this to the mask of event you want to enable (see doc) (ulong)
parm:           camera:set this to 1 to enable Motion Eye camera controls (only use it if you have a C1VE or C1VN model) (int)
parm:           minor:minor number of the misc device for the SPIC compatibility code, default is -1 (automatic) (int)
**parm:           kbd_backlight:set this to 0 to disable keyboard backlight, 1 to enable it (default: 0) (int)**
parm:           kbd_backlight_timeout:set this to 0 to set the default 10 seconds timeout, 1 for 30 seconds, 2 for 60 seconds and 3 to disable timeout (default: 0) (int)

```

Even though enabled seems to be the default, can you try this:
```
sudo modprobe -r sony_laptop
sudo modprobe -v sony_laptop kbd_backlight=0
```
...and see if it disables the keyboard backlight. Look also for any messages that may display on the screen.

Try also with the value 1 just to test.

---

### Post by sochin on 2013-04-27
I seem to get the same parameters:

```

~> modinfo sony-laptop | grep kbd
parm:           kbd_backlight:set this to 0 to disable keyboard backlight, 1 to enable it (default: 0) (int)
parm:           kbd_backlight_timeout:set this to 0 to set the default 10 seconds timeout, 1 for 30 seconds, 2 for 60 seconds and 3 to disable timeout (default: 0) (int)

```

Using the suggested command:

```

~> sudo modprobe -r sony_laptop
~> sudo modprobe -l sony_laptop
kernel/drivers/platform/x86/sony-laptop.ko
~> sudo modprobe -v sony_laptop kbd_backlight=0
insmod /lib/modules/3.5.0-27-generic/kernel/drivers/platform/x86/sony-laptop.ko kbd_backlight=0

```

Doesn't seem to affect the keyboard backlight. 

I tried various permutations of kbd_backlight and kbd_backlight_timeout,
it consistenly responds with a 10 second backlight. 

```

~> sudo modprobe -r sony_laptop
~> sudo modprobe -v sony_laptop kbd_backlight=1
insmod /lib/modules/3.5.0-27-generic/kernel/drivers/platform/x86/sony-laptop.ko kbd_backlight=1
~> 
~> sudo modprobe -r sony_laptop
~> sudo modprobe -v sony_laptop kbd_backlight=0
insmod /lib/modules/3.5.0-27-generic/kernel/drivers/platform/x86/sony-laptop.ko kbd_backlight=0
~> 
~> sudo modprobe -r sony_laptop
~> sudo modprobe -v sony_laptop kbd_backlight_timeout=3
insmod /lib/modules/3.5.0-27-generic/kernel/drivers/platform/x86/sony-laptop.ko kbd_backlight_timeout=3

```

I recall seeing another discussion on another forum that suggested
the light sensor had to also be disabled... (?)

---

### Post by Toz on 2013-04-27
Have a read of: [http://askubuntu.com/questions/276983/cant-disable-control-keyboard-backlight-on-sony-vaio-vpcf236fm]("http://askubuntu.com/questions/276983/cant-disable-control-keyboard-backlight-on-sony-vaio-vpcf236fm").

I'm sorry, but I don't know why you don't have that location on your system.

---

