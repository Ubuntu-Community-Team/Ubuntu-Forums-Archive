---
title: "modprobe unknown symbol"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by Vr_ on 2009-06-11
Hello, I have recently begun working on a project using the BeagleBoard (OMAP3530). The BeagleBoard currently has xubuntu(2.6.29) installed on it. The BeagleBoard needs to interface with a custom camera, so custom drivers were written, and compiled on the BeagleBoard (to avoid the use of cross compilation). The module compiles fine, however when an attempt is made to insert the module using the command: sudo modprobe -v -f DEMO1_usb_v1 the following output is produced
FATAL: Error inserting DEMO1_usb_v1 (/lib/modules/2.6.29/DEMO1_usb_v1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dmesg provides the following:

DEMO1_usb_v1: Unknown symbol __aeabi_unwind_cpp_pr0
DEMO1_usb_v1: Unknown symbol __tracepoint_kmalloc
DEMO1_usb_v1: Unknown symbol __aeabi_unwind_cpp_pr1

any help would be greatly appriciated.

---

