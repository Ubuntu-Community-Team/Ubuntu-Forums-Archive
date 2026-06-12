---
title: "BadWindow (invalid window parameter)"
date: 2011-03-29
forum: Hardware
---

### Post by silversoldier on 2011-03-29
Hi,

I have a Dell Precision 330 with Nvidia Quadro2 Pro graphic card. My Ubuntu is 10.10. When trying to run a program, the following error message came up:

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  19 (X_DeleteProperty)
  Resource id in failed request:  0x0
  Serial number of failed request:  86
  Current serial number in output stream:  90

I searched on internet and found a suggested solution to re-install the latest video driver. I downloaded the driver from Nvidia (Novidia-linux-x86-71.86.14-pkg1.run), boot my desktop to run level 2 and ran the driver's installation package. However, it failed. I followed Nvidia's README to build a customised driver package Nvidia-linux-x86-71.86.14-pkg1-custom.run and the installation still failed. After further research, it seems that I would need to download the kernel header and the development source code to build the kernel. However, this appears to be a risky path. I wonder if there is a safe way to resolve this problem Thanks for your help in advance.

---

