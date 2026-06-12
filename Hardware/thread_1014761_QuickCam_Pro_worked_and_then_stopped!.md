---
title: "QuickCam Pro worked and then stopped!"
date: 2008-12-18
forum: Hardware
---

### Post by eager2know on 2008-12-18
Hi everyone. I am getting a little frustrated with my Logitech QuickCam Pro fro Notebooks. Last sunday I just plugged it in and everything worked perfect right off the bat. Ekiga phone and Skype both worked like a charm.  The syslog had the following lines:

```

Dec 14 12:11:01 toshiba kernel: [  587.920067] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec 14 12:11:02 toshiba kernel: [  588.257016] usb 1-1: configuration #1 chosen from 1 choice
Dec 14 12:11:02 toshiba kernel: [  589.059751] Linux video capture interface: v2.00
Dec 14 12:11:05 toshiba kernel: [  592.085093] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
Dec 14 12:11:06 toshiba kernel: [  592.108176] input: UVC Camera (046d:08c3) as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
Dec 14 12:11:06 toshiba kernel: [  592.114441] usbcore: registered new interface driver snd-usb-audio
Dec 14 12:11:06 toshiba kernel: [  592.118576] usbcore: registered new interface driver uvcvideo
Dec 14 12:11:06 toshiba kernel: [  592.118597] USB Video Class driver (v0.1.0)	

```

Last night after installing some auto-offered updates I tried to get my cam working with Skype again and it just stopped. The driver is unable to initialize the device with return code (-5). The syslog now shows this:

```

Dec 17 23:16:36 toshiba kernel: [  184.904083] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec 17 23:16:37 toshiba kernel: [  185.230971] usb 1-1: configuration #1 chosen from 1 choice
Dec 17 23:16:37 toshiba kernel: [  185.669168] Linux video capture interface: v2.00
Dec 17 23:16:37 toshiba kernel: [  185.710851] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
Dec 17 23:16:38 toshiba kernel: [  186.713610] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
Dec 17 23:16:39 toshiba kernel: [  187.717445] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
Dec 17 23:16:39 toshiba kernel: [  187.717467] uvcvideo: Failed to initialize the device (-5).

```

The camera is listed when i do lsusb and driver seems to recognize it but it is no longer able to initialize it...
](*,)

Has anyone had similar experience?? Is there a way to get things back to working order???

---

### Post by acimmarusti on 2009-01-16
I've been experiencing quite a bit of trouble with that webcam as well on intrepid 8.10. The only program that gets my webcam working properly is luvcview.

try to use it, to check if your device works fine.

I've never been able to make ekiga work with this webcam. Skype works, but it's plagued with a annoying bug concerning audio and bluetooth (even though I don't use one).

Since this webcam uses the UVC video driver, I would encourage you to download the latest driver (source code) and compile it yourself. It definetly gets the webcam working, albeit not with all software!

---

### Post by eager2know on 2009-02-05
Thanks for the pointers. Where do I get the source for the video driver from and how do I compile it? Could you provide me with more specifics? Thanks.

---

### Post by vk4ebp on 2009-06-23
I have a similar problem where it worked only on first try and then stopped. Camera is x08c3, QC for Notebooks Pro. lsusb shown an increase in Device ID number with each plugging-in episode.
I found this 
[http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities]("http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities")
 but haven't found the patch it refers to yet. I wonder if anyone had any luck with this patch?

---

