---
title: "USBDevFS down in Kernel 2.6.24-24-generic instalation"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2009-08-10
It definitely looks as though I've made me a SNAFU concerning my souped-up Everex with Gigabyte/AMD/ATI hardware and Kernel 8.04-LTS.  When I pulled up USBview, it came back with the following error message:
```
Cannot open the file /proc/bus/usb/devices

Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted.
```
As it turns out, /proc/bus/usb is an empty directory as I type this, and Video4LinUX is also down on my system.  I checked /boot/config-2.6.24-24-generic and /boot/abi/2.6.24-24-generic and nothing appears amiss with either.  What other files could have broken?

---

### Post by bcschmerker on 2009-08-10
I ended up booting into Kernel 2.6.24-23-generic from GRUB, then purging and re-installing all Kernel 2.6.24-24-generic packages for Image, Modules and Headers.  Obviously something got thrown in the Kernel configuration prior to the reinstall.

Any hints on what to watch out for when adding Modules to a Kernel, especially which script files have to be kept in sync, would be much appreciated so that I can more quickly remedy this problem in the future.  Still cannot use USBView as of this post, but that could be indicative of a bug elsewhere.

---

### Post by kiplingw on 2010-04-04
Belated perhaps, but I too am having the same problem with usbview. Running Karmic.

---

### Post by bcschmerker on 2011-08-05
I am assuming this problem solved in later Kernels than the 2.6.24 chain due to further development on the UDev chain.  This Thread is hereby deprecated.

---

