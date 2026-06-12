---
title: "AMD Radeon R9 380 dual monitor needs to unplug dvi"
date: 2018-01-30
forum: Hardware
---

### Post by RobertLos on 2018-01-30
Hi,

please advise on the following:

Further to post  [https://ubuntuforums.org/showthread.php?t=2327625](https://ubuntuforums.org/showthread.php?t=2327625) I have the same problem that the monitor connected to the DVI device is only working when after a minute I physically unplug the monitor and replug it again. Than it detects and switches the second dual monitor on. Otherwise the monitor remains black, but seems to be detected because windows will be placed there (but are not visible).

The following commands lead to the following output:

[FONT=Courier New]$ lsmod | grep amdgpu
amdgpu               2019328  70
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
drm_kms_helper        167936  1 amdgpu
drm                   356352  7 amdgpu,ttm,drm_kms_helper[/FONT]

[FONT=Courier New]$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tonga PRO [Radeon R9 285/380] [1002:6939] (rev f1)[/FONT]

[FONT=Courier New]$ xrandr --listmonitors
Monitors: 2
 0: +*HDMI-A-0 1920/521x1080/293+1920+42  HDMI-A-0
 1: +DVI-I-1 1920/521x1080/293+0+0  DVI-I-1[/FONT]

I installed the latest AMDGPU-PRO driver (amdgpu-pro-17.40-492261.tar.xz)

The monitor works perfectly OK using windows 10 or during grub

I am using Ubuntu 16.04.03-LTS with kernel 4.13.0-32-generic

please advise

---

