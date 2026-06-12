---
title: "Ubuntu ppa nvidia drivers broken when trying to use pci-stub"
date: 2017-02-22
forum: Hardware
---

### Post by kvasko on 2017-02-22
Used the ppa to install nvidia-378  (apt-get install nvidia-378). Have two nvidia GPUs and I'm trying to follow the following set of instructions to do passthrough of one of the cards. So I need the nvidia driver to bind to one of the cards and pci-stub to be bound to the other.

[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

If I blacklist nvidia_378 BOTH cards get added to pci-stub. The drivers were installed via "apt-get install nvidia_378". No matter what pci-stub won't grab the only one GPU (which it should).

The following will get pci-stub to grab BOTH cards. All the documentation states that if I blacklist the driver, it will still load but not before pci-stub, which apparently isn't the case with the ppa for whatever reason.

/etc/initramfs-tools/modules

    pci_stub ids=10de:0ffe,10de:0e1b

/etc/default/grub

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"


/etc/modprobe.d/blacklist.conf

    blacklist nvidia_378
    blacklist nvidia_378_modeset
    blacklist nvidia_378_drm

There are a lot of threads running around this issue but none of them work. Don't quite get how this doesn't work.

System is a 14.04 4.4.0-31-generic. 

The workaround, but NOT the actual issue on why the ppa driver wouldn't work. I removed the ppa driver, I did `service lightdm stop`, downloaded the NVidia .run file. Installed the driver using the .run file. I used the dkms (which the Nvidia driver through apt-get was also using apparently) during the installation. Rebooted the system, it was initially grabbed by nouveau, added `blacklist nouveau` to my blacklist.conf file ran update-initramfs -u, rebooted and then tada...it worked. GPU 0 has NVidia driver, GPU 1 has pci-stub. So my question is why? What is broken/different with the Ubuntu ppa nvidia driver install that it won't allow the pci-stub to grab the device?

---

### Post by teste74 on 2017-02-26
hello;

```

/etc/modprobe.d/vfio.conf
options vfio-pci ids=[COLOR=#000000]10de:0ffe,10de:0e1b

[/COLOR]

/etc/vfio-pci.cfg
DEVICES="0000:02:00.0 0000:02:00.1"


# lspci | grep "VGA\|udio"
#02:00.0 / 02:00.1 = Graphic card video / Graphic card audio

Exemple:

GPU1
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]

GPU2 (VGA passthrough)
02:00.0 VGA compatible controller: NVIDIA Corporation Device 1c03 (rev a1)
02:00.1 Audio device: NVIDIA Corporation Device 10f1 (rev a1)





/etc/modprobe.d/blacklist.conf
blacklist nvidia
blacklist nvidia_drm
blacklist nvidiafb
blacklist nouveau


Edit Grub: 
???? , sorry !



[COLOR=#000000]Terminale: [/COLOR]update-initramfs -u
[COLOR=#000000]Terminale: [/COLOR]update-grub-u

reboot



Check:
dmesg | grep vfio




```

---

