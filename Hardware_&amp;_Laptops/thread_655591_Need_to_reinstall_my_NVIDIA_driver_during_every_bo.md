---
title: "Need to reinstall my NVIDIA driver during every boot"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by alexao on 2008-01-01
I have a problem now that I have to reinstall the nvidia driver (169.04) everytime I reboot my machine. Otherwise it uses the xorg.conf.failsafe. It starts X, but I can only get a very low resolution which I guess is the whole point in the failsafe option. I've installed this driver cause I need to use it for programming in CUDA for my master thesis. 

When running lsmod when X runs in failsafe mode, I get the following output:
lsmod | grep nvidia
nvidia 6221648 0
agpgart 35016 2 nvidia, intel_agp

but right after installing the nvidia driver again, I get:
lsmod | grep nvidia
nvidia 7867904 32
i2c core 26112 1 nvidia
agpgart 35016 1 nvidia, intel_agp


Any ideas?

---

### Post by tgilber1 on 2008-01-01
It sounds like the nvidia.ko kernel object module is being written to the volatile directory


1.  Edit you /etc/default/linux-restricted-modules-common file and add the "nv" driver to the following line:

DISABLED_MODULES="nv"

2.  Rerun the nvidia installation setup

3.  Reboot computer

_Note:  If this setup does not work, you can copy the nvidia.ko from the volatile directory before rebooting_

Find out location of nvidia.ko module that is being loaded

1.  sudo modprobe -l nividia #should print absolute path if it exists, and sudo is not required

2.  Copy nvidia.ko from volatile to modules directory

sudo cp /lib/modules/$(uname -r)/volatile/nvidia.ko /lib/modules/$(uname -r)/kernel/drivers/video

3.  sudo depmod -a $(uname -r)

4.  sudo /etc/init.d/gdm restart or Reboot computer

---

### Post by alexao on 2008-01-01
heh, thanks for the reply. Was just gonna come in here and say that I made a typo in the linux-restricted-modules-common file, I put in nvidia instead of nv. So it works now, cheers :)

---

