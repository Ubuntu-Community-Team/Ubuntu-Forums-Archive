---
title: "(Ubuntu 16.04) Blackscreen after installing AMDGPU-PRO drivers R9 380X"
date: 2017-07-19
forum: Hardware
---

### Post by nikoslykos1993 on 2017-07-19
I have ubuntu 16.04 installed with a R9 380X gfx card. I installed the latest AMDGPU-PRO driver but after the install every time i reboot the screen goes offline for about 10-13 seconds, the gpu fans spin to 100% (i fix this with a script i found on github ) but still is this normal? also i dont actually know if ubuntu uses this driver. After 10-13 seconds as i mentioned before the system boots normally with the correct resolution but i get this output:

```
 lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Amethyst XT [Radeon R9 M295X Mac Edition / R9 380X] (rev f1)
Subsystem: PC Partner Limited / Sapphire Technology Tonga XT / Amethyst XT [Radeon R9 380X / R9 M295X Mac Edition] (Radeon R9 380X Nitro 4G D5)
Kernel driver in use: amdgpu
```

Does this mean the driver doesnt work like it should? i suppose maybe the system tries to use the AMDGPU-PRO and falls back to the old driver i had ?

```
dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad
|/ Name           Version      Architecture Description
++-==============-============-============-=================================
ii  amdgpu-pro     17.10-450821 amd64        Meta package to install amdgpu Pro
```

I also added my user to video group.


```
Kernel used :  4.8.0-58-generic #63~16.04.1-Ubuntu SMP Mon Jun 26 18:08:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Anyone knows how to fix this? amdgpu-pro driver is better than the stock driver ubuntu comes with?

Thanks!

---

### Post by QIII on 2017-07-19
Hello!

Please use the default font and color.  Also, please post all terminal commands and their results between code tags.

---

