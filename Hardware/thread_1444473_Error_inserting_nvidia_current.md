---
title: "Error inserting nvidia_current"
date: 2010-04-01
forum: Hardware
---

### Post by leneflower on 2010-04-01
Hi, I'm a Ubuntu noob and I'm trying to configure my NVidia graphics card. I installed the nvidia_current drivers (with kpackagekit) and ran nvidia_xconfig, but X did not start. The nvidia kernel module was not loaded. When I tried to manually do a modprobe nvidia, this is the error I got:
FATAL: Error inserting nvidia_current (/lib/modules/2.6.32-18-generic/updates/dkms/nvidia-current.ko): No such device
What am I missing?

Thanks, Lene

---

### Post by leneflower on 2010-04-01
Taking a look at /var.log/kern.log yields:

Apr  1 17:44:51 uranus kernel: [ 9135.434753] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Apr  1 17:44:51 uranus kernel: [ 9135.434757] NVRM: This can occur when a driver such as rivafb, nvidiafb or
Apr  1 17:44:51 uranus kernel: [ 9135.434758] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
Apr  1 17:44:51 uranus kernel: [ 9135.434759] NVRM: device(s).
Apr  1 17:44:51 uranus kernel: [ 9135.434762] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
Apr  1 17:44:51 uranus kernel: [ 9135.434763] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
Apr  1 17:44:51 uranus kernel: [ 9135.434764] NVRM: support), then try loading the NVIDIA kernel module again.
Apr  1 17:44:51 uranus kernel: [ 9135.434766] NVRM: No NVIDIA graphics adapter probed!

These are not modules, though:

sudo rmmod nvidiafb
ERROR: Module nvidiafb does not exist in /proc/modules
sudo rmmod rivafb
ERROR: Module rivafb does not exist in /proc/modules
sudo rmmod rivatv
ERROR: Module rivatv does not exist in /proc/modules

Do I really have to rebuild the kernel to use the proprietary nvidia driver? Seriously?

---

### Post by druminus on 2010-04-06
Do you have separate partition for /usr?
There is a bug: [https://bugs.edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/538071](https://bugs.edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/538071)

Workaround that helped me is:
sudo cp /usr/lib/nvidia-current/modprobe.conf /etc/modprobe.d/nvidia.conf

---

