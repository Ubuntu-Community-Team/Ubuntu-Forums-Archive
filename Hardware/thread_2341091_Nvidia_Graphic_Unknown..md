---
title: "Nvidia Graphic Unknown."
date: 2016-10-24
forum: Hardware
---

### Post by sellasy on 2016-10-24
Hi everyone, I got a problem with Ubuntu 16.04 on my notebook.
Im not able to put my Nvidia GM108M [GeForce 830M] to work.
Already tried a lot of option on my research here on the forum but nothing answered my doubts.

Here are some lists for infos.

lshw -c video
```
*-display                      description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:b5000000-b53fffff memory:c0000000-cfffffff ioport:6000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 830M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

Dont know why it says Unclaimed, I'm trying to fix that by researching but i failed to find that solution

ubuntu-drivers list
```
intel-microcode
nvidia-340
nvidia-361

```

ubuntu-drivers devices
```
== /sys/devices/pci0000:00/0000:00:1c.4/0000:0a:00.0 ==modalias : pci:v000010DEd00001340sv0000103Csd00002280bc03sc02i00
model    : GM108M [GeForce 830M]
vendor   : NVIDIA Corporation
driver   : nvidia-340 - distro non-free
driver   : nvidia-361 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin


== cpu-microcode.py ==
driver   : intel-microcode - distro non-free
```

dpkg -l | grep -i nvidia
```
ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cardsii  libcuda1-340                                340.96-0ubuntu3                               amd64        NVIDIA CUDA runtime library
ii  nvidia-340                                  340.96-0ubuntu3                               amd64        NVIDIA binary driver - version 340.96
ii  nvidia-opencl-icd-340                       340.96-0ubuntu3                               amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver



```

And, when i get to the All Settings>Details it show "Graphics  Unknown"

I already updated my Additional driver to the "nvidia-361 - distro non-free recommended" witch is a proprietary, tested driver but nothing changed.
It also says that I'm using an alternative driver but i dont know wich driver is beeing used.

I tried a lot to find this solution but nothing works.

Hope someone could help me here
(sorry for my english)
Thanks!

---

