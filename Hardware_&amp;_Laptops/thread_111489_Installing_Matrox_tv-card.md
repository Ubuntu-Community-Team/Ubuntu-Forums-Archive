---
title: "Installing Matrox tv-card"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by Kiwinote on 2006-01-02
I have a matrox rainbow runner g series card that is not officialy supported in linux, however I have found [a site with a unofficial driver]("http://marvel.sourceforge.net/"), but I need some help installing it. My questions are in red and the readme is in blue

Thanks,
Kiwinote


[COLOR="Blue"]This is a driver for Matrox video cards with TV capture capabilities.
This file was last updated on 20040105 for the Linux 2.6.7 kernel.

To build this driver perform the following steps:

        - Obtain and configure a Linux 2.6.7 (or later) kernel.  Make sure
          the following options are enabled:
              CONFIG_MODULES,
              CONFIG_I2C, CONFIG_I2C_ALGOBIT,
              CONFIG_FB, CONFIG_FB_MATROX, CONFIG_FB_MATROX_G450,
              CONFIG_FB_MATROX_I2C,
              CONFIG_VIDEO_DEV, CONFIG_VIDEO_BT848[COLOR="Red"]I managed to do this[/COLOR]

        - Patch the kernel with the included kernel-2.6.7.patch file.  For
          example:
              cd /path/to/linux/soruce/[COLOR="Red"]In which folder is the source?[/COLOR]
              patch -p1 < /path/to/driver_fb/kernel-2.6.7.patch
          And then build and install the kernel.[COLOR="Red"]How do I do this?[/COLOR]

        - Build the driver_fb source code:
              cd /path/to/driver_fb
              make LINUX_SOURCE=/path/to/linux/source/

To load the driver:

        - Run the included iv script as root.  For example:
              su -
              cd /path/to/driver_fb
              ./iv[/COLOR]

---

