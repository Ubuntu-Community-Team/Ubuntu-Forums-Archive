---
title: "Installing two GPU's"
date: 2017-11-28
forum: Hardware
---

### Post by superstalker on 2017-11-28
Hi,

I currently have the following video cards installed on my computer. [UBUNTU 16.04]

lspci -nn | grep -E 'VGA|Display'
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360] [1002:6658]
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360] [1002:6658]
```

I have installed the drivers for these video cards. However only one of the video cards have the driver installed.

dpkg -l amdgpu-pro
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.40-492261 amd64        Meta package to install amdgpu Pr
```

I use four screens, two attached per video card. One outputs everything perfectly, the other one gives me RGB bars all over the screen. I can see the cursor moving on the screen, but anything else I can't see.

How do I install the second one?


Thank you in advance,
W. Roelofs

PS: How do I enable en disable crossfire? (It worked in windows).

---

### Post by Yellow Pasque on 2017-11-28
Re: crossfire
[https://phoronix.com/scan.php?page=news_item&px=AMD-CrossFire-mGPU](https://phoronix.com/scan.php?page=news_item&px=AMD-CrossFire-mGPU)

---

### Post by superstalker on 2017-11-28
So... crossfire isn't a thing anymore. Now it's called mGPU, and it's only possible for games to activate it...?

---

### Post by superstalker on 2017-11-28
Okay, I feel like [this]("https://ubuntuforums.org/showthread.php?t=2377454") thread is about the same problem. But I literally don't understand what solution he has in mind or what the problem is that he's facing. Could someone explain it to me?

---

### Post by Yellow Pasque on 2017-11-28
> **superstalker said:**
> Okay, I feel like [this]("https://ubuntuforums.org/showthread.php?t=2377454") thread is about the same problem. But I literally don't understand what solution he has in mind or what the problem is that he's facing. Could someone explain it to me?

It's not relevant unless you use sddm as opposed to the default lightdm.

---

### Post by superstalker on 2017-11-29
So, I've been looking around and found out that most problems lie within a file named 
```
/etc/X11/xorg.conf
```

However I don't have that file. Plus I don't know if this has something to do with the old and new drivers. A lot of solutions lie within the old driver enviroment.

---

### Post by superstalker on 2017-12-02
Update: I've decided to try and install Ubuntu 17.04. Great news, all my screens work!... But... I installed amdgpu-pro and got the same result...

---

### Post by Yellow Pasque on 2017-12-02
> **superstalker said:**
> But... I installed amdgpu-pro and got the same result...

Patient: "Doctor, it hurts when I do this."
Doctor: "Don't do that."

But seriously, is there a reason you need the pro driver? A lot of people coming from Windows assume they need to install the proprietary driver, and it is useful in certain cases (cpryptocurrency mining, OpenCL workloads), but for gaming and general desktop use, the open source driver is usually a better choice.

> I've decided to try and install Ubuntu 17.04
It's going to be EOL in two months..

---

### Post by QIII on 2017-12-02
I use AMDGPU and AMDGPU-PRO pretty much only because they are needed for @home projects I do.  Some games require it.

Phoronix has done several articles that show the Radeon driver plus the MESA package actually perform BETTER than AMDGPU/PRO in almost all the cases that most people will be interested in.  

Unless you are doing scientific computing or specific games, AMDGPU at present may not do you any good.  If you don't absolutely need it, you'd be better off not using it quite honestly.

---

### Post by superstalker on 2017-12-05
The reason I am not using the proprietary driver is because:
 1. Because I'm a former Windows user: For all drivers, go to the manufacturer's website and keep your drivers up to date.
 2. Because I get tearing accros the screen.
 3. Because I'm a former Windows user: For all drivers, go to the manufacturer's website and keep your drivers up to date.
 4. Because I'm worried the drivers can't handle games.
 5. Because I'm a former Windows user: For all drivers, go to the manufacturer's website and keep your drivers up to date.


Anyway, maybe this can help?

```
cat /var/log/Xorg.0.log |grep Driver

[     4.966]     X.Org Video Driver: 23.0
[     5.114]     Module class: X.Org Video Driver
[     5.114]     ABI class: X.Org Video Driver, version 23.0
[     5.115]     Module class: X.Org Video Driver
[     5.115]     ABI class: X.Org Video Driver, version 23.0
[     5.244]     Module class: X.Org Video Driver
[     5.244]     ABI class: X.Org Video Driver, version 23.0
[     5.245]     Module class: X.Org Video Driver
[     5.245]     ABI class: X.Org Video Driver, version 23.0
[     5.245]     Module class: X.Org Video Driver
[     5.245]     ABI class: X.Org Video Driver, version 23.0
[     5.245]     Module class: X.Org Video Driver
[     5.245]     ABI class: X.Org Video Driver, version 23.0
[     5.245] (II) AMDGPU: Driver for AMD Radeon:
[     5.245] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
[     5.246] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.258]     ABI class: X.Org Video Driver, version 23.0
[     5.709]     Module class: X.Org XInput Driver
```

---

### Post by superstalker on 2017-12-05
From articles I got the understanding that current opensource drivers weren't up to par and out of date. But in that case I'm uninstalling the darn thing.

---

