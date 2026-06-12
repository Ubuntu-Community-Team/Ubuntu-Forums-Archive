---
title: "USBmon for UBUNTU"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by fusion2344 on 2008-03-14
I need usbmon on UBUNTU (Edgy, Kernel 2.6.17-11-generic) to monitor(sniff) USB device communications.

According to a post on another forum I need to activate Kernel debugging and USB monitor in the kernel configuration menu.

I downloaded the kernel source (2.6.17), made an "oldconfig" end exectuted "make menuconfig".

In the kernel configuration menu "kernel debugging" and "USB monitor" was already activated.

So...

From the post I need to execute the following to start USBmon:

# mount -t debugfs none_debugs /sys/kernel/debug
# modprobe usbmon
# ls -l /sys/kernel/debug

But I dont have any debug information in my kernel directory.

Can someone please help me to get USBmon working.

URGENT please

---

