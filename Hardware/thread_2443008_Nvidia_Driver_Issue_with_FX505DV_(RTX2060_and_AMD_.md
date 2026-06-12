---
title: "Nvidia Driver Issue with FX505DV (RTX2060 and AMD Vega 10) on Ubuntu"
date: 2020-05-10
forum: Hardware
---

### Post by ColdCry on 2020-05-10
Hey  there. I am trying to install my nvidia drivers on Ubuntu 20.04. I  freshly installed ubuntu and right after it i made the software updater  updates. I manually downloaded the linux drivers of RTX2060 and  installed them right after disabled nouveau driver. There were no errors  with the installation and now Nvidia is working great. The card has an  hdmi output on the left side of my notebook and its connected to a  monitor which is working right now but lets come to my problem. If i  deattach hdmi cable from notebook the main display of the notebook shows  just blanks screen like its connected to hdmi. So from that i guessed  that amdgpu is not working. Before installing the nvidia drivers the  hdmi wasn't working and the main display of the laptop was working well.  How can i fix this issue?

Here is nvidia-smi
nvidia-smi
Sun May 10 13:13:22 2020
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.82 Driver Version: 440.82 CUDA Version: 10.2 |

|-------------------------------+----------------------+----------------------+
| GPU Name Persistence-M| Bus-Id Disp.A | Volatile Uncorr. ECC |
| Fan Temp Perf Pwr:Usage/Cap| Memory-Usage | GPU-Util Compute M. |
|===============================+======================+======================|
| 0 GeForce RTX 2060 Off | 00000000:01:00.0 On | N/A |
| N/A 35C P8 1W / N/A | 248MiB / 5934MiB | 1% Default |
+-------------------------------+----------------------+----------------------+
+-----------------------------------------------------------------------------+
| Processes: GPU Memory |
| GPU PID Type Process name Usage |
|=============================================================================|
| 0 1118 G /usr/lib/xorg/Xorg 35MiB |
| 0 1637 G /usr/lib/xorg/Xorg 68MiB |
| 0 1821 G /usr/bin/gnome-shell 131MiB |
+-----------------------------------------------------------------------------+
And here is lshw -c video
lshw -c video
WARNING: you should run this program as super-user.
*-display
description: VGA compatible controller
product: TU106M [GeForce RTX 2060 Mobile]
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=nvidia latency=0
resources:  irq:75 memory:f6000000-f6ffffff memory:c0000000-cfffffff  memory:d0000000-d1ffffff ioport:f000(size=128) memory:f7000000-f707ffff
*-display
description: VGA compatible controller
product: Picasso
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:05:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list
configuration: driver=amdgpu latency=0
resources: irq:73 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:c000(size=256) memory:f7500000-f757ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.,
So  the system knows there is a amdgpu and vga attached to that but it  doesn't work properly. I would be very glad if someone can help me about  this.

---

