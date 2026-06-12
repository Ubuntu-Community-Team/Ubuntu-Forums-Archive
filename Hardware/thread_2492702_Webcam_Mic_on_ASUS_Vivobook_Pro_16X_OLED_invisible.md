---
title: "Webcam Mic on ASUS Vivobook Pro 16X OLED invisible"
date: 2023-11-20
forum: Hardware
---

### Post by Ethan_Arns on 2023-11-20
So I've tried this on kernels 5.15 - 6.5, on both Ubuntu and Linux Mint. Sound output works, video input works, but no built in microphone support. pavucontrol > Input Devices > All Except Monitors shows nothing.
I'm dual booted, the other side being Windows 11, with the built-in webcam mic working and labeled "Microphone Array (AMD Audio Device)."
Here are some common outputs:

```
> lspci | grep Audio
01:00.1 Audio device: NVIDIA Corporation Device 2291 (rev a1)
34:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1640
34:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 60)
34:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
```
(I'm 90% certain the Multimedia Controller is the built-in mic)

```

> arecord -l
**** List of CAPTURE Hardware Devices ****
card 2: Generic_1 [HD-Audio Generic], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
(I'm 99% sure the above listed device is the headphone jack)

---

