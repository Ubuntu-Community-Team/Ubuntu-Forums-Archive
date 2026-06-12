---
title: "Nvidia 8400GS No tv out (Feisty)"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by bilkan on 2007-09-09
I've recently bought a PC with **MSI NX8400GS** (PCIe). I have a problem displaying desktop on tv. My tv set supports composite signal. My previous PC with an Ati Radeon 9600 SE (AGP) worked fine. 

I've installed the nvidia drivers from nvidia ver **100.14.11** under Xorg 7.2.0 in Feisty. The driver works fine without any problems but only detects my default LCD monitor and nothing else. I've modified my xorg.conf file according [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut), but without any success. 

I've also noticed that during PC power up (POST) the tv monitor remains blank, something that my older PC with ATi didn't do. TV set showed everything until gdm started.
I only use linux. I don't have windows installed in my PC and Idon't have a spare disk to check if it is a hardware problem. 

If anybody experiences the same problem or if anyone solved it, I would appreciate any help.

Thanks in advance.

---

### Post by bilkan on 2007-09-14
Ok. I found the problem; it was the composite cable. The new card supports only  composite video signal. So I changed the cable and everythig is ok!

---

