---
title: "USB Keyboard and mouse don't work after Kernel upgrade"
date: 2014-09-02
forum: Hardware
---

### Post by Adolfo_Sanchez on 2014-09-02
Hello

I'm using Ubuntu 14.04 on a Haswell platform

I did an upgrade from the kernel 13.3.0-32 to 13.3.0-33 amd64 using the commands

sudo add-apt-repository ppa:kernel-ppa/ppa 
sudo apt-get update
sudo apt-get install linux-headers-3.13.0-33-generic linux-image-3.13.0-33-generic

After the upgrade, when I enter the login screen, the mouse and the keyboard get totally unresponsive.

In grub they keyboard is still working.

I tried adding the option ohci_pci to the modules an updating the initramfs.

When I select the older kernel everything works fine.

I have also discovered that for some reason I have less modules in /lib/*version*/modules/kernel/ for the newer kernel (see attachment)


Any help would be appreciated.

---

