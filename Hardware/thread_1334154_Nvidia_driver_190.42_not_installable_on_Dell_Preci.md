---
title: "Nvidia driver 190.42 not installable on Dell Precision 470"
date: 2009-11-22
forum: Hardware
---

### Post by pelgrim on 2009-11-22
To use dual screen and opengl, I need to use restricted driver for
my graphic card on Dell Precision 470, that is:
NVIDIA-Model-P231, Nvidia Quadro4 NVS 280 XGL 64MB 2D PCI-E 16x
(still standard configuration of this pc)

Recomended driver doesn't work (version 173 in restricted drivers list)
Tried 180 and 185 from synaptics.
Still doesn't work.
When trying to configure with 
sudo nvidia-xconfig
whick makes me a xorg.conf file.
X doesn't boot anymore after that until I delete xorg.config

I was adviced to install version 190.42 manualy,
but after quiting X the installer tells me this:

nvidi-installer.log fragment

-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'. This happens most
frequently when this kernel module was built against the wrong or
improperly configured kernel sources, with a version of gcc that differs
from the one used to build the target kernel, or if a driver such as
rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
installed in this system is not supported by this NVIDIA Linux graphics
driver release.

I run the latest kernel available on Update Manager
2.6.31-15-generic

---

