---
title: "AMDGPU-Pro not working"
date: 2017-02-20
forum: Hardware
---

### Post by amivaleo on 2017-02-20
Hi guys,

Today I discovered the existence of the AMDGPU-Pro driver, compatible with Ubuntu 16.04. I use Gnome-Ubuntu 16.04.

I have got a notebook which has an Intel GPU and a dedicated Radeon **HD8530M** GPU:
```
$ lspci | grep -E 'VGA'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars LE [Radeon HD 8530M / R5 M240] (rev ff)
```
The Radeon GPU model is also in the specs given by the manufacturer: [https://www.asus.com/Notebooks/ASUS_VivoBook_S301LP/specifications/](https://www.asus.com/Notebooks/ASUS_VivoBook_S301LP/specifications/)


On AMD site ( [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx) ), I read that my GPU is compatible with the driver **AMDGPU-Pro version 16.60**.
I downloaded it, I installed it as the guide says, but after the reboot my pc doesn't load any graphical interface. It keeps showing several command lines in fullscreen, and the screen blinks as you can see from this short video I made: [https://vid.me/30Ve](https://vid.me/30Ve)

Do you have any idea about the reason for this malfunction? Is it a bug of the driver? Help me, please... ._.

---

### Post by QIII on 2017-02-20
Hello!

Which kernel are you running in 16.04?

---

### Post by amivaleo on 2017-02-20
```
$ uname -r
4.4.0-63-generic
```

Is this the problem?

---

### Post by QIII on 2017-02-20
You have two problems:

1.  I could not get AMDGPU-PRO to work on 16.04 without upgrading the kernel to 4.8.

2.  Your GPU's architecture is Graphics Core Next (GCN) 1.0.  While support for GCN 1.0 and 1.1 is coming, the AMDGPU-PRO driver presently works without fail on GCN 1.2 and later GPUs.

Even if you upgrade your kernel, it is not likely that your GPU will work with the AMDGPU-PRO driver for the moment.  You'll have to wait for further updates.

---

### Post by amivaleo on 2017-02-20
Where can I find these info you wrote in the second point?
I don't understand why they write that the driver is compatible with my gpu when it's not. Also, I would like to read somewhere that the kernel 4.8 is needed in the AMD page I linked in the first post. :/
No more AMD GPUs for me for the rest of my life, that's sure.

---

### Post by QIII on 2017-02-20
I wouldn't write off AMD GPUs.  AMD is doing exactly what the Linux community has been asking for for years:  Creating a truly functional open-source driver.  AMDGPU is the open source version.  AMDGPU-Pro is AMDGPU with a proprietary overlay.  Let me express that a different way:  AMD's proprietary drive is based on its open source driver.  That is standing the whole driver world on its head.  What you are encountering right now is nothing more than road construction.  In the end, nobody will hold a candle to AMD support for Linux.

Why do I say kernel 4.8?  Lots of experimentation.

AMD's list of compatible GPUs for 16.04 is [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx").


I've done a bunch of research to find out what GPUs are GCN 1.0 or greater, and have a list [here]("http://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").

You might ask "Why GCN 1.0 and later?  Why not earlier GPUs?"  The answer is simply that prior GPUs physical architecture is not compatible with AMDGPU.

Another important point to note is that AMDGPU-PRO supports Vulkan, which is itself a recent development.

---

### Post by amivaleo on 2017-02-20
What they're doing is surely something we all should be thankful for. On the other hand, I've never really had the chance to use my dedicated GPU so far. It is something I paid for... Less than 2 years ago, I decided to buy this notebook also because I read that its radeon GPU was supported by fglrx driver. Unfortunately, the support for the driver was dropped in just a few months when ubuntu 16.04 came (I bought my laptop in October 2015).
This issue with the dedicated GPU was not even the only I have had with this stupid laptop. It looks like that I trusted the review of the wrong guy when I decided to buy it.

> **QIII said:**
> AMD's list of compatible GPUs for 16.04 is [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx").
That page leads to the version 16.40 of the driver. The version I linked in the first post is the 16.60, and this should be compatible with my GPU. I'll give it a try. I've just updated my kernel to 4.8. Maybe I'll be lucky!

> **QIII said:**
> I've done a bunch of research to find out what GPUs are GCN 1.0 or greater, and have a list [here]("http://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").
I can't find mine! :lolflag:

Thank you for your help, I really appreciate it. :)

Edit:
You were right... The driver doesn't work, not even the 16.60 version.
I open a thread in the AMD official forum.

---

