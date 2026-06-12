---
title: "USB Speakers support for old laptop"
date: 2008-06-04
forum: Hardware
---

### Post by dspayre on 2008-06-04
I hope I am posting in the right forum.  I have exhausted all my resources and was wondering if any gurus can shed some light on my problem.

I only started using linux a few months ago and I am hooked.  It is really satisfying to solve the problems and this forum has been a great resource.

Here is my problem:

Laptop:  Dell Inspiron 2100 (very old) with USB 1.1
USB Speakers:  Nexxtech USB 2.0 Stereo Notebook Speakers
OS:  Fluxbuntu

I can't seem to get these speakers to work on this system.  I was wondering if my problem is that USB 2.0 is not compatible with 1.1 or my laptop is not capable of supporting USB audio.

There are drivers loaded for the onboard sound.  I have tried to set the snd_usb_audio to index 0 in alsa-base but it seems to always be set to index 0.  I even blacklisted my onboard sound and the result from "cat /proc/asound/modules" still sets snd_usb_audio to 1 and no device for 0.  

dmesg | grep usb shows:

[ 1415.834987] usbcore: registered new interface driver usbfs
[ 1415.835054] usbcore: registered new interface driver hub
[ 1415.835123] usbcore: registered new device driver usb
[   10.900000] usb usb1: configuration #1 chosen from 1 choice
[   11.244000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   11.424000] usb 1-1: configuration #1 chosen from 1 choice
[   12.400000] usbcore: registered new interface driver hiddev
[   13.884000] input: USB HID v1.00 Device [USB Audio Device] on usb-0000:00:07.2-1
[   13.884000] usbcore: registered new interface driver usbhid
[   13.884000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.392000] usbcore: registered new interface driver xpad
[   42.736000] usbcore: registered new interface driver snd-usb-audio
[ 2180.732000] usb 1-1: USB disconnect, address 2
[ 2186.556000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 2186.736000] usb 1-1: configuration #1 chosen from 1 choice
[ 2186.752000] input: USB HID v1.00 Device [USB Audio Device] on usb-0000:00:07.2-1

Does anyone know if I just have a hardware compatibility issue or is it just a driver issue?  I really don't know where to go from here.

---

