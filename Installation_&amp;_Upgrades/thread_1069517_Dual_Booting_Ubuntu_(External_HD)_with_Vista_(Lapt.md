---
title: "Dual Booting Ubuntu (External HD) with Vista (Laptop) - Need some pointers"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Nekrinos on 2009-02-14
Hey all, I'm really new to the Ubuntu scene. I have purchased an external HD and am getting ready to attempt a dual boot of Vista (on my Presario F756NR notebook) with ubuntu, which I will install on the external HD. I have read many forum postings and guides that seem to tell me that a dual boot between hard drives is possible, but they don't give a clear method of doing this. Is there anyone who has done what I am about to do that could maybe point me in the direction of any tools or information I need to be successful?

The reason I am not just jumping on this and trying to learn by trial and error is that the F756NR seems to be notoriously difficult to find drivers and such for after a failed os install, and becomes irritable whenever one tries to alter its original configuration. I learned through trial and error that this particular model does not support xp, and I don't care to repeat history :D (This is not a windows forum... I'll hush up!)

Nek

---

### Post by Pumalite on 2009-02-14
It's better to install Ubuntu on the external and later make USB first in boot:
At step 7 >Advanced Tab>Change (hd0) for /dev/sdb
Check your external's device with:
```
sudo fdisk -lu
```

---

### Post by Anger 2 on 2009-02-14
Regarding installation,you might find these sites helpful
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
http:[www.linuxnewbieguide.org/content/partitioning-disk](www.linuxnewbieguide.org/content/partitioning-disk)

---

### Post by cobrapatrol on 2009-02-14
I dual boot Ubuntu and Vista.  When I installed 8.10 from a downloaded distro is automagicly installed grub, which manages all the Linux kernels and my Vista boot partition.  Look up grub, it should manage what you want.

I changed partition sizes on the Vista disk using the disk manager <Start:Manage:Disk Management>, which allows you to right-click on the NTFS partitons and reduce their size and just leave it as a raw disk.  Yhe Ubuntu distro installation should find the raw partition and install directly.

Alternately, You use linux from a bootable disk to fdisk the raw partition and create a ext3 type partition for the Ubuntu.  I used gparted, which is a great graphical partitioning tool.  I used the same procedure to change partitions on a second disk so it has NTFS and ext3 partitions also.

Good luck

HTH - Jim

---

### Post by Pumalite on 2009-02-14
If you decide to install Ubuntu in the same drive as Vista; you have to allocate space for Ubuntu with the Vista partitioner first:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by cdtech on 2009-02-14
I just installed mine to the external hard drive (usb drive) and kept the GRUB bootloader on the USB drive. Set the BIOS to boot the USB drive first and the primary to boot second. If the USB drive is not plugged in it will boot normally into windows.

Works for me.......

---

### Post by Nekrinos on 2009-02-15
Cool, its good to know that actually works! Thanks for everyone's responses... ill let you know how things turn out.

---

