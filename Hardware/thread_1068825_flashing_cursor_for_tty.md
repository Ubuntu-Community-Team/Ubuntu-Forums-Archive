---
title: "flashing cursor for tty"
date: 2009-02-13
forum: Hardware
---

### Post by helbent forleder on 2009-02-13
Hi.:):)
I am using the netbook remix on an Asus eee 1000H. I have a strange problem that I've just recently noticed.
When I open a virtual terminal all that I see is a flashing cursor. I can type commands and they work, but I can't see what I am doing on the screen. :(
If I boot in recovery mode and I run repair on the X server, I can use the terminal normally (I can see everything) for that session only. The next reboot it's back to typing blind.
Any ideas how I should go about finding the problem and fixing it?
Here's the relevant part of my /boot/grub/menu.lst
> title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=419385a0-4b2e-43b6-807f-d2f3b785e872 ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=419385a0-4b2e-43b6-807f-d2f3b785e872 ro single
initrd		/boot/initrd.img-2.6.24-21-eeepc

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
Any ideas would be appreciated!:guitar:

---

### Post by easybake on 2009-02-13
did you change the font color in your terminal?

---

### Post by helbent forleder on 2009-02-13
> **easybake said:**
> did you change the font color in your terminal?
Not that I know of? Where do I find the configuration file?

---

### Post by helbent forleder on 2009-02-13
Any other ideas?
:guitar:

---

