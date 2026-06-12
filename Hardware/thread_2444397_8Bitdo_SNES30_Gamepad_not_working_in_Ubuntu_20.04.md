---
title: "8Bitdo SNES30 Gamepad not working in Ubuntu 20.04"
date: 2020-05-29
forum: Hardware
---

### Post by marcio-toloi on 2020-05-29
Hello guys.

I have a 8Bitdo bluetooth SNES30 Gamepad. I'm trying to use it with USB cable in Ubuntu 20.04 LTS. I used to play wired with it in my old installation of Xubuntu 16.04.

I'm trying for days. Followed most of tips people saying about creating specific UDEV rules (Retropie forums). I also tried using bluetooth. Sometimes it works for like 2 minutes before disconnecting.

The path "/dev/input/js0" is not being created after I plug in the usb cable.

```

$ jstest /dev/input/js0
jstest: No such file or directory
```


Here is some other informations:


$ lsusb
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 033: ID 2dc8:ab20 SNES30             SNES30 Joy    
Bus 003 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 002: ID 04d9:a09f Holtek Semiconductor, Inc. E-Signal LUOM G10 Mechanical Gaming Mouse
Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


$ udevadm monitor (when I plug in the usb cable):
```
KERNEL[2696.469166] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7 (usb)
KERNEL[2696.470791] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
KERNEL[2696.471755] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
KERNEL[2696.472092] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43 (input)
KERNEL[2696.472533] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/event19 (input)
KERNEL[2696.531458] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/js0 (input)
KERNEL[2696.531507] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/hidraw/hidraw3 (hidraw)
KERNEL[2696.531541] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
KERNEL[2696.531578] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
KERNEL[2696.531613] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7 (usb)
UDEV  [2696.540172] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7 (usb)
KERNEL[2696.543593] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/event19 (input)
UDEV  [2696.543634] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
UDEV  [2696.545725] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
UDEV  [2696.552257] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/hidraw/hidraw3 (hidraw)
KERNEL[2696.563212] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/js0 (input)
KERNEL[2696.579224] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43 (input)
KERNEL[2696.579347] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/hidraw/hidraw3 (hidraw)
KERNEL[2696.579364] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
KERNEL[2696.579379] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
KERNEL[2696.579390] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
UDEV  [2696.579982] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43 (input)
UDEV  [2696.581847] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/event19 (input)
UDEV  [2696.586359] add      /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/js0 (input)
UDEV  [2696.587573] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
UDEV  [2696.588729] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
UDEV  [2696.592818] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-7 (usb)
UDEV  [2696.594205] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/event19 (input)
UDEV  [2696.595972] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/hidraw/hidraw3 (hidraw)
UDEV  [2696.596204] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43/js0 (input)
UDEV  [2696.597363] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C/input/input43 (input)
UDEV  [2696.598226] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
UDEV  [2696.598874] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001C (hid)
UDEV  [2696.599968] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0 (usb)
KERNEL[2696.607436] add      /devices/parport0/ppdev0.0 (parport)
KERNEL[2696.607454] bind     /devices/parport0/ppdev0.0 (parport)
KERNEL[2696.607461] unbind   /devices/parport0/ppdev0.0 (parport)
KERNEL[2696.607467] remove   /devices/parport0/ppdev0.0 (parport)
UDEV  [2696.608251] add      /devices/parport0/ppdev0.0 (parport)
UDEV  [2696.608804] bind     /devices/parport0/ppdev0.0 (parport)
UDEV  [2696.609284] unbind   /devices/parport0/ppdev0.0 (parport)
UDEV  [2696.609690] remove   /devices/parport0/ppdev0.0 (parport)
```


$ lsmod
```
Module                  Size  Used by
hid_sjoy               20480  0
ff_memless             20480  1 hid_sjoy
rfcomm                 81920  16
cmac                   16384  6
algif_hash             16384  3
algif_skcipher         16384  3
af_alg                 24576  14 algif_hash,algif_skcipher
bnep                   24576  2
snd_hda_codec_hdmi     61440  1
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
nvidia_uvm            966656  0
kvm                   663552  0
mei_hdcp               24576  0
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
nvidia_drm             45056  6
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
nvidia_modeset       1114112  9 nvidia_drm
snd_hda_intel          53248  7
snd_intel_dspcfg       24576  1 snd_hda_intel
aesni_intel           372736  9
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_usb_audio         258048  2
crypto_simd            16384  1 aesni_intel
cryptd                 24576  5 crypto_simd,ghash_clmulni_intel
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_usbmidi_lib        36864  1 snd_usb_audio
glue_helper            16384  1 aesni_intel
uvcvideo               98304  0
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
nvidia              20430848  358 nvidia_uvm,nvidia_modeset
snd_seq_midi           20480  0
intel_cstate           20480  0
intel_rapl_perf        20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_vmalloc      20480  1 uvcvideo
eeepc_wmi              16384  0
videobuf2_memops       20480  1 videobuf2_vmalloc
asus_wmi               32768  1 eeepc_wmi
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
videobuf2_v4l2         24576  1 uvcvideo
btusb                  57344  0
sparse_keymap          16384  1 asus_wmi
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
wmi_bmof               16384  0
btrtl                  24576  1 btusb
snd_pcm               106496  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
videodev              225280  3 videobuf2_v4l2,uvcvideo,videobuf2_common
input_leds             16384  0
btbcm                  16384  1 btusb
serio_raw              20480  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
btintel                24576  1 btusb
mc                     53248  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
joydev                 24576  0
drm_kms_helper        184320  1 nvidia_drm
snd_timer              36864  2 snd_seq,snd_pcm
bluetooth             581632  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ipmi_devintf           20480  0
snd                    90112  31 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
ipmi_msghandler       106496  2 ipmi_devintf,nvidia
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ecdh_generic           16384  1 bluetooth
sysimgblt              16384  1 drm_kms_helper
ecc                    28672  1 ecdh_generic
mei_me                 40960  1
soundcore              16384  1 snd
mei                   106496  3 mei_hdcp,mei_me
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
drm                   491520  9 drm_kms_helper,nvidia_drm
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  3 usbhid,hid_generic,hid_sjoy
crc32_pclmul           16384  0
i2c_i801               32768  0
ahci                   40960  3
r8169                  90112  0
lpc_ich                24576  0
libahci                32768  1 ahci
realtek                24576  1
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  1 asus_wmi
```


$ dmesg (just after I plug in the usb cable):
```
[ 3038.801957] usb 3-7: new full-speed USB device number 34 using xhci_hcd
[ 3038.951538] usb 3-7: New USB device found, idVendor=2dc8, idProduct=ab20, bcdDevice= 0.01
[ 3038.951544] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3038.951548] usb 3-7: Product: SNES30 Joy    
[ 3038.951551] usb 3-7: Manufacturer: SNES30            
[ 3038.953789] input: SNES30             SNES30 Joy     as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001D/input/input44
[ 3039.014558] hid-generic 0003:2DC8:AB20.001D: input,hidraw3: USB HID v1.10 Joystick [SNES30             SNES30 Joy    ] on usb-0000:00:14.0-7/input0
```

$ journalctl -f
```
mai 29 18:30:07 pc-home kernel: usb 3-7: new full-speed USB device number 36 using xhci_hcd
mai 29 18:30:07 pc-home kernel: usb 3-7: New USB device found, idVendor=2dc8, idProduct=ab20, bcdDevice= 0.01
mai 29 18:30:07 pc-home kernel: usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
mai 29 18:30:07 pc-home kernel: usb 3-7: Product: SNES30 Joy    
mai 29 18:30:07 pc-home kernel: usb 3-7: Manufacturer: SNES30            
mai 29 18:30:07 pc-home kernel: input: SNES30             SNES30 Joy     as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:2DC8:AB20.001F/input/input46
mai 29 18:30:07 pc-home kernel: hid-generic 0003:2DC8:AB20.001F: input,hidraw3: USB HID v1.10 Joystick [SNES30             SNES30 Joy    ] on usb-0000:00:14.0-7/input0
mai 29 18:30:07 pc-home mtp-probe[5299]: checking bus 3, device 36: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7"
mai 29 18:30:07 pc-home mtp-probe[5299]: bus: 3, device: 36 was not an MTP device
mai 29 18:30:07 pc-home fido_id[5309]: 3-7:1.0: Failed to open report descriptor at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/report_descriptor': No such file or directory
mai 29 18:30:07 pc-home systemd-udevd[5308]: js0: Process '/usr/bin/jscal-restore /dev/input/js0' failed with exit code 1.
mai 29 18:30:07 pc-home mtp-probe[5314]: checking bus 3, device 36: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7"
mai 29 18:30:07 pc-home mtp-probe[5314]: bus: 3, device: 36 was not an MTP device
```

$ sudo udevadm info -e
```

...
P: /devices/pci0000:00/0000:00:14.0/usb3/3-7
N: bus/usb/003/037
L: 0
E: DEVPATH=/devices/pci0000:00/0000:00:14.0/usb3/3-7
E: SUBSYSTEM=usb
E: DEVNAME=/dev/bus/usb/003/037
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=2dc8/ab20/1
E: TYPE=0/0/0
E: BUSNUM=003
E: DEVNUM=037
E: MAJOR=189
E: MINOR=292
E: USEC_INITIALIZED=3370177304
E: ID_VENDOR=SNES30
E: ID_VENDOR_ENC=SNES30\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=2dc8
E: ID_MODEL=SNES30_Joy
E: ID_MODEL_ENC=SNES30\x20Joy\x20\x20\x20\x20
E: ID_MODEL_ID=ab20
E: ID_REVISION=0001
E: ID_SERIAL=SNES30_SNES30_Joy
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030000:
E: ID_PATH=pci-0000:00:14.0-usb-0:7
E: ID_PATH_TAG=pci-0000_00_14_0-usb-0_7
...
```


I'll appreciate any help.

Thanks.

---

