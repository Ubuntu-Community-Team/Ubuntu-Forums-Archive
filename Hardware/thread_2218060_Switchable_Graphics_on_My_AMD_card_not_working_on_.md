---
title: "Switchable Graphics on My AMD card not working on Ubuntu"
date: 2014-04-19
forum: Hardware
---

### Post by Utkarsh_Gupta on 2014-04-19
These are my hardware details which I read somewhere how to upload. I can't figure out how to enable switchable graphics and how to install the drivers for my AMD card. I followed instructions on a ubuntu forum thread which resulted in my getting a low graphics error problem. The situation further worsened as i tried manipulating lightdm and gdm. Finally I had to remove ubuntu and do a fresh install of 14.04. Now I am pretty scared of trying anything new which I don't know will work or not. Please Help!!!

[http://paste.ubuntu.com/7284483/](http://paste.ubuntu.com/7284483/)

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 10.1.0


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Dell Device [1028:05b8]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] [1002:6601] (rev ff)
    Kernel driver in use: radeon
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:05b8]

PS: Still awaiting an answer!! :(

---

### Post by aosama on 2014-06-24
same problem and the VGA fan on the left hand side is always on at maximum speed
Mars [Radeon HD 8730M] (rev ff)

---

### Post by Mark Phelps on 2014-06-24
> **aosama said:**
> same problem and the VGA fan on the left hand side is always on at maximum speed
Mars [Radeon HD 8730M] (rev ff)

Unless you ALSO have dual graphics in your PC -- both Intel and AMD, this is not the same problem and you should open your own thread, not hijack someone else's.

---

