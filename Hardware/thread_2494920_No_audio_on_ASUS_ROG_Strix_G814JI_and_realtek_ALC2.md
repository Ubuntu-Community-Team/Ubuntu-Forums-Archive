---
title: "No audio on ASUS ROG Strix G814JI and realtek ALC294"
date: 2024-01-31
forum: Hardware
---

### Post by maksam07 on 2024-01-31
Hi. I have experience with a new 2023 gaming laptop - ASUS ROG Strix G814JI 
Full model name: ASUS ROG Strix G18 G814JI-N6062

I need the laptop more for work than for gaming, but still plan on installing two OS: Windows and linux.
At first I installed Windows 10, but it turns out the laptop doesn't have full support for it and there was no sound there either. When I installed Windows 11, then with all its updates the sound appeared by itself and I did not put any additional drivers. That is, everything works correctly on Windows 11.

And so when I got to linux (ubuntu, kubuntu) (22, 23 versions), nowhere could I get working sound from the speakers. There is sound in the headphones! But the speakers don't work. I searched a lot of information on the internet, but I could not get the sound to produce anything from the speakers. 

If you can, please advise what options you can take, I will try just about anything I can and what I can with my knowledge, but would like to get sound out of the laptop speakers.

I'm using live-usb for tests right now, I haven't installed an OS on the laptop.


Here's some information:
```

ubuntu@ubuntu:~$ inxi -SMAG
System:
  Host: ubuntu Kernel: 6.5.0-9-generic arch: x86_64 bits: 64 Desktop: GNOME
    v: 45.0 Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Laptop System: ASUSTeK product: ROG Strix G814JI_G814JI v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: G814JI v: 1.0 serial: <superuser required>
    UEFI: American Megatrends LLC. v: G814JI.321 date: 10/24/2023
Graphics:
  Device-1: Intel Raptor Lake-S UHD Graphics driver: i915 v: kernel
  Device-2: NVIDIA AD106M [GeForce RTX 4070 Max-Q / Mobile] driver: N/A
  Device-3: Sonix USB2.0 HD UVC WebCam driver: uvcvideo type: USB
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: iris gpu: i915
    resolution: 2560x1600~240Hz
  API: OpenGL v: 4.6 Mesa 23.2.1-1ubuntu3 renderer: Mesa Intel Graphics
    (RPL-S)
Audio:
  Device-1: Intel driver: snd_hda_intel
  Device-2: NVIDIA driver: snd_hda_intel
  API: ALSA v: k6.5.0-9-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active

```

```

ubuntu@ubuntu:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x625f230000 irq 209
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0x87080000 irq 17

```

```

ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Yellow Pasque on 2024-01-31
Support wasn't added until kernel 6.7: [https://github.com/torvalds/linux/commit/a40ce9f4bdbebfbf55fdd83a5284fbaaf222f0b9](https://github.com/torvalds/linux/commit/a40ce9f4bdbebfbf55fdd83a5284fbaaf222f0b9)

---

### Post by maksam07 on 2024-01-31
> **Yellow Pasque said:**
> Support wasn't added until kernel 6.7: [https://github.com/torvalds/linux/commit/a40ce9f4bdbebfbf55fdd83a5284fbaaf222f0b9](https://github.com/torvalds/linux/commit/a40ce9f4bdbebfbf55fdd83a5284fbaaf222f0b9)

Does that mean I need to put a kernel of at least 6.8.*? or 6.7.*?

---

### Post by Yellow Pasque on 2024-01-31
The change was added in 6.7-rc7, so if you want to try it:
[https://kernel.ubuntu.com/mainline/v6.7.2/](https://kernel.ubuntu.com/mainline/v6.7.2/)

You may need to turn off SecureBoot or find some way to sign the kernel. I don't know. Don't ask me about SecureBoot. All I know is that I disable it when possible because it causes more real problems than it theoretically solves IMO.

---

### Post by b-boarder on 2024-02-06
Hello!

Unfortunately I cannot help you with the sound-problem.
But since I am thinking about buying the device, I just want to ask you, to give some information on how Linux is running on the Rog Strix G814JI. Are there any other problems?

Thanks in advance!

---

