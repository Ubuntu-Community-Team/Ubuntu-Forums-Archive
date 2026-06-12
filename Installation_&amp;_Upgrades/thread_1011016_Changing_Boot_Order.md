---
title: "Changing Boot Order"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2008-12-14
I updated from ubuntu 7.10 to 8.04 LTS. Now whne my system starts, I get a shell prompt that says 
BusyBox v1.1.3
Enter 'help' for a list of built-in commands
(initramfs)_

When I enter GRUB, I see something like this:


the first choice is this:
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=586255b2-73b6-483c-89aa-630e0727fe07 ro quiet splash

the second choice is this:
kernel /boot/vmlinuz-2.6.22-16-generic root=UUID=586255b2-73b6-483c-89aa-630e0727fe07 ro quiet splash

When I choose the Second choice,2.6.22-16 kernel choice, the system starts up ok.

When I choose the first choice, the 2.6.24-22 kernel, I get the BusyBox initramfs prompt, and this is also what happens if I just let the system start up, without entering into GRUB.

So, How do I fix this or modify the boot order to always use the 2.6.22-16 kernel?

Or if possible, how do I fix the First Choice, the 2.6.24-22 kernel, so that it doesn't keep coming up to this initramfs prompt?

---

### Post by fubbleskag on 2008-12-14
you can edit /boot/grub/menu.lst to edit these things.

if you change **default     0** to **default     1** it should begin booting the 2nd option by default

alternatively, you could remove the first entry entirely - it will be further down the file and look something like this (except with your kernel, UUID, etc):
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a97830f8-09d5-4c2f-81b5-33e5fb4a8063
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a97830f8-09d5-4c2f-81b5-33e5fb4a8063 ro splash vga=789 quiet 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

---

### Post by logos34 on 2008-12-14
check if the ramdisk image is in /boot:

initrd.img-2.6.24-22-generic  

sometimes busybox/initramfs error can be due to missing or corrupt initrd

---

### Post by hd79 on 2008-12-14
fubbleskag
I tried adding a line in the menu.lst file, right underneath the default number entry, and I took out the crosshatch and added default 1, but when I rebooted, i still came up to the initramfs screen.

I shall try your other suggestion and try editing out the first entry after the End of the Defaults section and then see what happens.

 I assume I also have to take out the entry that says something about the recovery mode?
title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=586255b2-73b6-
483c-89aa-630e0727fe07 ro single
initrd          /boot/initrd.img-2.6.24-22-generic

thanks for your help with this!

---

### Post by hd79 on 2008-12-14
logos34

I checked the boot directory, and here is what is in that directory:
abi-2.6.20-16-generic             initrd.img-2.6.22-16-generic.bak
abi-2.6.22-16-generic             initrd.img-2.6.24-22-generic
abi-2.6.24-22-generic             initrd.img-2.6.24-22-generic.bak
config-2.6.20-16-generic          memtest86+.bin
config-2.6.22-16-generic          System.map-2.6.20-16-generic
config-2.6.24-22-generic          System.map-2.6.22-16-generic
grub                              System.map-2.6.24-22-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.22-16-generic
initrd.img-2.6.22-16-generic      vmlinuz-2.6.24-22-generic

So it looks like the file you asked about is there, but there seems to be quite a few files in that directory. More than I expected, at any rate, so maybe that is part of the problem?

Thanks for your assistance!

---

