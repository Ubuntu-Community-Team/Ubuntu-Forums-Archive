---
title: "RAM upgrade"
date: 2011-04-01
forum: Hardware
---

### Post by TimmyK. on 2011-04-01
Hello again. Earlier today, I upgraded my RAM from 2.0 GB to 4.0 GB. When I booted up, it gave me the options of F1 to continue, F2 to configure, and F5 to run diagnostics. It hit F1, and it booted as normal. However, when I went to SysInfo, I was informed I had 3,014 MB, and in the System Monitor, it told me I had 2,900 MB. Is there any way to change this; something is the BIOS menu maybe? I am running  Dell D620 with a 32-Bit Ubuntu, by the way. Reading the [Wikipedia article]("http://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D620") on this, it should be able to accept at least 3.3 GB.

---

### Post by kiddfroster on 2011-04-01
> **TimmyK. said:**
> Hello again. Earlier today, I upgraded my RAM from 2.0 GB to 4.0 GB. When I booted up, it gave me the options of F1 to continue, F2 to configure, and F5 to run diagnostics. It hit F1, and it booted as normal. However, when I went to SysInfo, I was informed I had 3,014 MB, and in the System Monitor, it told me I had 2,900 MB. Is there any way to change this; something is the BIOS menu maybe? I am running  Dell D620 with a 32-Bit Ubuntu, by the way. Reading the [Wikipedia article]("http://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D620") on this, it should be able to accept at least 3.3 GB.

If it's the 32 bit version, and you have integrated graphics, some of your RAM is being stolen from the system memory for the graphics card. That would be the cause of the missing memory. If your processor supports 64-bit instructions, I would just upgrade to Ubuntu 64-bit.

---

### Post by TimmyK. on 2011-04-01
It does support 64-bit, but please read the section of the Wikipedia article I linked to. I don't think that will help.

---

### Post by PRC09 on 2011-04-01
The following link should explain the reason......



[http://duartes.org/gustavo/blog/post/motherboard-chipsets-memory-map](http://duartes.org/gustavo/blog/post/motherboard-chipsets-memory-map)

---

