---
title: "Blacklist amdgpu."
date: 2017-11-21
forum: Hardware
---

### Post by cuda12345 on 2017-11-21
I'm having trouble with pci passthough, I have one nVidia card, and one AMD card. I want to pass the AMD card to Qemu, but I need to blacklist the amdgpu module to do it. However, whenever I do, I'm greeted with no signal to the nVidia card.

Ubunutu 16.04 LTS

Why does blacklisting amdgpu affect the nVidia card?

```
 lspci -nnk -d 1002:67df
23:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:67df] (rev e7)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:22fc]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
jam@AMD:~$ lspci -nnk -d 10de:0df8
22:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GL [Quadro 600] [10de:0df8] (rev a1)
    Subsystem: Hewlett-Packard Company GF108GL [Quadro 600] [103c:0835]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
vfio  
vfio_iommu_type1  
vfio_pci  
vfio_virqfd  
kvm  
kvm_amd

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"

/etc/modprobe.d/vfio.conf

options vfio-pci ids=1002:67df,1002:aaf0

/etc/mkinitcpio.conf


MODULES="... vfio vfio_iommu_type1 vfio_pci vfio_virqfd ..."
HOOKS="... modconf ..."



```

---

