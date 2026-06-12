---
title: "to many items in /boot"
date: 2008-11-05
forum: General Help
---

### Post by BoneSaw on 2008-11-05
so recently in an attempt to upgrade to 8.10, i have come to realize that my /boot partition has about 6 different kernels wasting space.

according to uname -r, i am using 2.6.24-21 generic. is it safe to delete the rest of these? (i have found no problems with this kernel yet.

if so which files should i delete?

here is an ls readout of /boot

```

bonesaw@butcher:/boot$ ls
abi-2.6.20-16-generic             initrd.img-2.6.24-18-generic.bak
abi-2.6.22-14-generic             initrd.img-2.6.24-19-generic
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-17-generic             initrd.img-2.6.24-20-generic
abi-2.6.24-18-generic             initrd.img-2.6.24-20-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-21-generic
abi-2.6.24-20-generic             initrd.img-2.6.24-21-generic.bak
abi-2.6.24-21-generic             lost+found
config-2.6.20-16-generic          memtest86+.bin
config-2.6.22-14-generic          System.map-2.6.20-16-generic
config-2.6.24-16-generic          System.map-2.6.22-14-generic
config-2.6.24-17-generic          System.map-2.6.24-16-generic
config-2.6.24-18-generic          System.map-2.6.24-17-generic
config-2.6.24-19-generic          System.map-2.6.24-18-generic
config-2.6.24-20-generic          System.map-2.6.24-19-generic
config-2.6.24-21-generic          System.map-2.6.24-20-generic
grub                              System.map-2.6.24-21-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-18-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-20-generic
initrd.img-2.6.24-17-generic.bak  vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-18-generic

```

---

### Post by drs305 on 2008-11-05
Yes it is safe to remove the older kernels. I'd recommend keeping at least one older kernel which you know worked well in the past.

---

### Post by ad_267 on 2008-11-05
You can use the package manager (Synaptic for example, in System - Administration - Synaptic) to uninstall them. Look for the linux-image and linux-headers packages and uninstall the previous versions.

---

### Post by BoneSaw on 2008-11-05
thanks a bunch to both of you.

---

