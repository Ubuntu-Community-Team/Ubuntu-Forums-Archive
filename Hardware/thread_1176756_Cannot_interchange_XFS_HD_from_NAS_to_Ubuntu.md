---
title: "Cannot interchange XFS HD from NAS to Ubuntu"
date: 2009-06-02
forum: Hardware
---

### Post by grfi on 2009-06-02
Hi, I am having an issue and I'll try to explain it to the best of my ability.

I have a Lacie 2big Network NAS sitting in my network. It is [this]("http://www.lacie.com/products/product.htm?pid=11253") model with the latest firmware (2.0.7).
I also have 2 external USB hard drives connected to the USB expansion ports of the NAS.

My main machine is a Windows Vista 32 bits laptop and I also run a Ubuntu 9.04 virtual machine using Virtualbox from within Windows Vista.

The NAS default filesystem is XFS and it also supports this filesystem from drives connected to the USB ports.

Recently I tried to format one of the hard drives using Gparted and XFS from the virtual machine. It formats and mounts ok in the virtual machine, but the drive does not mount in the NAS device. It is not recognized. 

The NAS has its own XFS format option. When using this option to format the USB drive it mounts ok in the NAS. The drive also mounts ok in the virtual machine from the laptop USB port. However if I do any disk operation in the USB drive connected to the laptop USB port and using the virtual machine it does not mount anymore in the NAS. I have to reformat it with the NAS XFS format option.

To sum it up: I cannot interchange a XFS formatted USB hard disk from the USB port of my NAS to my laptop USB port and access it from the virtual Ubuntu machine without creeping it and not being able to mount it back again in the NAS device.

Does anyone has some insight on this? I thought XFS would be XFS no matter where I format it (NAS or Gparted). Could it be some incompatibility between the two filesystems? Interesting note: if I format the drive to FAT32 everything works ok and I can interchange the drive from the NAS to the laptop virtual machine without a problem. I would prefer to use XFS because of the better filesystem efficiency.
Thanks for the help.

---

