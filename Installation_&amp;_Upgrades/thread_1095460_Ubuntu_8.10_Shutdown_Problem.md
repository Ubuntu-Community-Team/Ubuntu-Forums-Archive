---
title: "Ubuntu 8.10 Shutdown Problem"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by David Brant on 2009-03-13
Ubuntu 8.10 Shutdown Problem

I am a newbie to Linux, and who has managed to solve a couple of problems with my installation (wireless LAN and sound). However, one item remains to be cured.

When Loading Ubuntu 8.10 Out of Box (via the free CD through the post) on a Dell Optiplex GX1 Desktop of some vintage (don't ask!), the shutdown feature does not completely power off. It just hangs at the very end due to some ACPI related problem. I say this because i also tried

sudo shutdown -h now

And it shuts down ok from recovery mode.

Having followed some excellent threads, my understanging is i may need to edit the /boot/grub/menu.lst file and perhaps add

acpi=force pci=noacpi

to the Kernal /boot.. line(s).

But several Kernals are listed. System Monitor stipulates i am running on 2.6.27-11-generic, so:-

A) Should they include both that end "quiet splash", becoming "quiet splash acpi=force pci=noacpi" (all on same line)
B) or should they include both that end "single", becoming "single acpi=force pci=noacpi" (all on same line)
C) and what about the memtest?

My menu.list file reads
**************************************************************************
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		1ef08f8a-74e9-4e3e-9f29-c26d2904625d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1ef08f8a-74e9-4e3e-9f29-c26d2904625d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1ef08f8a-74e9-4e3e-9f29-c26d2904625d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1ef08f8a-74e9-4e3e-9f29-c26d2904625d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1ef08f8a-74e9-4e3e-9f29-c26d2904625d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1ef08f8a-74e9-4e3e-9f29-c26d2904625d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1ef08f8a-74e9-4e3e-9f29-c26d2904625d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1ef08f8a-74e9-4e3e-9f29-c26d2904625d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1ef08f8a-74e9-4e3e-9f29-c26d2904625d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
**************************************************************************

I have tried several edit options to the /etc/modules file

apm
apm power_off=1
acpi=force
acpi=force pci=noacpi

but all to no avail. 

Any help or advice would be much appreciated.

---

