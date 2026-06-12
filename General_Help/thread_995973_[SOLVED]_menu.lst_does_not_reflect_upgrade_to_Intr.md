---
title: "[SOLVED] menu.lst does not reflect upgrade to Intrepid"
date: 2008-11-28
forum: General Help
---

### Post by nachomania on 2008-11-28
Recently, I upgraded to Intrepid, but during the install, I didn't really pay attention to the prompts that came up. The one about grub, I really missed. So now, I need to add acpi=force, but I have no idea where to put it. /boot/grub/menu.lst doesn't show Intrepid. I'm not even sure I'm using the new kernel.

---

### Post by drs305 on 2008-11-28
During the install you may have told the install to keep your old grub menu.
Here are some commands to run to help us help you:

What you are running:
```

uname -r 

```
What your menu.list looks like:
```
cat /boot/grub/menu.list
```
Which kernels you have installed:
```
ls /boot/ | grep vmlinuz*
```
UUID's mentioned in grub:
```
sudo blkid
```

You can also install StartUp-Manager, a gui-based app that helps tweak grub's menu.lst, including which kernel to boot.
To install:
```

sudo apt-get install startupmanager

```

To run:
System, Administration, StartUp-Manager

Here is a tutorial:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by pennacook on 2008-11-28
Does your menu.lst have:
```
title		Ubuntu 8.10
```

The acpi=force would have to be put on the kernel line, at the end of the line.

---

### Post by zeigfried on 2008-11-28
Run ```
sudo update-grub
``` and see if it helps.

Cheers

---

### Post by nachomania on 2008-11-28
I'm running 2.6.24-21 generic

> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=10246f51-b8b4-4b74-aff0-0da7b76a5ba1 ro vga=791 acpi=force
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=10246f51-b8b4-4b74-aff0-0da7b76a5ba1 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=10246f51-b8b4-4b74-aff0-0da7b76a5ba1 ro vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=10246f51-b8b4-4b74-aff0-0da7b76a5ba1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sudo blkid gives 
/dev/sda1: UUID="10246f51-b8b4-4b74-aff0-0da7b76a5ba1" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="eae67e13-b288-4839-84bf-3fc716894b4c"

Intrepid is not in there, and I can't find the new kernel in Startup-Manager

---

### Post by drs305 on 2008-11-28
Did you run this:
```
ls /boot/ | grep vmlinuz*
```
Intrepid should be 2.6.27 and you appear to have only Hardy's kernel - 2.6.24

You can also look in Synaptic and search for "linux-image-2.6" and see if you have the "linux-image-2.6.27-X" or "linux-image-2.6.27-X-generic" installed. The X could be a 4 through 7 or now 9, I believe.

---

### Post by nachomania on 2008-11-28
Yes, just became a 9. Same prompt came when it updated, and I selected replace this time. Problem *solved* :D

---

