---
title: "Asus Zenbook UX51 - NVIDIA GeForce 650M not recognized"
date: 2014-02-26
forum: Hardware
---

### Post by alscdz on 2014-02-26
Hi,

I'm having a problem with my Asus Zenbook UX51 (Ubuntu 13.10) where I cannot install NVIDIA drivers. 
When I try to run (downloaded from nvidia page - NVIDIA-Linux-x86_64-331.49.run) drivers, I get:

> WARNING: You do not appear to have an NVIDIA GPU supported by the 331.49 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com").


Here is some info:

```
*$ uname -a*
*Linux ales-zenbook 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux*

*$ lspci | grep -i vga*
*00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)*
*01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev ff)*


$ lspci -v (**only including VGA controllers**)
*00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])*
*    Subsystem: ASUSTeK Computer Inc. Device 15a7*
*    Flags: bus master, fast devsel, latency 0, IRQ 47*
*    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]*
*    Memory at d0000000 (64-bit, prefetchable) [size=256M]*
*    I/O ports at f000 [size=64]*
*    Expansion ROM at <unassigned> [disabled]*
*    Capabilities: <access denied>*
*    Kernel driver in use: i915*
*01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev ff) (prog-if ff)*
*    !!! Unknown header type 7f*


*$ lsmod | grep -i nou**
[I]$ 

[/I]*$ dmesg | grep NVIDIA*
*$ *
```

I also tried installing bumblebee and nvidia-current through apt (using official instructions [https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee](https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee)), but no difference. Still wasn't able to run nvidia-settings.


I can provide any additional info, if needed. 

Thanks!
Ale&#353;

---

### Post by Bashing-om on 2014-02-28
alscdz; Hi !
With release 13.10 there is another option (seeing as how Nvidia does not support optimus in linux), 
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

BumbleBee must be purged !

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

