---
title: "nVidia restricted driver problem"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Kdub111 on 2009-02-22
I'm having a problem getting the nVidia kernel driver to work.  I think I caused the problem myself when I attempted to install the driver via System->Administration->Hardware Drivers while I was updating my system.

Now, when X starts, I get an unhappy message saying that the kernel driver is not loaded and I am forced to use safe graphics mode.

I think the problem may somehow be related to DKMS.

Here's some console output that may be useful:

```

root@waugh-desktop:~# lsmod | grep nv
root@waugh-desktop:~# modprobe nvidia
FATAL: Module nvidia not found.
root@waugh-desktop:~# find /lib/modules/2.6.27-11-generic/ -name '*nvidia*'
/lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia
/lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko
/lib/modules/2.6.27-11-generic/updates/dkms/nvidia.ko
root@waugh-desktop:~# cat /var/log/dkms_autoinstaller 


nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (177.82): Already installed on this kernel.

nvidia (180.11): Already installed on this kernel.

```

I've tried uninstalling and reinstalling multiple times to no avail.

Any help would be greatly appreciated!

---

