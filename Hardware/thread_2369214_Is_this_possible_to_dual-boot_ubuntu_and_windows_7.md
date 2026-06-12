---
title: "Is this possible to dual-boot ubuntu and windows 7 on HP Zbook G1?"
date: 2017-08-20
forum: Hardware
---

### Post by tranvannhancu on 2017-08-20
I'm going to buy a new laptop HP Zbook G1 with specifications as below:


[LIST]
[*]CPU: Intel Core i7-4800MQ | 2,7 GHz (Turbo Boost 3,7 GHz) | 6 MB Cache L3
[*]GPU: Intel HD Graphics 4600 + NVIDIA Quadro K1100M
[*]RAM: 8 GB DDR3L
[*]HDD: 500GB
[*]OS: Windows 7 Professional 64-bit
[/LIST]

I want to ask if it is possible to dual-boot windows 7 and Ubuntu (14.04 or 16.04 is OK) on this machine. I read some posts about people getting problem installing with windows 8 and windows 10 but not mentioning windows 7.

Does anyone has problem with this installation? Thank you very much!

---

### Post by yancek on 2017-08-20
The most likely reason people may have had problems with windows 8/10 is that they are generally pre-installed using UEFI.  If Ubuntu or another Linux is installed and not properly installed UEFI then there will be problems dual-booting.  If windows 7 is pre-installed using the older MBR, then you need to install Ubuntu MBR and not UEFI or you will have boot problems.  Read the link below for Ubuntu dual boot documentation.  The basic thing is that you should see a different screen on boot UEFI or MBR, explained at the link below.  If you see a purple screen, it will be booting MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gordintoronto on 2017-08-20
Is it actually new, or just new to you?  The 4800MQ was launched in February, 2013.  Google didn't provide any information when I searched "zbook G1".

The NVIDIA Quadro K1100M also appears to date from 2013.

If possible, try booting from a 16.04 flash drive before buying the computer.

If you can make enough space on the hard drive (using Windows tools to shrink the existing partition(s)) you might be in luck.

---

### Post by tranvannhancu on 2017-08-21
> **yancek said:**
> The most likely reason people may have had problems with windows 8/10 is that they are generally pre-installed using UEFI.  If Ubuntu or another Linux is installed and not properly installed UEFI then there will be problems dual-booting.  If windows 7 is pre-installed using the older MBR, then you need to install Ubuntu MBR and not UEFI or you will have boot problems.  Read the link below for Ubuntu dual boot documentation.  The basic thing is that you should see a different screen on boot UEFI or MBR, explained at the link below.  If you see a purple screen, it will be booting MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This is really helpful. I'll check that out when I have my laptop. Thank you :D

---

### Post by tranvannhancu on 2017-08-21
> **gordintoronto said:**
> Is it actually new, or just new to you?  The 4800MQ was launched in February, 2013.  Google didn't provide any information when I searched "zbook G1".

The NVIDIA Quadro K1100M also appears to date from 2013.

If possible, try booting from a 16.04 flash drive before buying the computer.

If you can make enough space on the hard drive (using Windows tools to shrink the existing partition(s)) you might be in luck.

I don't know where the G1 comes from but I think it indicates that the processor is Haswell compared to G3 where it has Skylake processor. G2 also uses Haswell but the graphics card is AMD. Yeah I'll try booting from it before buying it. Thanks for your advice :D

---

