---
title: "Logitec Conference Cam Connect Freezes Systems"
date: 2020-08-20
forum: Hardware
---

### Post by barryscholfield on 2020-08-20
[COLOR=#242729][FONT=Arial]Complete novice here. Haven't used ubuntu in years.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have a Logitec Conference Cam Connect. Works fine on Window and Chrome OS. As soon as I plug it into Ubuntu the system freezes and becomes unresponsive. As soon as I unplug it all becomes fine again. Tested on fresh installs of Mate 18.04 and Ubuntu 20.04 after performing all updates.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]No idea where to start to fix this. And have had the question on ask Ubuntu for weeks with no response.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It seems to have something to do with the audio. I can switch the video component of the camera/mic/speaker combo off but even so after about 30sec the system freezes. And it is picked up as an external sound card.

System log at time of error:
[/FONT][/COLOR]
3
Aug 11 11:02:09 barry-System-Product-Name kernel: [ 1623.488198] usb 2-1.2.1: USB disconnect, device number 44
Aug 11 11:02:09 barry-System-Product-Name kernel: [ 1623.490070] usb 2-1.2: clear tt 1 (02c0) error -71
Aug 11 11:02:09 barry-System-Product-Name kernel: [ 1623.494118] usb 2-1.2.1: 1:1: usb_set_interface failed (-71)
Aug 11 11:02:09 barry-System-Product-Name pulseaudio[1713]: [pulseaudio] udev-util.c: Failed to get card object.
Aug 11 11:02:09 barry-System-Product-Name pulseaudio[1713]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 11 11:02:09 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.2
Aug 11 11:02:09 barry-System-Product-Name pulseaudio[1713]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-Logitech_ConferenceCam_Connect_0X450X090XCB0X15-00" card_name="alsa_card.usb-Logitech_ConferenceCam_Connect_0X450X090XCB0X15-00" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 11 11:02:09 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0
Aug 11 11:02:09 barry-System-Product-Name acpid: input device has been disconnected, fd 15
Aug 11 11:02:09 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.1
Aug 11 11:02:09 barry-System-Product-Name acpid: input device has been disconnected, fd 16
Aug 11 11:02:09 barry-System-Product-Name kernel: [ 1623.627156] usb 2-1.2.2: USB disconnect, device number 45
Aug 11 11:02:09 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.3/0003:046D:084C.0018
Aug 11 11:02:09 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.3
Aug 11 11:02:10 barry-System-Product-Name upowerd[1208]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1
Aug 11 11:02:10 barry-System-Product-Name upowerd[1208]: u

---

### Post by SeijiSensei on 2020-08-20
Try installing cheese. You might be missing some libraries that will be installed as dependencies for that program.

```
sudo apt install cheese
```

---

### Post by barryscholfield on 2020-08-20
Have cheese installed, restricted extras, ffmpeg and OBS. The latter being the software that we need to get working. The problem manifests from live disk to fresh install all the way to fully setup system with all codecs and drivers.

Edit: It also replicates on multiple machines. Tested it on both my desktop and an older Compaq laptop. Exactly the same effect.

---

### Post by SeijiSensei on 2020-08-20
Sorry, but I can't help further. I have a Pro 9000 which works out of the box.

What's "OBS"?

---

### Post by Autodave on 2020-08-20
OBS is recording / streaming software: free across all platforms.  Great program.

I am kinda wondering if you have a bad camera?  Shorted unit or cable?

---

