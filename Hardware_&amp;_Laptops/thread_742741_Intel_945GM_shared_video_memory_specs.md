---
title: "Intel 945GM shared video memory specs?"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by diafygi on 2008-04-02
Hi all, I have a Sager NP6260 laptop with an Intel 945GM integrated graphics card with shared video memory. I was wondering if there was any way to tell how much memory was being shared with the graphics card (I have 1.5GB total). In Windows, the device properties listed 64MB, but that changes based on the driver used (I got 96MB once, with an older driver). How can I tell how much Ubuntu's driver is using? I'm new to this, so I don't even know where to look for what driver it is.

I'm running Hardy Heron 8.04 beta.
Sysinfo says it's an "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])"

Does anyone know any commands that might be helpful? I thought the amount of shared video RAM was controlled by the BIOS, but there isn't a setting in the BIOS and the amount changed based on the driver in Windows.

---

### Post by tgalati4 on 2008-04-02
I think the 945GM graphics chipset can address a maximum of 224 MB of shared memory.  I believe the "intel" drivers in Linux take what is needed to support the resolution, color bit-rate, and 2D vs 3D texturing.

It should be addressable in your BIOS under a buried setting.  Otherwise, try some command line utilities like hwinfo or glxinfo.  Also check the X server entries in /var/log.  You may find some video memory usage statistics.

---

### Post by mrsteveman1 on 2008-04-02
I believe the kernel lists the memory being used by the driver, so check dmesg.

---

