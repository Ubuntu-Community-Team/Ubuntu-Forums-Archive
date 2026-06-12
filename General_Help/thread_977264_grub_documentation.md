---
title: "grub documentation"
date: 2008-11-10
forum: General Help
---

### Post by gotix on 2008-11-10
I would like to learn more about the parameters in the /boot/grub/menu.lst file.

I tried to use this guide ([http://darksun.com.pt/mirage/usb_minipe_backtrack_knoppix.html](http://darksun.com.pt/mirage/usb_minipe_backtrack_knoppix.html)) to install a Damn Small Linux (which is based on Knoppix) on a Pen Drive.
However it does not work and I would like to know more about all those parameters like this:

kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init lang=pt apm=power-off vga=791 initrd=minirt.gz nomce quiet pci=nommconf BOOT_IMAGE=knoppix

In the grub documentation, does not say anything about all those possible parameters for "kernel" ([http://www.gnu.org/software/grub/manual/html_node/kernel.html#kernel](http://www.gnu.org/software/grub/manual/html_node/kernel.html#kernel)), only says that you can pass the kernel image.

Does anyone know if there is any better grub documentation that explain this kind of things?

thanks

---

### Post by ciscosurfer on 2008-11-10
This is a [fairly extensive guide]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by meierfra. on 2008-11-10
The kernel parameters have nothing to do with grub. Grub does not even look at the parameters, it just passes them  to the kernel. 

So you have to look at the kernel documentation and the DSL documentation to figure out what they mean.

---

