---
title: "Kernel Panic after installing any ne kernel"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by kkass on 2005-08-12
I am trying to install the 686 kernel on my Dell Inspiron 8600 (Pentium M).  Unfortunately when I boot, it gives me a kernel panic.

"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0, 0)"

I also attempted to install the 2.6.11 386 kernel from the backports, and it gives my the same error.  If I halt grub, and boot with the 386 kernel it boots just fine.

I need to upgrade to the 686 kernel to support the 1.5GB of RAM I have installed.  (I thought about compiling a fresh kernel, but I expect it to have the same problem!)

Any ideas?

---

### Post by nad on 2005-08-14
Are you out of room in your /boot filesystem?

---

### Post by kkass on 2005-08-14
No, i have only used 14% of /boot (with the second kernel installed).

---

### Post by nad on 2005-08-14
Get out a rscue disk and take a look at your /boot/grub/menu.lst .

Barring that, you could work at your grub prompt.

---

### Post by kkass on 2005-08-15
I can still select the 386 kernel and boot up fine.  As far as I can tell my menu.lst file looks ok as well.  The entries for the 386 and 686 kernels are almost identical.

I verified that all the kenel images are actually on the system.

---

### Post by nad on 2005-08-15
Well... The kernel panic message states that it does not recognize your /dev/*da1 block device.

If I remember correctly, there are issues with 686 kernels seeing sata devices. There are bios workarounds for this. Also, the no exec feature of some dells do not behave nicely with grub.

Just some items for you to further research if you are so inclined.

---

### Post by kkass on 2005-08-17
Ok, I tried several suggestions to get the system to boot SATA devices with the 686 kernel.  Unfortunately nothing worked.

I once tried installing the 2.6.11 kernel from backports and had the same kernel panic.  So I tried compiling a new kernel.

I followed this HOWTO ([https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto) ), and used "/boot/config-2.6.10-5-386" for the configuration.

I expect that this should basically be a copy of my current kernel.  Unfortunately, when I boot I get the same kernel panic.


Any more suggestions?

---

### Post by tseliot on 2005-08-17
Have you tried to compile and install kernel 2.6.12 (from kernel.org) or to install a Breezy kernel (by adding its repositories in /etc/apt/sources.list)?

---

### Post by kkass on 2005-08-17
I just tried installing the 2.6.12 386 kernel from breezy, and it DID boot.  It also produced many errors during boot up (mostly related to ndiswrapper.)  It also did not start X.  I suspect i would have to install NVIDIA drivers for the 2.6.12 kernel as well as ndiswrapper.

So does this provide any clues to why other kernel images will not boot?

---

### Post by tseliot on 2005-08-17
Can you post the following things?

1) the name of your motherboard

2) post your /etc/modules   (type: "sudo gedit /etc/modules" or "sudo kate /etc/modules" in Terminal or Konsole)

---

### Post by kkass on 2005-08-18
1) I have not been able to find the name or vendor of my motherboard.  I have a Dell Inspiron 8600 laptop.  The best I have found is that it uses an Intel 855PM chipset.  I have the 1.3GHz processor, 1.5 GB RAM, and 128 MB NVIDIA Graphics card.  If you need more specific info, I can open it up, but not till monday.

2)
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
nvidia
ndiswrapper
```

---

### Post by tseliot on 2005-08-18
I've found out (thanks to google that your computer needs Intel PIIXn chipset support. 

add the following line at the end of your modules file (open it with "sudo gedit /etc/modules"):

piix

Now try to boot with a different kernel.

---

### Post by kkass on 2005-08-18
I tried that, and it still did not work.  I also tried rebuilding the initrd.img file with that module included.

(I tried this previously with only the ata_piix module.  Here is the thread for reference [http://ubuntuforums.org/showthread.php?t=30233&highlight=mkinitrd+modules+ntfs](http://ubuntuforums.org/showthread.php?t=30233&highlight=mkinitrd+modules+ntfs))

---

### Post by tseliot on 2005-08-18
Ok, try my guide about Kernel compilation:

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) 

Remember to select the i386 architecture and enable the support for RAM up to 4GB (it's all in my guide).

Then tell me if it works

---

