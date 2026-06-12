---
title: "Philips PCVC690K Webcam Microphone Issues"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by ayapejian on 2008-03-30
Hey Everyone ... I'm trying to get the builtin microphone working from this Philips webcam working.  I can't seem to get Audacity to detect it, not sure if ALSA is seeing it either ... new to the recording / sound area with linux.  The video portion of the webcam works fine as verified in ekiga, however the sound doesn't work in that app either. 

If I unplug the USB cable and replug it in I get the following output in the '/var/log/debug' log and the following entries in dmesg ... I've tried messing around with the 'gnome-volume-control' app, and selected all the input devices that it lists, and turned all of them up, then switched audacity and tried all 3 options it gives ... none of which shows any input when monitoring.  The 3 choices Audacity give are:
[LIST]
[*]'OSS: /dev/dsp', 
[*]'ALSA: HDA NVidia: ALC883 Analog (hw:0,0)'
[*]'ALSA: HDA NVidia: ALC883 Analog (hw:0,2)'
[*]'ALSA: Default'
[/LIST]

'/var/log/debug'
```

Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.948500] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_video4linux_0'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.948812] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.949597] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_mixer__1'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.950032] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_pcm_0'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.951928] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_alsa_capture_0'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.953328] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_alsa_control__1'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.953854] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.954376] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_if2'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.955924] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_usbraw'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.956525] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_pcm_0_0'). 
Mar 30 21:51:04 Pheonix NetworkManager: <debug> [1206928264.957360] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B'). 
Mar 30 21:51:09 Pheonix NetworkManager: <debug> [1206928269.709104] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B'). 
Mar 30 21:51:09 Pheonix NetworkManager: <debug> [1206928269.742611] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.596791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_video4linux_0'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.635238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.851969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_pcm_0'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.853058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_alsa_capture_0'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.854060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_pcm_0_0'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.855317] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_oss_mixer__1'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.884042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_if2'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.885360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_alsa_control__1'). 
Mar 30 21:51:10 Pheonix NetworkManager: <debug> [1206928270.902105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_30c_02130211E010021B_usbraw'). 

```

dmesg
```

[ 4034.005894] usb 2-6: USB disconnect, address 15
[ 4038.189397] usb 2-6: new full speed USB device using ohci_hcd and address 16
[ 4038.755034] usb 2-6: configuration #1 chosen from 1 choice
[ 4038.762985] pwc: Philips PCVC690K (Vesta Pro Scan) USB webcam detected.
[ 4039.641682] pwc: Registered as /dev/video1.

```

---

