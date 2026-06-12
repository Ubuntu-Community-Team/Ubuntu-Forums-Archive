---
title: "logitech c525 webcam microphone"
date: 2016-12-04
forum: Hardware
---

### Post by jgw on 2016-12-04
I have a logitech c525 webcam.  In theory this camera should just work.  The camera does work but the microphone is not recognized by any program I could find.  It is listed in lsusb as: Bus 008 Device 004: ID 046d:0826 Logitech, Inc. HD Webcam C525   pulse volume control doesn't recognize it, skype doesn't recognize it, etc.  I think I am missing something here.  Its also listed in "Linux UVC driver and tools" as supported.  

I have tried everything I could think of.  I have also included a shot of alsa mixer for the camera microphone

pulseaudio -vvv returned (amongst other things):
E: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
E: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-046d_HD_Webcam_C525_1C9273A0-00" card_name="alsa_card.usb-046d_HD_Webcam_C525_1C9273A0-00" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:09.0/0000:03:00.0/usb8/8-3/8-3.3/8-3.3:1.0/sound/card1 (alsa_card.usb-046d_HD_Webcam_C525_1C9273A0-00) failed to load module.
D: [pulseaudio] protocol-native.c: Protocol version: remote 30, local 30
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] srbchannel.c: SHM block is 65472 bytes, ringbuffer capacity is 2 * 32712 bytes
D: [pulseaudio] protocol-native.c: Enabling srbchannel...
I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:09.0/0000:03:00.0/usb8/8-3/8-3.3/8-3.3:1.0/sound/card1 is busy: no
D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="usb-046d_HD_Webcam_C525_1C9273A0-00" card_name="alsa_card.usb-046d_HD_Webcam_C525_1C9273A0-00" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio1'
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HD Webcam C525/HD Webcam C525.conf
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HD Webcam C525
I: [pulseaudio] (alsa-lib)main.c: error: failed to import HD Webcam C525 use case configuration -2
I: [pulseaudio] alsa-ucm.c: UCM not available for card HD Webcam C525

[ATTACH=CONFIG]272562[/ATTACH]

Thoughts?

Thank you ......................

---

### Post by gordintoronto on 2016-12-05
Have you considered just using a cheap external microphone? Logitech provides a driver for the microphone under Windows, which indicates that it's not a standard mic.

Have you reviewed this?
[http://askubuntu.com/questions/163729/microphone-is-not-working-in-skype](http://askubuntu.com/questions/163729/microphone-is-not-working-in-skype)

---

### Post by jgw on 2016-12-05
Thank you for the reply.  I suspect your solution will be THE solution but this just drives me nuts.  Part sees it part does not, I just know I am missing something.

---

