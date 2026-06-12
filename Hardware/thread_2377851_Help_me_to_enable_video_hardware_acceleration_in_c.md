---
title: "Help me to enable video hardware acceleration in chromium on AMD/ATI card"
date: 2017-11-17
forum: Hardware
---

### Post by digitalone2 on 2017-11-17
Hello. I have a laptop with an ATI VGA, Radeon open source driver and Arch Linux. I installed this package: 
[https://aur.archlinux.org/packages/chromium-vaapi/and](https://aur.archlinux.org/packages/chromium-vaapi/and) 
and hardware acceleration works fine in chromium.

Then I have another laptop with another ATI VGA, same Radeon open source driver and Lubuntu 16.04 LTS. 
chromium-browser does not have hardware acceleration support, by default chromium has not enabled it on Linux. But there's this patch
[https://chromium-review.googlesource.com/c/chromium/src/+/532294](https://chromium-review.googlesource.com/c/chromium/src/+/532294)
that enables VAAPI hardware acceleration inside the browser on Linux.

The package above for Arch Linux works well and I tried to find something similar for Lubuntu. There's this PPA: 
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)
It provides chromium-dev with the same patch.

I installed it, but hardware acceleration does not work.

Could you help me to find the solution?
Maybe it's an issue in libva to get VAAPI working. I could provide tests and logs from terminal if you can collaborate.

Thanks.

---

### Post by TheFu on 2017-11-17
[https://www.unixmen.com/quick-tip-enable-hardware-acceleration-chromium-chrome-browser/](https://www.unixmen.com/quick-tip-enable-hardware-acceleration-chromium-chrome-browser/) - there are some settings inside the browser that need to be enabled.  If you've done that already, IDK.

---

### Post by digitalone2 on 2017-11-17
> **TheFu said:**
> [https://www.unixmen.com/quick-tip-enable-hardware-acceleration-chromium-chrome-browser/](https://www.unixmen.com/quick-tip-enable-hardware-acceleration-chromium-chrome-browser/) - there are some settings inside the browser that need to be enabled.  If you've done that already, IDK.

Yes, already done on Lubuntu, but hardware acceleration won't work.
Did the same on Arch Linux and it works there. 

Should be an issue in libva packages that provides vaapi support, but I can't understand why they work on Arch Linux and not on Lubuntu.

---

### Post by TheFu on 2017-11-17
Don't know.
I stopped using AMD when they dropped support for my radeon CPU.
Works on my iGPU/Intel.

There are lots of possible reasons.

---

### Post by Yellow Pasque on 2017-11-17
What does vainfo show?
```
vainfo
```

---

### Post by digitalone2 on 2017-11-17
> **TheFu said:**
> Don't know.
I stopped using AMD when they dropped support for my radeon CPU.
Works on my iGPU/Intel.

There are lots of possible reasons.
Which reasons?
Hardware acceleration works on Radeon cards. If it works on Arch Linux, there should be a way to get it working on Lubuntu too.
Both systems are installed on the same GPU family. Lubuntu is on Kabini, Arch on Mullins.
According to this: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)
They belong to Sea Island family and "Video Decode (VDPAU/OpenMax/VAAPI) on UVD" is supported.

> **Temüjin said:**
> What does vainfo show?
```
vainfo
```
This is the output on Lubuntu:
```
[FONT=monospace][COLOR=#000000]libva info: VA-API version 0.39.0 [/COLOR]
libva info: va_getDriverName() returns 0 
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so 
libva info: va_openDriver() returns -1
libva info: vaInitialize failed with error code -1 (unknown libva error),exit[/FONT]
```

It seems libva is not implemented in the right way on Lubuntu.

This is the other output on ArchLinux:
```
[FONT=monospace][COLOR=#000000]libva info: VA-API version 1.0.0[/COLOR]
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_0
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.0 (libva 2.0.0)
vainfo: Driver version: mesa gallium vaapi
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSlice
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSlice
      VAProfileNone                   : VAEntrypointVideoProc
[/FONT]
```

VAAPI version on Lubuntu is 0.39.0 while 1.0.0 on Arch Linux.
Is there a way to get it working on 0.39.0?

I can't see now on Lubuntu, but libva on Arch Linux is provided for Radeon driver by "libva-mesa-driver" package, while mesa is the radeon driver package (see here: [https://wiki.archlinux.org/index.php/Hardware_video_acceleration](https://wiki.archlinux.org/index.php/Hardware_video_acceleration)).
Can you tell me which are the relative packages in Lubuntu?

---

### Post by Yellow Pasque on 2017-11-17
mesa-va-drivers

---

### Post by digitalone2 on 2017-11-18
> **Temüjin said:**
> mesa-va-drivers
Great, I missed that package. Don't know why it's not installed by default.
After installation, vainfo output on Lubuntu is similar to the one on Arch Linux.
I'll try to install chromium-dev and see if hardware acceleration works.

---

### Post by digitalone2 on 2017-11-18
Nothing to do, hardware acceleration is still not working.
It's because ubuntu LTS uses old ATI drivers and hardware video decode is disabled on chromium, even if the patch is enabled.
It works on Arch because it's a rolling release and has latest drivers. 
That's very sad. :(

---

### Post by TheFu on 2017-11-18
**New is the enemy of stable.**

LTS users want stability over all else.  We don't want API changes.  We don't want unproven software.  Business and many home users don't want surprises. The system they installed in 2016 should work the same in 2017, 2018, 2019, ...  The only way to ensure this is to NOT push newer versions of libraries or programs.  We do want fixes, but not new versions.

RHEL 6 is on a 2.6 kernel still.

Everyone has slightly different needs and the LTS releases fits a specific requirement.

---

### Post by Yellow Pasque on 2017-11-18
> **digitalone2 said:**
> Nothing to do, hardware acceleration is still not working.
It's because ubuntu LTS uses old ATI drivers and hardware video decode is disabled on chromium, even if the patch is enabled.
It works on Arch because it's a rolling release and has latest drivers. 
That's very sad. :(

There are ways to upgrade to later graphics drivers. 
Official way: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) (and [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack) for more technical detail)
Or use an unofficial PPA, like: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

---

### Post by digitalone2 on 2017-11-18
> **TheFu said:**
> **New is the enemy of stable.**

LTS users want stability over all else.  We don't want API changes.  We don't want unproven software.  Business and many home users don't want surprises. The system they installed in 2016 should work the same in 2017, 2018, 2019, ...  The only way to ensure this is to NOT push newer versions of libraries or programs.  We do want fixes, but not new versions.

RHEL 6 is on a 2.6 kernel still.

Everyone has slightly different needs and the LTS releases fits a specific requirement.
I know, this is the reason I installed an LTS on the other laptop because it's not for me, but for my brother. I use Arch Linux. 

But he watches some videos on YouTube and hardware acceleration gives the system a light load on CPU resources. 

> **Temüjin said:**
> There are ways to upgrade to later graphics drivers. 
Official way: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) (and [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack) for more technical detail)
Or use an unofficial PPA, like: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)
Thanks, I will give it a try.

---

### Post by digitalone2 on 2017-11-19
Installed this: [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates)
And this: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

Enabled "Override software rendering list", "Hardware-accelerated video" and "Hardware-accelerated mjpeg decode for captured frame" from chrome://flags

Installed h264ify extension. Rebooted chromium. 
chrome://gpu/ shows "Video Decode: Hardware accelerated".

During Youtube playback, chrome://media-internals shows "GpuVideoDecoder".

Thanks.

---

