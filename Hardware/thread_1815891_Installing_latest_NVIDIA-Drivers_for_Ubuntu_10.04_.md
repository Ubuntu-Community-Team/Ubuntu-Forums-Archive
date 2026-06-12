---
title: "Installing latest NVIDIA-Drivers for Ubuntu 10.04 and libqt4-opengl-dev"
date: 2011-08-01
forum: Hardware
---

### Post by fortmeier on 2011-08-01
Hi there,

for using Cuda 4.0 I need the latest NVIDIA drivers to be installed (> ~250.xx). Unfortunately,  Ubuntu 10.04 does only Support the installation up to I think 195.xx so I downloaded the installer script from NVIDIA and installed the drivers. For those to work properly I needed to remove all nvidia-* and libgl1-mesa* packages and removed all opengl libraries and headers manually. This worked, otherwise there are errors appearing when trying to use any appliciation relying on glx and the nvidia-settings tool does not show any info in the glx section (complaining about 'could not identify vendor' or the like). 

Now I need to install the package "libqt4-opengl-dev". If I install it, all the mese stuff gets installed as well an I end up with a system where glx is not working again.

Any advice?

Cheers,
Dirk

---

