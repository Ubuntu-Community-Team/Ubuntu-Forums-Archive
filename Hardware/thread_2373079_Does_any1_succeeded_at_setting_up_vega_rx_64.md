---
title: "Does any1 succeeded at setting up vega rx 64?"
date: 2017-10-02
forum: Hardware
---

### Post by poornewbie on 2017-10-02
Hello.
Please excuse me for bad English.


I am trying to set up radeon vega rx64 on xubuntu 17.04 with open source driver.
(If I remember correctry, it called
There are two useful articles on phoronix: [one]("https://www.phoronix.com/scan.php?page=article&item=radeon-vega-setup&num=1") and [two]("https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-DC-Ubuntu-Kernel-Next").

However, I still cannot make it work.

I installed Michael's kernel from [here]("https://www.phoronix.net/downloads/drm-next-4.15-dc/linux-image-4.13.0-rc5-phx-drm-next-4.15-dc_4.13.0-rc5-phx-drm-next-4.15-dc-1_amd64.deb"), added Padoka ppa and installed xserver-xorg-video-amdgpu, mesa and llvm-6.0 from there.
As far as I understood, the articles also said that I need firmware from linux-firmware.git, but I cannot understand how to install them.
Should I copy them somewhere or add a kernel parameter with path to firmware folders?

Also, I added amdgpu.dc=1 to the kernel parameters.


So far my results are:
  * I got good resolution (1920x1080). Prior to driver installing there was only 1024x768 aviable.
  * Unigine Superposition cannot run the bencmark, saying that benchmark crashed.
  * ```
$ lsmod | grep -i amd
$
```
  * ```
$ dmesg | grep amd
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-rc5-phx-drm-next-4.15-dc root=UUID=b1726985-50c2-4958-8c2c-def1a7fa860c ro quiet splash nomodeset amdgpu.dc=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-rc5-phx-drm-next-4.15-dc root=UUID=b1726985-50c2-4958-8c2c-def1a7fa860c ro quiet splash nomodeset amdgpu.dc=1
[    1.184603] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[    9.566192] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
```

  * Games are not even running, or suffer from low fps or huge artifacts.

So it seems that driver is now working, but I have no idea what to do (except to install firmwares which I don't know how to install).

---

