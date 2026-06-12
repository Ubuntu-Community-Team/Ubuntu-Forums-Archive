---
title: "Why Did Webcam Stopped Working"
date: 2009-03-12
forum: Hardware
---

### Post by abiggy on 2009-03-12
Hello,

I am having an issue with my webcam. I just installed Ubuntu about a week ago and have been installing all the programs I have wanted. Anyway for the first week or so I had my Skype video, cheese, aMSN working with my webcam, which is a Logitech Quickcam for Notebook Pro. I had it plugged in through a high speed usb hub. 

As of yesterday it has stopped working. Nothing seems to recognize even when I plug it directly into my computer. When I plug it in now i get from dmesg:

```
[ 1599.080266] usb 5-7.1: new high speed USB device using ehci_hcd and address 14
[ 1599.359950] usb 5-7.1: configuration #1 chosen from 1 choice
[ 1599.360844] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
[ 1600.360185] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[ 1601.360283] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[ 1601.360298] uvcvideo: Failed to initialize the device (-5).
[ 1602.323537] 14:3:3: cannot set freq 16000 to ep 0x86
```

In addition the most bizarre part is that there is a microphone built into the webcam and it still allows me to use it for voice calls with skype, although the sound has become very delayed almost 3 seconds but I think that may just be another issue. Not sure if it helps but PulseAudio calls the mic *ALSA PCM on hw:2 (USB Audio) via DMA*. I was wondering if anyone knows why this issue would arise and maybe how I could solve it for good!? 

Any help would be greatly appreciated!

Thanks in advance,

Adam

---

### Post by vk4ebp on 2009-06-23
I have a similar problem where it worked only on first try and then stopped. Camera is x08c3, QC for Notebooks Pro. lsusb shown an increase in Device ID number with each plugging-in episode.
I found this
[http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities]("http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities")
but haven't found the patch it refers to yet. I wonder if anyone had any luck with this patch?

---

### Post by IcarusR on 2009-06-23
The patch is the code in this message [http://lists.berlios.de/pipermail/linux-uvc-devel/2007-March/001476.html]("http://lists.berlios.de/pipermail/linux-uvc-devel/2007-March/001476.html")

---

