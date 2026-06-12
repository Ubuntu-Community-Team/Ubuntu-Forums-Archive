---
title: "webcam on dell inspiron n4010 with 11.04"
date: 2011-05-29
forum: Hardware
---

### Post by leocertuche on 2011-05-29
hello,

I remember my webcam used to work on 10.04 Lucid Lynx but once I stepped to 10.10 Maverick it stopped working. I upgraded to 11.04 Natty but no luck yet. Here's the output of lsusb:

leocertuche@laptopleo:~$ lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and of guvcview:

leocertuche@laptopleo:~$ sudo guvcview
[sudo] password for leocertuche: 
guvcview 1.4.1
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
opening '/sys/class/video4linux' failed: Error opening directory '/sys/class/video4linux': No such file or directory
Unable to detect devices on your system
ERROR opening V4L interface: No such file or directory
Init video returned -1

Any help is much appreciated.

Thanks in advance,

Leo

---

### Post by leocertuche on 2011-06-10
Hi

I downloaded [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git), compiled and installed. Now the outputs changed a bit but still no luck:

root@laptopleo:~# lsusb 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 010: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 009: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 008: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@laptopleo:~# guvcview 
guvcview 1.4.1
ALSA lib pcm.c:2212(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1613(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
opening '/sys/class/video4linux' failed: Error opening directory '/sys/class/video4linux': No such file or directory
Unable to detect devices on your system
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

Thank you so much for your help!

---

### Post by yogesh4984 on 2011-06-26
Try another software "camorama webcam viewer". This one is working for me on Dell Inpiron n4010 with 11.04 ..
Cheers.

---

### Post by horito on 2011-10-28
I wonder what's going on here... I have similar issues and haven't been able to get the camera working. 

0) it worked on earlier versions of the kernel
1) The driver seems installed, 
2) when I invoke the camera, the LED turn on mommentarily then shuts off... 
3) The device files /dev/videoX change at time

any experiences user that could give me a hint on how to proceed? thanks!

I'm pasting the output of most important cmds. Although I might me missing any... pleaase let me know if you have an idea on how to diagnose the problem. I'm clueless at this point!

output for: uname, dmesg, lsusb, lsmod and guvcview


THANKS!!!!




$ uname -a
Linux xxxxxx 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


lsusb give me:
Bus 001 Device 007: ID 0c45:641d Microdia

for the camera, it is listed in:
[http://www.ideasonboard.org/uvc/#documentation](http://www.ideasonboard.org/uvc/#documentation)

as supported by the uvc drivers

$ lsmod | grep video
uvcvideo               72195  1 
videodev               82052  2 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
video                  19438  1 i915

I wonder if the problem is the i915??


$ guvcview 
guvcview 1.4.1
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
/dev/video1 - device 1
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

$ dmesg
[   55.965547] usb 1-1.4: USB disconnect, address 3
[   56.220313] usb 1-1.4: new high speed USB device using ehci_hcd and address 5
[   56.373724] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[   56.405248] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input11
[  460.475253] usb 1-1.4: USB disconnect, address 5
[  460.734259] usb 1-1.4: new high speed USB device using ehci_hcd and address 6
[  460.887456] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[  460.919115] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input12
[  543.372930] usb 1-1.4: USB disconnect, address 6
[  543.627799] usb 1-1.4: new high speed USB device using ehci_hcd and address 7
[  543.781396] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[  543.812921] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13

---

