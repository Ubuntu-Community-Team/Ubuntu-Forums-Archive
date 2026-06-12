---
title: "Supporting 2013 GPU hardware on latest LTS ?"
date: 2017-11-21
forum: Hardware
---

### Post by zanzibarwinds2 on 2017-11-21
Hi

I got a brand new install of Ubuntu on a 2013 desktop and was wondering if there would be any benefit to me attempting to get drivers installed for the GPU that was in it. The monitor is currently plugged into the Intel board but there is a Radeon card in the PC as well.

IF no benefit then I'll just forget it but I was hoping that I could get some benefit (*Like scaling which I don't currently have and screen image seems to be clipped at the bottom*) since the card was there already, if the drivers are stil supported of course.

**lspci -nn | grep -E 'VGA|Display'** result
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos XTX [Radeon HD 8490 / R5 235X OEM] [1002:6771]

```

**Ubuntu version info**

```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

```

---

### Post by Yellow Pasque on 2017-11-21
EDIT: Nevermind. I thought this was a laptop. Sorry for noise.

---

### Post by mastablasta on 2017-11-22
AMD uses opensource drivers now (Radeon, AMDGPU) and for some chips closed add on called AMDGPU-PRO. this means the drivers are already installed (they might need enabling) since in linux, the  drivers are part of kernel. 

carefully read: [https://askubuntu.com/questions/791249/amd-intel-hybrid-graphics-on-ubuntu-16-04](https://askubuntu.com/questions/791249/amd-intel-hybrid-graphics-on-ubuntu-16-04)
and: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) [avoid fglrx if possible. if not, then you need 14.04 LTS (the original one) and work from there. that release is still supported but only until 2019.]

we don't know what OS you have installed. but ubuntu 17.10 has latest kernel as does the point release of 16.04 LTS if HWE stack is used.


yes, you would benefit from using the AMD chip. but then again it also depends what the usage is. if you are only doing office work or media playing or internet browsing, then intel will do just fine, otherwise AMD should outperform it.

---

