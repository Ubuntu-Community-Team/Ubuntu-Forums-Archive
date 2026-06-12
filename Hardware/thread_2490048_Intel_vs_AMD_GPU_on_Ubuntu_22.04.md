---
title: "Intel vs AMD GPU on Ubuntu 22.04"
date: 2023-08-20
forum: Hardware
---

### Post by agentl074 on 2023-08-20
So, I've used Intel and AMD integrated graphics on Ubuntu and Mint, and they both worked fine, but I have yet to use a video card with it. I still have a machine on Windows, but it uses an old XFX AMD Radeon HD7800 video card, and it looks as though it is too old for the amdgpu kernel driver -- and will use the old Radeon driver which isn't as good. 

So, I was thinking about going for the XFX AMD Radeon RX580 since I heard that works pretty well with Ubuntu 22.04 out of the box. What do you guys use with regard to video cards and Ubuntu 22.04?

---

### Post by TheFu on 2023-08-21
Intel discrete GPUs are very new.  If it were me, I wouldn't seek them out.  LTT did a review of early versions of those and he wasn't impressed.  The iGPUs seem fine for non-gamers or video editors.  A laptop I used for a few years with an 8th gen Core i5 worked well enough, until I asked it to do video editing.  The iGPUs are mainly for servers and office productivity workers - think spreadsheets, documents, presentations to bore everyone or software developers who aren't working on games.

I had a low-end nVidia 1030 GPU from pre-COVID before the cray prices happened and the price nearly doubled, even on that GPU.  Anyway, the iGPU in a Ryzen 5 5600G is faster than that nvidia, so just because it is an iGPU, that doesn't mean it can't do some stuff a little over what we'd expect.  Depending on the other parts in your rig, it might make sense to get a faster Ryzen with an on-board GPU.  When I did it, it was $120 for the new Ryzen, including the fast iGPU and I didn't have to change anything else. It was just a CPU swap to get 40% more CPU performance, with better GPU driver support, faster GPU work, and lower overall power consumption.

Here's the new iGPU:
```
$ inxi -Gxx
Graphics:
  Device-1: AMD vendor: ASUSTeK driver: amdgpu v: kernel 
  bus ID: 09:00.0 chip ID: 1002:1638 
  Display: x11 server: X.Org 1.20.13 driver: **amdgpu**,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1200~60Hz 
  OpenGL: 
  renderer: AMD RENOIR (DRM 3.42.0 **5.15**.0-79-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6 direct render: Yes 
```

What you hope to accomplish with the system and new GPU?  New for the sake of new isn't a good idea, unless it brings you joy and you have the money to waste.
I don't game, but I do video cutting (not content creation). The iGPU is excellent for that need as far as I'm concerned.  I isn't setup to do anything like hardware encoding of video codecs or AI processing. For that, I'd probably need a $300 GPU and why would I pay nearly 3x what the CPU cost for a GPU?  That isn't the sort of work I do.

---

### Post by agentl074 on 2023-08-22
Well, for gaming... talking 5 to 10+ year old games, even my old Intel Core I5 2410M Asus laptop was doing fine under Mint 20.3, but the AMD Ryzen 5 5500U powered Asus laptop under Ubuntu 22.04 LTS was actually comparable to my Windows 10 desktop using an XFX AMD Radeon R7800 series! This was using the standard HDMI output (not DP or DVI). 

This said, I was more interested in the visual quality differences people were seeing rather than performance. In this regard, my experience was the Intel's open source video drivers resulted in smoother visual quality than the AMDgpu open source driver -- at least, with the Radeon 5500U integrated graphics.

Integrated graphics today (especially within the past couple of years are no joke at all) comparable to a decent video card from 5-7 years ago -- which is saying a lot! This said, I would like a dedicated video card, but I was unsure about the visual quality of the open source AMDgpu compared to the Intel kernel baked drivers for video cards.

---

