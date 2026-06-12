---
title: "No Boot from SD, ? initrd missing Modules"
date: 2010-03-25
forum: Hardware
---

### Post by SBFree on 2010-03-25
I am trying to create a bootable Netbook Remix (2.6.31-14) image on an SDHC card. The machine boots fine from USB and trys to boot from the SDHC but doesn't. I have been able to use Grub2 to load the kernel and initrd images on the SDHC card manually but at boot get a message like:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/mmcblk[COLOR="Red"]01p[/COLOR] does not exist. Dropping to shell 

If I boot Netbook Remix from the USB stick and look at the SDHC card with GParted the bootable partition is labled /dev/mmcblk[COLOR="Red"]0p1[/COLOR]
In GParted the device is labeled /dev/mmcblk0

At one point I ran cat /proc/modules once system booted from USB and say modules for drive but running it from the SDHC card had only the following modules: fbcom,tileblit,font,bitblit,softcursor,
usbhid,ohci,ieee,i915,drm,i2c_algo,video,e1000e,output 2780,
intel_agp,agpgart (module names abbreviated)

It looked like all my HD storage mods were missing. At this point I do not know how to really check which modules are in the initrd I am loading or why the device name is slightly different when booted from the system in USB as opposed to the name given in the error when I try to boot from SDHC. Any insights or guidance  is appreciated.

Scott

---

