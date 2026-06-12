---
title: "nVidia Drivers Questions"
date: 2009-05-14
forum: Hardware
---

### Post by Vigh on 2009-05-14
hi, I am running a TOSHIBA satellite pro 6100, everything is working fine on ubuntu 9.04 except for the graphics card drivers, now whenever I install the drivers using either envyng or the hardware drivers option in administration it promptly installs driver 96.43.10, which results in any program requiring 3d acceleration to cause the computer to crash and also limits the screen resolution to 800x600, i then proceeded to download nvdias old drivers specifically for my graphics card a geforce4 go 420 mobile GPU, the driver 1.0-9639, I then disabled the GDM (xserv,xorg) a requirement to install the nvidia drivers manually, but kept on getting the following error when attempting to install the drivers manually

ERROR: If you are using a Linux 2.6 kernel, please make sure
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

All ideas and comments welcome. Thanks.

---

