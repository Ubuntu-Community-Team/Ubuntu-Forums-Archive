---
title: "AMD Carrizo Laptop  Can Only Boot to Low Graphics Mode"
date: 2015-08-23
forum: Hardware
---

### Post by ping-wu on 2015-08-23
My company recently bought a new HP Pavilion laptop with the new AMD Carrizo A10 CPU and its built-in video chip.  We have tested the new computer with a Ubuntu LiveUSB (14.04.2 and 14.04.3).  In both instances, we can only boot into low graphics mode (VGA, 640 x 480).

I have tried to boot with the NOMODESET and/or acpi=off kernel parameters, but both to no avail.

When I go back to the office tomorrow, are there any options that I can try to boot Ubuntu in full graphic mode from the LiveUSB?

---

### Post by Petro Dawg on 2015-08-23
New chips usually take a while before they are supported by Linux, the drivers have to be written.  While you are logged in in the low graphics mode, you might check the "additional drivers" application to see if there are any AMD/ATI Radeon drivers available yet.  Otherwise you may need to go the AMD website and see if they have released Linux drivers yet for your chip.

---

### Post by ping-wu on 2015-08-24
Thanks.  At the present time, I am mainly interested in modifying the kernel parameters or something similarly simple.

But I will also try to install Ubuntu into this new machine tomorrow, followed by flgrx driver.  In the meantime, if there are any suggestions, or what's the best approach to install the flgrx driver, will really appreciate it.  Thanx.

---

### Post by Yellow Pasque on 2015-08-24
It looks like Ubuntu hasn't added the carrizo firmware to their linux-firmware package yet. [http://people.freedesktop.org/~agd5f/radeon_ucode/carrizo/](http://people.freedesktop.org/~agd5f/radeon_ucode/carrizo/)
Try manually downloading all of those files and putting them in a firmware directory (and then reboot):
```
sudo mkdir /lib/firmware/carrizo
cd <your download directory>
sudo cp carrizo* /lib/firmware/carrizo
```

---

### Post by Yellow Pasque on 2015-08-24
> **Petro Dawg said:**
> you might check the "additional drivers" application to see if there are any AMD/ATI Radeon drivers available yet.  Otherwise you may need to go the AMD website and see if they have released Linux drivers yet for your chip.

I doubt the Additional Drivers utility has had the Carrizo PCI ID's added to it. If the user wishes to run the proprietary fglrx/Catalyst driver, s/he should install fglrx-updates package (rather than trying to download drivers directly from AMD). The updated fglrx drivers in Trusty do support Carrizo:
```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

---

### Post by ping-wu on 2015-08-25
> **Temüjin said:**
> I doubt the Additional Drivers utility has had the Carrizo PCI ID's added to it. If the user wishes to run the proprietary fglrx/Catalyst driver, s/he should install fglrx-updates package (rather than trying to download drivers directly from AMD). The updated fglrx drivers in Trusty do support Carrizo:
```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

I have installed fglrx-updates and/or fglrx-amdcccle-updates, both solved the low graphics mode problem.

However, there are also problems with wireless (RTL8723BE) and suspend.  The wireless problem should be easy to solve, but the suspend problem is a toughie.  This computer is simply too new, but it runs very well, very cool (as in temperature), has a long battery life, and is very reasonably priced.

Any suggestion regarding wireless and suspend will be appreciated.

---

### Post by Yellow Pasque on 2015-08-25
Suspend is very difficult to troubleshoot. Did it suspend properly before you installed video driver?

> there are also problems with wireless (RTL8723BE)
Describe the problem. Also, confirm your kernel version:
```
uname -a
```

---

### Post by ping-wu on 2015-08-25
> **Temüjin said:**
> Suspend is very difficult to troubleshoot. Did it suspend properly before you installed video driver?

Suspend problem existed before installing the fglrx drivers.  Yes, suspend problems can be spooky, but any suggestions will be welcome.


> Describe the problem. Also, confirm your kernel version:
```
uname -a
```

This is how I (sort of) solved the problem:

sudo apt-get install linux-headers-generic build-essential git
git clone [http://github.com/lwfinger/rtlwifi_new](http://github.com/lwfinger/rtlwifi_new)
cd rtlwifi_new
make clean
sudo make install
sudo modprobe rtl8723be

sudo reboot

I said "soft of", because the wireless connection was not very stable.

---

### Post by ping-wu on 2015-08-25
> **Temüjin said:**
> 

Describe the problem. Also, confirm your kernel version:
```
uname -a
```

"uname -a" produced the following results:

Linux amd15 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ping-wu on 2015-08-25
> **ping-wu said:**
> 
I said "soft of", because the wireless connection was not very stable.

sudo lshw -C network showed the following (in part):

description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: (deleted)
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-26-generic firmware=N/A ip=192.168.0.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 ioport:d000(size=256) memory:ff400000-ff403fff


(The suspend and wireless problems will be re-submitted in a new thread.)

---

### Post by ping-wu on 2015-08-30
> **ping-wu said:**
> (The suspend and wireless problems will be re-submitted in a new thread.)

These problems seem to have been solved in Ubuntu 15.10 beta 1 (with fglrx-amdcccle-updates; otherwise still boots into SVGA 800 x 600 video mode).

---

### Post by Yellow Pasque on 2015-08-30
> otherwise still boots into SVGA 800 x 600 video mode
Did you install the firmware as suggested in my previous post?

---

### Post by Yellow Pasque on 2015-08-30
Actually, you should already have the firmware if you're running a fully updated 15.10 install, as Ubuntu added the firmware a few days ago (in linux-firmware 1.147).

If you're still interested in using the open source driver, post the /var/log/Xorg.0.log file from a boot when you only have 800x600 (use code tags).

---

### Post by ping-wu on 2015-09-03
> **Temüjin said:**
> Actually, you should already have the firmware if you're running a fully updated 15.10 install, as Ubuntu added the firmware a few days ago (in linux-firmware 1.147).

If you're still interested in using the open source driver, post the /var/log/Xorg.0.log file from a boot when you only have 800x600 (use code tags).

Thanks.  I will do a fresh installation in a few days.

Any further suggestions, please let me know.

---

### Post by Yellow Pasque on 2015-09-03
So I have discovered that Carrizo needs very recent components for open-source 3D acceleration (4.2 kernel, libdrm 2.6.43, mesa 11.x). Ubuntu 15.10 will not have the necessary pieces by default, but I'm guessing "oibaf" will add updated components once 15.10 is released as he usually does ( [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) ). If you don't feel comfortable running a PPA and non-standard kernel, you could run the proprietary fglrx/Catalyst driver or wait until Ubuntu 16.04LTS is released.

---

### Post by ping-wu on 2015-09-19
> **ping-wu said:**
> I have installed fglrx-updates and/or fglrx-amdcccle-updates, both solved the low graphics mode problem.

However, there are also problems with wireless (RTL8723BE) and suspend.  The wireless problem should be easy to solve, but the suspend problem is a toughie.  This computer is simply too new, but it runs very well, very cool (as in temperature), has a long battery life, and is very reasonably priced.

Any suggestion regarding wireless and suspend will be appreciated.

I burned and booted from a liveUSB with today's daily build ofn 15.10 (which has been upgraded to Linux 4.2 kernel).  No problem with suspend or wireless.  No need to install the fglrx driver, either (can't install it on a liveUSB anyway :D).

Awesome! Awesome! Awesome!!!

---

