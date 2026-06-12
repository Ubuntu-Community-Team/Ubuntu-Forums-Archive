---
title: "AMDGPU not working anymore on 18.10"
date: 2018-11-17
forum: Hardware
---

### Post by notone2 on 2018-11-17
Hello,

I have hybrid graphics
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / R7 M520] [1002:6660]

```

Drivers for AMD were working fine until 18.04 update, and now when I go to "additional drivers" there are none (there used to be nvidia drivers before 18.04)

I tried installing amdgpu and amdgpu-pro but I get
```
WARNING: amdgpu dkms failed for running kernel
```

Tried installing and reinstalling ```
apt install amdgpu-dkms libdrm-amdgpu-amdgpu1 libdrm-amdgpu1 libdrm2-amdgpu
``` but they are already installed and nothing changes.

---

### Post by notone2 on 2018-11-18
also tried adding *ppa:graphics-drivers/ppa*, but *ubuntu-drivers devices* gave no output, and *sudo ubuntu-drivers autoinstall* said there are no drivers, I tried installing *sudo apt install nvidia-390* but no joy

purged all nvidia files, and added *ppa: oibaf/graphics-drivers*, again found no drivers and still can't see any additional drivers,
but at least now in setting shows boths cards
 [ATTACH=CONFIG]281683[/ATTACH]

but when I tried PRIMING it, it shows like it primed it succesfully but when I check again, Intel card is still in use

```
notone@fieldless:~$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x64 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 2 associated providers: 1 name:modesetting
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:HAINAN @ pci:0000:03:00.0
notone@fieldless:~$ xrandr --setprovideroffloadsink 1 0
notone@fieldless:~$ DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: AMD HAINAN (DRM 2.50.0, 4.18.0-12-generic, LLVM 7.0.1)
notone@fieldless:~$ glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile
```

Only thing I didn't tried installing is
[https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-8000m-series/amd-radeon-hd-8670m-series-gpu](https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-8000m-series/amd-radeon-hd-8670m-series-gpu)
but not sure if I want to do that, any help please?

---

### Post by Yellow Pasque on 2018-11-18
Your glxinfo and "DRI_PRIME=1 glxinfo" looks good, so what exactly is your issue? Are programs not running as expected? If so, give more detail. My advice would be not to use proprietary amdgpu-pro drivers unless you are an enterprise/workstation user sticking to LTS ubuntu releases. That does not appear to be you.

> I tried installing sudo apt install nvidia-390
You don't have an nvidia GPU, so that doesn't make sense.

---

### Post by QIII on 2018-11-18
Hello!

I use the AMDGPU-PRO overlay to AMDGPU ***only*** to run distributed GPGPU computing projects that require it.  I agree that for the vast majority of people, AMDGPU-PRO is of little value -- or maybe even more trouble than help.

Besides that, since AMDGPU-PRO is an overlay to the open source AMDGPU driver that is installed with Ubuntu on machines that it supports, if the latter does not work the former won't either.

I believe your problem lies with the hybrid graphics arrangement your machines uses.  I'm not sure that AMD and Intel play well together in the AMDGPU era.  It was difficult enough during the fglrx era.

I would suggest that you see if your BIOS/EFI allows you to bypass the integrated Intel graphics and use the dedicated AMD GPU.  This will only work if the system is muxless -- that is that the graphics are not multiplexed through the Intel chip.  Most systems are now muxless, but that is not universal.

---

### Post by notone2 on 2018-11-22
thanks for the answers, and sorry for the late answer

i'm still struggling with linux and most of the time i'm following instructions and probably at least 50% not sure what i'm doing

generally, before 18.04, i had two sets of drivers in "additional drivers" and most of the steam games were running smoothly, now i can't start 80% of the games, and some i can are really slow, so i guessed the drivers were not doing what they suppose to

can I somehow check when is the system using what gpu and are they doing what they should do?

also i don't know is this help but i get software updates that i can't check and mark for installation
[[IMG]https://image.ibb.co/eRpJZq/2018-11-22-21-29.png[/IMG]]("https://imgbb.com/")

---

### Post by Yellow Pasque on 2018-11-23
If you want a Steam game to use the AMD GPu, add this to its launch options:
```
DRI_PRIME=1 %command%
```

There may be an option in Steam to do this universally for every game. I don't use Steam Linux, so I don't remember.

---

