---
title: "NVIDIA Driver Installation"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by Eugene C. on 2006-04-09
Hi. I'm trying to install the latest version of NVIDIA's drivers on my Ubuntu system (I have a Geforce 2 MX 400). Anyway, the installation is asking for the Linux kernel sources which I don't have on my system under /usr/src. I'm running kernel version 2.6.12-10-386 so I figured I could download the kernel source using Synaptic...which doesn't have it displayed (the nearest version was 2.6.11). I tried looking for the sources on the kernel website but no go there either. So, can anyone point me in the right direction on where I can go and download my kernel version sources? I'm fairly new to Linux so please forgive me if I missed anything obvious. Thanks in advance.

---

### Post by karthik085 on 2006-04-09
You probably need linux-headers-2.6.12-10-386.
Follow this guide: 
[http://ubuntuforums.org/showthread.php?t=139264&highlight=howto+install+latest+nvidia](http://ubuntuforums.org/showthread.php?t=139264&highlight=howto+install+latest+nvidia)

---

### Post by Eugene C. on 2006-04-09
The kernel headers is exactly what I needed, thanks a lot for your help!

---

