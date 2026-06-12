---
title: "Which NVidia driver for Ubuntu 18.04 LTS?"
date: 2020-11-23
forum: Hardware
---

### Post by John Nagle on 2020-11-23
What's the recommended video driver today for NVidia boards for Ubuntu 18.04 LTS. There are seven options offered:

[IMG]https://i.ibb.co/M9M98QG/nvidiadriveroptions.png[/IMG]

**Pick one. **The default after updating the system was Noveau, which doesn't use the hardware GPU. Not too useful.

I know, this is an old headache, with many mentions in the forum over the years, referencing drivers of the distant past. So, have to ask again.


I'm getting system crashes from the NVidia driver while the machine is unused and in a screen-locked state, but with a browser open. Happens about twice a month. 

[FONT=courier new]Nov 23 09:12:16 Nagle-LTS kernel: [586581.925164] Xorg: page allocation failure: order:5, mode:0x14040c0(GFP_KERNEL|__GFP_COMP), nodemask=(null)
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925167] Xorg cpuset=/ mems_allowed=0
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925174] CPU: 1 PID: 1817 Comm: Xorg Tainted: P           OE    4.15.0-124-generic #127-Ubuntu
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925176] Hardware name: ASUS All Series/Z87M-PLUS, BIOS 0311 04/18/2013
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925177] Call Trace:
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925186]  dump_stack+0x6d/0x8e
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925193]  warn_alloc+0xff/0x1a0
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925197]  ? __alloc_pages_direct_compact+0x51/0x100
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925201]  __alloc_pages_slowpath+0xdc5/0xe00
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925206]  __alloc_pages_nodemask+0x29a/0x2c0
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925212]  alloc_pages_current+0x6a/0xe0
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925216]  kmalloc_order+0x18/0x40
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925219]  kmalloc_order_trace+0x24/0xb0
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925224]  __kmalloc+0x1fe/0x210
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925252]  nvkms_alloc+0x25/0x60 [nvidia_modeset]
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925278]  _nv002653kms+0x16/0x30 [nvidia_modeset]
Nov 23 09:12:16 Nagle-LTS kernel: [586581.925281] WARNING: kernel stack frame pointer at 00000000964a9a14 in Xorg:1817 has bad value 00000000defae3b2[/FONT]

---

### Post by Bashing-om on 2020-11-23
John Nagle; Hello

> 
What's the recommended video drive


For the GT 640 card Nvidia recommends the 450 version driver:
[https://www.nvidia.com/Download/driverResults.aspx/164073/en-us](https://www.nvidia.com/Download/driverResults.aspx/164073/en-us)

[INDENT]My bit to try and help
[/INDENT]

---

