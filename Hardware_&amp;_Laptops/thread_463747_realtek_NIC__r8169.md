---
title: "realtek NIC  r8169"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by X0RZALE on 2007-06-04
Im having difficulty setting up XUBUNTU on my Asus Z92Tseries laptop.  Everything is working ok, accept that after install, the drivers for my wired ethernet aren't working.  As for the wireless I have nothing to test it with anyway.  I have installed the r8169 drivers using: 

# sudo make clean modules 
# sudo make install
# sudo depmod -a
# sudo insmod ./src/r8169.ko

I know I need to configure something to enable the driver to work.  It doesn't come up when I reboot.  I would just like to know the steps for setting up the device properly so it will work.

It will be very handy to know how to configure network drivers and devices etc.

---

### Post by X0RZALE on 2007-06-04
I just figured out that if I enable the boot rom for this device at startup in the bios the driver works floorlessly without any extra configuration other then making and installing as done above.  Phew what a relief.  

Seriously, before doing anything check that the device is fully enabled in the bios.

---

