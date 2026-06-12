---
title: "Driver for Radeon R4/R5 Graphics in Ubuntu 17.10"
date: 2018-03-31
forum: Hardware
---

### Post by donmatas on 2018-03-31
Hi,

I have a laptop HP Pavilion 15. I am running with Ubuntu 17.10 (16.04 does not work properly). Regrettably, the GPU is not working as it should (it blinks randomly). Its card is a Radeon R4/R5 Graphics: 

```
$ lspci |grep ati
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05)
```

Several posts say that the privative driver only works with 16.04. Does anyone have a solution?

---

### Post by QIII on 2018-04-01
Hello!

It's not that AMDGPU and AMDGPU-PRO (the "private driver" you are talking about) only work with 16.04 (that is when they *started* supporting Ubuntu), but a matter of which GPUs are supported by AMDGPU.

I don't know that all R4 and R5 series GPUs are supported by AMDGPU.  Some of the R5s on some of the Kaveri APUs are.

Would you please post the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```

That will tell us which driver module is loaded -- that is, which was installed by default when you installed Ubuntu.

If an AMDGPU supported GPU is present at install time, Ubuntu installs the AMDGPU driver.

---

### Post by donmatas on 2018-04-01
> **QIII said:**
> Hello!

Would you please post the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```



Sure!
```

$ lsmod | grep radeon
radeon               1478656  26
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        167936  2 amdgpu,radeon
drm                   360448  28 amdgpu,radeon,ttm,drm_kms_helper
```

```
$ lsmod | grep amdgpu
amdgpu               2019328  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        167936  2 amdgpu,radeon
drm                   360448  28 amdgpu,radeon,ttm,drm_kms_helper
```

Thank you very much!!!

---

### Post by QIII on 2018-04-01
The amdgpu module is loaded.

Does this machine have both integrated and dedicated graphics?

Would you post the results of 

```
lspci | grep VGA 
```

---

### Post by Yellow Pasque on 2018-04-02
> **QIII said:**
> Would you post the results of 
```
lspci | grep VGA 
```

You should probably read this: [https://superuser.com/a/1215760](https://superuser.com/a/1215760)
I see non "VGA Controller" PCI class most often with hybrid graphics and servers with dedicated 3D units that aren't connected to displays.

---

### Post by QIII on 2018-04-02
Yet another valuable trinket for my kitbag!

Thanks.

---

### Post by donmatas on 2018-04-02
> **QIII said:**
> 
Would you post the results of 

```
lspci | grep VGA 
```


```
$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05)
```

Thanks!

---

### Post by QIII on 2018-04-03
Thanks!  Did you see Temüjin's post?

---

### Post by donmatas on 2018-04-03
> **QIII said:**
> Thanks!  Did you see Temüjin's post?

I did, but it does not have sense for me. Perhaps because I am not a super user but a simple user... jajajaja

In any case, here is the output of the command:

```
$ lspci -nn | grep '\[03'
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05)
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445] [1002:6900] (rev ff)
```

---

### Post by QIII on 2018-04-03
So, Temüjin's suggestion netted us a very important bit of information.  You have what AMD calls "Dual Graphics":  That is, two AMD graphics units.  One is the R4/5, the other an R7.

The R7 is a dedicated GPU while the R4/5 is integrated on the APU die.

The best performance will come from the R7, but that will cost you in battery life.  The best battery life will come from the R4/5, but the performance will not be as good.

Which concerns you most:  Performance or battery life?

(By the way, some time ago I researched what appeared at the time to be a list of GPUs for which the AMDGPU was working or would soon be.  You can have a look at it in [this blog article]("https://theleftcoastgeek.net/index.php/hardware/12-possible-amdgpu-pro-supported-gpus-by-the-end").  A lot has changed, but that was pretty good at the time.)

---

### Post by Yellow Pasque on 2018-04-04
First of all, the proprietary AMD driver (amdgpu-pro) does not support the Mullins core found in the APU. So that option is out. Dead end there.

> The best performance will come from the R7, but that will cost you in battery life. The best battery life will come from the R4/5, but the performance will not be as good. Which concerns you most: Performance or battery life?
I think you're going off on a tangent there. Since the OP seems unaware of the hybrid graphics, I doubt s/he's using DRI_PRIME or is unsatisfied with the performance of the integrated graphics. The concern seems to be a bug with the integrated graphics.
I'd suggest trying a LiveUSB of 18.04 (if one is not comfortable installing mainline kernel) to see if it's been fixed. Another option is to force amdgpu kernel module to see if that makes a difference. Speaking of that...

> some time ago I researched what appeared at the time to be a list of GPUs for which the AMDGPU was working or would soon be.

The Mullins integrated chip is GCN 1.1. The discrete Topaz GPU is GCN 1.0. You can try running them on the open source amdgpu module, but I think support is still considered experimental. You need to boot with some extra parameters to try that: ```
amdgpu.si_support=1 radeon.si_support=0 amdgpu.cik_support=1 radeon.cik_support=0
```

---

### Post by donmatas on 2018-04-04
> **QIII said:**
> 

Which concerns you most:  Performance or battery life?



Thank you very much QIII!

What I need is a normal performance of the GPU. I do not use video games but I do watch movies (video files and via web streaming services like Netflix) but the screen blinks when I try to use those tools. 

I do not know which GPU (r4/5 or r7) is being used. If is r4/5, it seems that I should switch to r7. If is r7, I should do something else. In any case, what and how should I do it?

Thanks!

---

### Post by Yellow Pasque on 2018-04-07
>  I do not use video games but I do watch movies (video files and via web streaming services like Netflix) but the screen blinks when I try to use those tools. 

What program are y ou trying to use? Are you tring to use a web browser? Accelerated video decode does't work in a web browser.

>  it seems that I should switch to r7. If is r7, I should do something else.

I don't think it will make a difference. Both GPU's have similar capabilities for video decoding: [https://www.x.org/wiki/RadeonFeature/#index8h2](https://www.x.org/wiki/RadeonFeature/#index8h2)
If you're trying to watch H.264 4k, switching may help. You use DRI_PRIME like this (using mpv as example):
```
DRI_PRIME=1 mpv filename
```

Make sure PRIME is set up correctly:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

---

