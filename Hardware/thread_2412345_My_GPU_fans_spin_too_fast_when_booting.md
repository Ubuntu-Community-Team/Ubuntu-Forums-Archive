---
title: "My GPU fans spin too fast when booting"
date: 2019-02-11
forum: Hardware
---

### Post by ash22 on 2019-02-11
When my computer boots up it freezes for a moment and shows a glitch screen and then the fans speed up on maximum speed. It used to be fine before but has just started doing it out ov nowhere. It doesn't happen when I boot into Windows, only Ubuntu Mate even when it's a live CD. My GPU is the AMD Radeon R9 300 series. I would upload a video but I don't know where to post it to.

---

### Post by aljames2 on 2019-02-11
You'll likely need to use an AMD Open Source driver for Ubuntu to get that card working properly.  There is [AMDGPU]("https://help.ubuntu.com/community/AMDGPU-Driver") & [RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") projects depending on the card you have.

---

### Post by ash22 on 2019-02-12
> **aljames2 said:**
> You'll likely need to use an AMD Open Source driver for Ubuntu to get that card working properly.  There is [AMDGPU]("https://help.ubuntu.com/community/AMDGPU-Driver") & [RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") projects depending on the card you have.

I alreddy have amdgpu and I've even reinstalled it but when I serch amdgpu on Synaptic, it has two results for the drivers. One is Xserver-xorg-video-amdgpu which I have installed and the other one Xserver-xorg-video-amdgpu-hwe-18.04. Which one am I supposed to use? They both say they work with the card I've got (Tonga). When I try to install the other one I just get a message that says "could not apply changes! Fix broken packages first".

---

### Post by him610 on 2019-02-12
Should fix broken packages...
```

sudo apt-get update
sudo apt-get install -f
sudo apt-get purge

```
After fix, consider installing AMD GFX drivers using Settings>Additional Drivers

---

### Post by ash22 on 2019-02-12
I still got the error and there weren't any additional drivers to install in the settings

---

### Post by him610 on 2019-02-12
Please post results of *inxi -G* between code tags

---

### Post by ash22 on 2019-02-12
This is the output ```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa,radeon)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD Radeon R9 380 Series (TONGA, DRM 3.23.0, 4.15.0-45-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.2.2


```

---

