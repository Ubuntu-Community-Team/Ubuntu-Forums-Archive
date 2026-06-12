---
title: "question about boot menu"
date: 2008-08-09
forum: General Help
---

### Post by analyzer92 on 2008-08-09
I have recently installed Hardy Heron on my desktop. This was my first time installing Ubuntu. After I installed it, the boot menu was normal it had the mem test, the "safe mode" one, the normal one, and XP which I left on. However, once I got the internet set up, I had about 200 upgrades and one of them was a kernel upgrade. After I upgraded the kernel, I noticed that there are more selections on my boot menu. The mem test, the "safe mode" ubuntu for both kernel versions, ubuntu with both kernels, and XP. I was wondering, if it is good to delete the old kernel entries on the boot menu and if so, how do you do it.

---

### Post by x1a4 on 2008-08-09
Hi,

Kernels are in the /boot/ directory.  To delete them, simply delete  the following files:

/boot/config-*kernel-version*,
/boot/initrd.img-*kernel-version*,
/boot/System.map-*kernel-version*,
/boot/vmlinuz-*kernel-version*
```
sudo rm /boot/*-*kernel-version*-*
```

Then update GRUB
```
sudo /usr/sbin/update-grub
```

---

### Post by housam on 2008-08-09
edit your menu.lst.
Type in a terminal the following code 
```
gksudo gedit /boot/grub/menu.lst
```
then put a hash  # in front of any line (and its group lines ) that you don't want it to show up in the grub menu.
this will not remove the kernel from your computer but will just make it not to be shown up.

---

### Post by sisco311 on 2008-08-09
> **x1a4 said:**
> Hi,

Kernels are in the /boot/ directory.  To delete them, simply delete  the following files:

/boot/config-*kernel-version*,
/boot/initrd.img-*kernel-version*,
/boot/System.map-*kernel-version*,
/boot/vmlinuz-*kernel-version*
```
sudo rm /boot/*-*kernel-version*-*
```Then update GRUB
```
sudo /usr/sbin/update-grub
```

Removing the old kernel(s) from synaptic is more secure.

OP: 
Search in Synaptic for *linux-image* and remove the unwanted ones.
I recommend you to keep at least two kernels.

Commenting out the entries from grub is the safest option.

---

