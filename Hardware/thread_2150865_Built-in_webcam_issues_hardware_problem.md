---
title: "Built-in webcam issues: hardware problem?"
date: 2013-06-02
forum: Hardware
---

### Post by gladiool on 2013-06-02
Hi guys,

I have an Acer Aspire 5734Z laptop with a built-in webcam. It has always worked just fine in Cheese, Skype, etc., but now all of a sudden I'm having problems with it. Most of the time, the applications can't find my webcam at all now and when they do, the picture is black.

I'm not a real expert in finding log files that might tell me what's wrong, but when I run dmesg I see the following lines over and over again:
```
[ 5903.808090] usb 5-2: USB disconnect, device number 72
[ 5903.846192] ehci-pci 0000:00:1d.7: port 4 reset error -110
[ 5904.176081] usb 2-4: new high-speed USB device number 123 using ehci-pci
[ 5904.342243] usb 2-4: New USB device found, idVendor=064e, idProduct=a219
[ 5904.342251] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[ 5904.342256] usb 2-4: Product: 1.3M WebCam
[ 5904.342261] usb 2-4: Manufacturer: Suyin
[ 5904.342266] usb 2-4: SerialNumber: HF1315-S32B-OV01-VA-R02.01.05
```

Also, when I restart my laptop from sleep mode, it spits out the following message about twenty times in the short moment before my lock screen appears:
```
unable to enumerate USB device on port 4
```

Does anyone know what the problem might be? The "USB disconnect" makes me think the webcam's connection wires might have come loose within my laptop by transporting it, but I don't want to open up my laptop when the problem might just as well be a driver regression. I'd appreciate your ideas!

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by gladiool on 2013-06-02
I followed your advice and, sadly, I got the same results on a freshly-downloaded Kubuntu live image. Now, do you think it makes sense to open up my laptop and check for loose wires or is this probably not a problem that I can fix myself?

---

