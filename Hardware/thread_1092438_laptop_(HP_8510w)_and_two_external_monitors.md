---
title: "laptop (HP 8510w) and two external monitors"
date: 2009-03-10
forum: Hardware
---

### Post by espenbe on 2009-03-10
I just got an HP 8510w laptop, a docking station and two external monitors.  The laptop has nVidia (NVIDIA Quadro FX570M) graphics chipset.

Using WinXP getting the two external monitors to work is straight forward.  I can however not get the two external monitors to work at the same time using Ubuntu 8.10.  The docking station has two display ports - DVI and VGA.  If I plug a monitor into each port, the monitor connected to the VGA port works, but I can not get any sign of life from the monitor connected to the DVI port.  I have installed the nvidia driver version 177 from Nvidia.

My question: is it at all possible to get this to work?  If yes - how? can anyone point me to some howto or some clues?

---

### Post by jtopland on 2009-03-30
I got success with Ubuntu using the HDMI, but I did not try sound. Though I remember having to use an older version(173?) of the driver in order to use HDMI output. Try the previous 173 driver.

I am using Slackware 12.1 now with the very latest nvidia driver(180.44). The hdmi/dvi does not at all, but vga does. Using older drivers does not seem to help. May be related to kernel configurations. But for Ubuntu this went fine, but with older drivers. For now I just use vga.

---

### Post by jtopland on 2009-03-30
**!!!FIX FOR USING HDMI/DVI WITH LATEST LINUX KERNEL!!!**

173.14.17 (beta) seems to be the *ONLY* driver which enables HDMI/DVI output and works for Linux kernel 2.6.28.8.

Previous NVidia drivers returns the annoying:
> ERROR: If you are using a Linux 2.4 kernel, please make sure
         you either have configured kernel sources matching your
         kernel or the correct set of kernel headers installed
         on your system.

         If you are using a Linux 2.6 kernel, please make sure
         you have configured kernel sources matching your kernel
         installed on your system. If you specified a separate
         output directory using either the "KBUILD_OUTPUT" or
         the "O" KBUILD parameter, make sure to specify this
         directory with the SYSOUT environment variable or with
         the equivalent nvidia-installer command line option.

         Depending on where and how the kernel sources (or the
         kernel headers) were installed, you may need to specify
         their location with the SYSSRC environment variable or
         the equivalent nvidia-installer command line option.

The driver is here: [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.17/NVIDIA-Linux-x86-173.14.17-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.17/NVIDIA-Linux-x86-173.14.17-pkg0.run)
:popcorn::popcorn::popcorn:

I hope NVidia some day updates their Linux drivers to support hdmi on out laptops. 180.44 (30. march 2009) still does not support it.

---

