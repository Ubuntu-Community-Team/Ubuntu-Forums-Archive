---
title: "sudo modprobe lt_modem | FATAL: module not found"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by wook on 2006-02-27
I'm trying to setup my internal modem on a IBMA21M laptop with Breezy.  I followed the [ DialupModemHowto ](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29#head-cc17ea0ff3df391406e74527f1aed569be04709fon) the Ubuntu Wiki.  scanModem found the internal modem has a supported Lucent/Agere DSP (digital signal processing) chipset,  When entering the commands $ sudo modprobe lt_serial or
  $ sudo modprobe lt_modem, I get a FATAL: module not found.  Next, I changed the grub boot commands /boot/grub/menu.lst as follows (pci=routeirq is new):
```
 ## ## Start Default Options ##
  ## default kernel options
  ## default kernel options for automagic boot options
  ## If you want special options for specifiv kernels use kopt_x_y_z
  ## where x.y.z is kernel version. Minor versions can be omitted.
  ## e.g. kopt=root=/dev/hda1 ro
  # kopt=root=/dev/hda1 ro pci=routeirq
```

I updated grub: $ sudo update-grub

I reentered the commands $ sudo modprobe lt_serial and
  $ sudo modprobe lt_modem; same error.

Any help would be appreciated.

---

