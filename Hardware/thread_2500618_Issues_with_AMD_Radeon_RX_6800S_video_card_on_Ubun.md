---
title: "Issues with AMD Radeon RX 6800S video card on Ubuntu 24.04"
date: 2024-09-06
forum: Hardware
---

### Post by kazinho_br on 2024-09-06
[COLOR=#000000][FONT=&amp]My Specs:

Processor:
AMD Ryzen 9 7900X (comes with onboard AMD Radeon&#8482; Graphics)
GPU AMD Radeon RX 6800S 8GB GDDR6
Memory DDR5 25GB 5800Mhz
Disk 1TB SSD NVME
 
Operational System:
Ubuntu 24.04 LTS - Kernel Image 6.8

I'm having performance issues on my newly installed Ubuntu 24.04.

I installed version 6.2 from the AMD repo website ([https://repo.radeon.com/amdgpu-install/6.2/ubuntu/jammy/amdgpu-install_6.2.60200-1_all.deb]("https://repo.radeon.com/amdgpu-install/6.1.3/ubuntu/focal/amdgpu-install_6.1.60103-1_all.deb")) and everything run well (I had thought so).

The instalation complete and have generated all files of dkms files so.
After that I ran the command glxinfo -B and got the result below:

```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD Radeon Graphics (radeonsi, rembrandt, LLVM 18.1.7, DRM 3.58, 6.8.0-41-generic) (0x1681)
    Version: 24.2.0
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 108 MB, largest block: 108 MB
    VBO free aux. memory - total: 10758 MB, largest block: 10758 MB
    Texture free memory - total: 108 MB, largest block: 108 MB
    Texture free aux. memory - total: 10758 MB, largest block: 10758 MB
    Renderbuffer free memory - total: 108 MB, largest block: 108 MB
    Renderbuffer free aux. memory - total: 10758 MB, largest block: 10758 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 12136 MB
    Currently available dedicated video memory: 108 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD Radeon Graphics (radeonsi, rembrandt, LLVM 18.1.7, DRM 3.58, 6.8.0-41-generic)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 24.2.0-devel
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 4.6 (Compatibility Profile) Mesa 24.2.0-devel
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile


OpenGL ES profile version string: OpenGL ES 3.2 Mesa 24.2.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```


From what I can get, the card being used in my system is the standard Radeon onboard card and not my RX  6800S.


I was able to confirm this by running the heaven benchmark program, where I only got 15 to 20 fps in the  tests.


On the same computer when I run the same test I get about 120fps in the heaven benchmark test.


I will attach the debug files that AMD recommends we put:
[/FONT][/COLOR]
> $ lspci -vnn > lspci.vnn.log
$ lspci -nn > lspci.nn.log
$ sudo dmidecode > dmidecode.log
$ uname -a > uname.a.log
$ lsinitramfs /boot/initrd.img-`uname -r` > lsinitramfs.log
$ sudo lshw > lshw.log
$ modinfo amdgpu > modinfo.amdgpu.log
$ glxinfo > glxinfo.log

[COLOR=#000000][ATTACH]294206[/ATTACH]
[/COLOR][COLOR=#000000][FONT=&amp]
I would really appreciate if anyone could help. I don't know what else to do in Linux.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2024-09-06
> ROG Zephyrus G14
So you have a laptop? Does DRI_PRIME work?
```
DRI_PRIME=1 glxinfo -B
```

> I installed version 6.2 from the AMD repo website
Not a good idea, especially since it looks like you used the wrong version (you wanted noble for Ubuntu24 and you used jammy for Ubuntu 22). Unless you want to use compute stuff ("ROCm"), installing extra drivers from AMD is not necessary.

---

### Post by kazinho_br on 2024-09-10
[COLOR=#000000]So you have a laptop? Does DRI_PRIME work?[/COLOR]
[COLOR=#000000]Code:
DRI_PRIME=1 glxinfo -B[/COLOR]
You are damn right! This command activate my gpu! I can't undertand why my stronger gpu is not activated when it is needed!

I don't have many Linux skills, I'll study more!


Regarding the question I raised about whether Linux is possible, I understand that it is necessary to activate the dedicated GPU. Is it possible to make it automatic in some way in Linux?

---

### Post by Yellow Pasque on 2024-09-11
> **kazinho_br said:**
> Is it possible to make it automatic in some way in Linux?
Are you talking about load-based switching? No, Linux doesn't do that.

---

