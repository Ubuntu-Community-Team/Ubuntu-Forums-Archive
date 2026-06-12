---
title: "Ubuntu 10.10 Webcam problem"
date: 2010-11-23
forum: Hardware
---

### Post by rkrdo on 2010-11-23
So my laptop's webcam stopped working all of the sudden, I have a Samsung q430-11. Whenever I open cheese I don't get any errors, just a black screen and when using the command lsusb I get this:
```

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1210:25f4 DigiTech 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```and when using gstreamer-properties I get this:
```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

```It's kind of weird that is used to work just fine in Ubuntu 10.04

---

### Post by Fafler on 2010-11-24
```
tail -f /var/log/messages
```
Connect cam, start cheese and post output :-)

---

### Post by rkrdo on 2010-11-24
I can't plug or unplug the webcam since it's built in the laptop but from the command you gave me I got this:

```

Nov 24 00:06:03 ricardo-laptop kernel: [10515.599616] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:06:45 ricardo-laptop kernel: [10558.010784] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:06:45 ricardo-laptop kernel: [10558.025583] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:06:46 ricardo-laptop kernel: [10558.342013] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:06:46 ricardo-laptop kernel: [10558.357859] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:07:33 ricardo-laptop kernel: [10605.761584] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:07:33 ricardo-laptop kernel: [10605.775345] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:07:39 ricardo-laptop kernel: [10611.249748] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:07:39 ricardo-laptop kernel: [10611.266479] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:08:21 ricardo-laptop kernel: [10653.677967] NVRM: os_raise_smp_barrier(), invalid context!
Nov 24 00:08:21 ricardo-laptop kernel: [10653.692783] NVRM: os_raise_smp_barrier(), invalid context!


```

---

### Post by Fafler on 2010-11-24
Then try this instead:
```
 cat /var/log/messages | grep video
```
You log might be full of those  NVRM: os_raise_smp_barrier(), invalid context! errors you get. Those are by the way, probably an issue with 64 bit Ubuntu and the Nvidia driver, but if it doesn't cause any unstability, just ignore it. Anyway, if /var/log/messages doesn't give any usefull info, try the command on the archived files.

```
 sudo cat /var/log/messages.{1,2,3,4} | grep video
```

---

### Post by rkrdo on 2010-11-24
Using the ```
cat /var/log/messages | grep video
``` command I get this:

```

Nov 21 03:14:19 ricardo-laptop kernel: [   19.012218] Linux video capture interface: v2.00
Nov 21 03:14:19 ricardo-laptop kernel: [   19.027988] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 21 03:14:19 ricardo-laptop kernel: [   19.034556] usbcore: registered new interface driver uvcvideo
Nov 21 03:36:48 ricardo-laptop kernel: [   21.693752] Linux video capture interface: v2.00
Nov 21 03:36:48 ricardo-laptop kernel: [   21.700078] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 21 03:36:48 ricardo-laptop kernel: [   21.709000] usbcore: registered new interface driver uvcvideo
Nov 21 03:39:36 ricardo-laptop kernel: [   19.757659] Linux video capture interface: v2.00
Nov 21 03:39:36 ricardo-laptop kernel: [   19.771827] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 21 03:39:36 ricardo-laptop kernel: [   19.781802] usbcore: registered new interface driver uvcvideo
Nov 21 03:42:17 ricardo-laptop kernel: [18446744065.459048] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 220.537 msecs
Nov 21 03:42:17 ricardo-laptop kernel: [18446744065.459056] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 123.187 msecs
Nov 21 03:42:17 ricardo-laptop kernel: [18446744066.669301] video LNXVIDEO:00: Restoring backlight state
Nov 21 03:42:19 ricardo-laptop kernel: [18446744068.502624] Modules linked in: easy_slow_down_manager parport_pc ppdev snd_hda_codec_nvhdmi binfmt_misc acpi_cpufreq joydev snd_hda_codec_realtek snd_hda_intel arc4 snd_hda_codec snd_hwdep nvidia(P) snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ath9k ath9k_common ath9k_hw ath mac80211 snd_timer snd_seq_device uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 cfg80211 psmouse serio_raw video output intel_ips intel_agp snd led_class soundcore snd_page_alloc lp parport ahci libahci sky2
Nov 21 12:19:58 ricardo-laptop kernel: [   19.081780] Linux video capture interface: v2.00
Nov 21 12:19:58 ricardo-laptop kernel: [   19.095243] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 21 12:19:58 ricardo-laptop kernel: [   19.099441] usbcore: registered new interface driver uvcvideo
Nov 22 11:04:04 ricardo-laptop kernel: [   22.293933] Linux video capture interface: v2.00
Nov 22 11:04:04 ricardo-laptop kernel: [   22.300191] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 11:04:04 ricardo-laptop kernel: [   22.311943] usbcore: registered new interface driver uvcvideo
Nov 22 13:12:55 ricardo-laptop kernel: [   18.725985] Linux video capture interface: v2.00
Nov 22 13:12:55 ricardo-laptop kernel: [   18.849416] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 13:12:55 ricardo-laptop kernel: [   18.852557] usbcore: registered new interface driver uvcvideo
Nov 22 13:37:26 ricardo-laptop kernel: [   18.764194] Linux video capture interface: v2.00
Nov 22 13:37:26 ricardo-laptop kernel: [   18.786302] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 13:37:26 ricardo-laptop kernel: [   18.803643] usbcore: registered new interface driver uvcvideo
Nov 22 16:07:54 ricardo-laptop kernel: [   21.047229] Linux video capture interface: v2.00
Nov 22 16:07:54 ricardo-laptop kernel: [   21.070988] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 16:07:54 ricardo-laptop kernel: [   21.191108] usbcore: registered new interface driver uvcvideo
Nov 22 17:27:09 ricardo-laptop kernel: [   18.933917] Linux video capture interface: v2.00
Nov 22 17:27:09 ricardo-laptop kernel: [   18.952094] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 17:27:09 ricardo-laptop kernel: [   18.960315] usbcore: registered new interface driver uvcvideo
Nov 22 18:10:43 ricardo-laptop kernel: [   18.783711] Linux video capture interface: v2.00
Nov 22 18:10:43 ricardo-laptop kernel: [   18.806853] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 18:10:43 ricardo-laptop kernel: [   18.814520] usbcore: registered new interface driver uvcvideo
Nov 22 19:35:24 ricardo-laptop kernel: [   18.871888] Linux video capture interface: v2.00
Nov 22 19:35:24 ricardo-laptop kernel: [   18.908112] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 22 19:35:24 ricardo-laptop kernel: [   18.921074] usbcore: registered new interface driver uvcvideo
Nov 23 01:15:12 ricardo-laptop kernel: [   23.229307] Linux video capture interface: v2.00
Nov 23 01:15:12 ricardo-laptop kernel: [   23.241360] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 01:15:12 ricardo-laptop kernel: [   23.253093] usbcore: registered new interface driver uvcvideo
Nov 23 03:09:44 ricardo-laptop kernel: [   22.399881] Linux video capture interface: v2.00
Nov 23 03:09:44 ricardo-laptop kernel: [   22.410528] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 03:09:44 ricardo-laptop kernel: [   22.414038] usbcore: registered new interface driver uvcvideo
Nov 23 03:28:47 ricardo-laptop kernel: [   19.778172] Linux video capture interface: v2.00
Nov 23 03:28:47 ricardo-laptop kernel: [   19.808322] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 03:28:47 ricardo-laptop kernel: [   19.812424] usbcore: registered new interface driver uvcvideo
Nov 23 13:07:36 ricardo-laptop kernel: [   19.075999] Linux video capture interface: v2.00
Nov 23 13:07:36 ricardo-laptop kernel: [   19.085897] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 13:07:36 ricardo-laptop kernel: [   19.090789] usbcore: registered new interface driver uvcvideo
Nov 23 15:39:31 ricardo-laptop kernel: [   19.864275] Linux video capture interface: v2.00
Nov 23 15:39:31 ricardo-laptop kernel: [   19.868413] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 15:39:31 ricardo-laptop kernel: [   19.925218] usbcore: registered new interface driver uvcvideo
Nov 23 16:07:43 ricardo-laptop kernel: [   18.921776] Linux video capture interface: v2.00
Nov 23 16:07:43 ricardo-laptop kernel: [   18.972563] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 16:07:43 ricardo-laptop kernel: [   18.977605] usbcore: registered new interface driver uvcvideo
Nov 23 16:42:28 ricardo-laptop kernel: [   21.119124] Linux video capture interface: v2.00
Nov 23 16:42:28 ricardo-laptop kernel: [   21.190954] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 16:42:28 ricardo-laptop kernel: [   21.194487] usbcore: registered new interface driver uvcvideo
Nov 23 17:37:12 ricardo-laptop kernel: [ 3299.808308] usbcore: deregistering interface driver uvcvideo
Nov 23 17:37:15 ricardo-laptop kernel: [ 3302.784749] Linux video capture interface: v2.00
Nov 23 17:37:15 ricardo-laptop kernel: [ 3302.787840] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 17:37:15 ricardo-laptop kernel: [ 3302.790880] usbcore: registered new interface driver uvcvideo
Nov 23 19:16:07 ricardo-laptop kernel: [   18.874190] Linux video capture interface: v2.00
Nov 23 19:16:07 ricardo-laptop kernel: [   18.920135] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 19:16:07 ricardo-laptop kernel: [   18.930610] usbcore: registered new interface driver uvcvideo
Nov 23 20:23:57 ricardo-laptop kernel: [   25.065882] Linux video capture interface: v2.00
Nov 23 20:23:57 ricardo-laptop kernel: [   25.069144] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 20:23:57 ricardo-laptop kernel: [   25.072911] usbcore: registered new interface driver uvcvideo
Nov 23 21:10:50 ricardo-laptop kernel: [   19.253231] Linux video capture interface: v2.00
Nov 23 21:10:50 ricardo-laptop kernel: [   19.279676] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 23 21:10:50 ricardo-laptop kernel: [   19.283007] usbcore: registered new interface driver uvcvideo
Nov 24 12:11:44 ricardo-laptop kernel: [   23.702780] Linux video capture interface: v2.00
Nov 24 12:11:44 ricardo-laptop kernel: [   23.805817] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Nov 24 12:11:44 ricardo-laptop kernel: [   23.809587] usbcore: registered new interface driver uvcvideo

```

It seem that the laptop does detect the webcam but it still doesnt work

---

### Post by Fafler on 2010-11-24
Indeed it is. As i last few things to check before i´m out of ideas, is to 1) check the permissions to the camera and 2) check that you actually chose the camera in cheese. Double check.

Now, a temporary solution, even though it´s a bit of a hassle is to install VitualBox (the Oracle version, not the one in the repositories) and run 10.04 on top of it.

You seem quite competent, so i think you should see if the ucvidideo guys have a mailing list. In that case, you should cantact them. Or search for people with similar problems, using the log info you have.

---

### Post by Rebootkid on 2011-01-22
So, recently converted from 32 bit to 64 bit, both 10.10 installs.

Everything worked just fine under 32, but 64, nothing would detect the webcam.

lsusb showed the hardware was good

lsusb
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod showed the video bits were there

lsmod | grep video
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
video                  22176  0 
output                  2527  1 video

However, when I checked the /dev directory, there was no "video" or "video0" listed.

Checked dmesg


$ dmesg | grep video
[    0.673628] pci 0000:01:00.0: Boot video device
[   15.883524] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   15.938648] Linux video capture interface: v2.00
[   15.987854] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   15.990111] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   16.002792] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   16.002869] uvcvideo: Failed to initialize the device (-5).
[   16.003006] usbcore: registered new interface driver uvcvideo

Okay, the cam didn't initialize properly. Not sure why, but I suspect that everything is still looking for the 32bit video drivers. I'm not even sure if V4L has 64bit drivers.

Went and grabbed the 32bit drivers with
sudo apt-get install lib32v4l-dev

Then, downed and upped the cam with
sudo rmmod uvcvideo
sudo modprobe uvcvideo

I haven't rebooted yet, but I think it'll stay.

Now skype, flash, etc, all detect the webcam.

Hope this is helpful to others

---

