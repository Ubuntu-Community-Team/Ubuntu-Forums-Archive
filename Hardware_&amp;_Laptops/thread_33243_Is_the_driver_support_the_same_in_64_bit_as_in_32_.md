---
title: "Is the driver support the same in 64 bit as in 32 bit?"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by Henne on 2005-05-10
Hi

Im buying a budget computer with a K8Upgrade-760GX motherboard. I have read that this board could cause sound some problems with Ubuntu, but it look liked people had no big difficulties fixing this. But i couldn't find out if those people were using the 32 bit version of Ubuntu or the 64 bit. From Windows i know that the driver support is still very poor in the 64 bit edition. Is this the same with Ubuntu or is the driver support the same as in the 32 bit version?

Thank you in advance :)

---

### Post by harryc on 2005-05-10
It depends on what they did to fix the sound issue. What was the fix? Also what sound driver does it use? Does it come natively in Ubuntu or were they installing an external driver? If it's a native Ubuntu driver, chances are good it is also supported in 64 bit.

---

### Post by Henne on 2005-05-10
[QUOTE=harryc]It depends on what they did to fix the sound issue. What was the fix? Also what sound driver does it use? Does it come natively in Ubuntu or were they installing an external driver? If it's a native Ubuntu driver, chances are good it is also supported in 64 bit.[/QUOTE]

If i understood it right, the sound was not automaticly dettected but they could just use the "intel8x0" driver and that would work. Im pretty sure that that one is native, but those guys were using another distro of linux, but i though the driver was like build into the kernel :).

---

### Post by harryc on 2005-05-10
That is a regular alsa driver that is in the kernel. You should have no problem with 64 bit support.

---

