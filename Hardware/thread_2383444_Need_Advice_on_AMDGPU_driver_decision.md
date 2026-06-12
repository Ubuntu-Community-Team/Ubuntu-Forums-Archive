---
title: "Need Advice on AMDGPU driver decision"
date: 2018-01-25
forum: Hardware
---

### Post by cloudkos on 2018-01-25
Hello there to all , 
I got an AMD A8 7600 CPU (Kaveri APU) 

```
lspci -k | grep -EA3 'VGA|3D|Display' 
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Kaveri [Radeon R7 Graphics]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu

```

Ubuntu Version : Desktop 16.04.3 LTS

I want to use better graphics since i am getting some graphic lags with chrome latest and generally better performance but i am lost in the tutorials .

What can i use ? AMDGPU or AMDGPU-pro ?  
I tried to blacklist the radeon driver and use amdgpu instead but i failed with like 4 -5 different techniques .

Thanks a lot in advance.

---

### Post by cloudkos on 2018-01-25
Hello there to all , 
I got an AMD A8 7600 CPU (Kaveri APU) 

```
lspci -k | grep -EA3 'VGA|3D|Display' 
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Kaveri [Radeon R7 Graphics]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu

```
Ubuntu Version : Desktop 16.04.3 LTS


I want to use better graphics since i am getting some graphic lags with chrome latest and generally better performance but i am lost in the tutorials .


What can i use ? AMDGPU or AMDGPU-pro ? 
I tried to blacklist the radeon driver and use amdgpu instead but i failed with like 4 -5 different techniques .


Thanks a lot in advance.

---

### Post by QIII on 2018-01-25
When you installed, amdgpu would have been used if the version of amdgpu available at the time of the Ubuntu release supported your hardware.  Otherwise radeon would have been used.  If you try to install amdgpu on an Ubuntu release that does not contain the appropriate driver, attempting to install it will fail.

Would you please post the output of

```
lsmod | grep radeon 
```

and

```
lsmod | grep amdgpu 
```

---

### Post by sparkzer56 on 2018-02-01
In all honesty, if you want more performance, you NEED to upgrade your kernel, and upgrade to the Oibaf ppa. I've literally had nothing but black screens on anything below Linux Kernel 4.15. Once I upgraded i've had no issues at all other than the wifi driver doesn't work with it, So i'm stuck with either ethernet, or tethering my phone to my laptop.

---

### Post by coffeecat on 2018-02-01
@cloudkos, I've merged your two separate threads that you started in different sections of the forum, and moved the merged thread to the Hardware sub-forum.

Please do not post duplicates; this dilutes community support.

---

### Post by kirenpillay1 on 2018-02-12
I've had 16.04 Gnome Edition on my AM1 5150 APU, and HD Video was tearing and lacked smoothness (Netflix and Youtube). I tried to download the latest ATI drivers but couldn't install them. 

I then downgraded to 14.04 LTS, and the result is really great. The pictures are smoother, with no lag, and that's with the stock-standard Radeon driver. I'm not going to bother installing the Catalyst drivers, I'm happy with this setup.

---

