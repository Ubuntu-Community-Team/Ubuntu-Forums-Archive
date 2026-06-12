---
title: "size of initrd"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by mobinskariya on 2009-09-06
my problem is i've got only a /boot partition of 20mb (thought that 15mb is maximum for a /boot).. i compiled a new kernel 2.6.30.5 (tried compiling for the first time).. when i make an intrd image with the following command
```
mkinitramfs -o initrd.img-2.6.30.5 2.6.30.5
```
it gives
```
gzip: stdout: No space left on device
```

so i tried the following command
```
mkinitramfs -o /home/mobin/Desktop/initrd.img-2.6.30.5 2.6.30.5
```
but the initrd due to the above command gives a file of 47mb.. while the initrd currently in my /boot is only of 7.2mb. am i doing anything wrong??(sorry for my confusing description)

thanx in advance
mobin

---

### Post by Fafler on 2009-09-06
There are not really any restraints as to how big /boot can be. Back in the day, some BIOS's had trouble booting from large drives and the solution was to put /boot in the first x cylinders of the drive and mount the rest of the drive after booting the kernel.

47 mb seems like a lot! Have you build initrd's that way before? Try
```
mkdir ~/initrd
cd ~/initrd
gzip -dc /path/to/initrd | cpio -id
```
This will extract the contents of the initrd and allow you to inspect them. Extract you current initrd and compare.

---

