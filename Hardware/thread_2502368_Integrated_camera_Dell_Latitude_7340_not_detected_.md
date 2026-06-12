---
title: "Integrated camera Dell Latitude 7340 not detected: Solution"
date: 2024-11-12
forum: Hardware
---

### Post by federicarike on 2024-11-12
Hi everyone,

the built-in webcam of my Latitude 7340 was not detected by Ubuntu 24.04 LTS, even after full OS reinstallation. Here is how to fix it:

[This is a DEVELOPMENT PPA - use OEM for stable release instead]

 **********************************************************************************************************************************
  sudo add-apt-repository ppa: oem-solutions-group/intel-ipu6
sudo apt install linux-modules-ipu6-generic-hwe-24.04 linux-modules-ivsc-generic-hwe-24.04
sudo apt install libcamhal-ipu6ep0
reboot 
************************************************************************************************
Of course, you can put 22.04 in place of 24.04, if this is your version. Hope this helps!

---

### Post by federicarike on 2024-12-23
The OEM archive for Intel MIPI camera drivers:

*Please remove any ipu6/ipu7 module or ppa repository before starting*

______________________________________________________________________________________
$ sudo apt install ubuntu-oem-keyring
$ sudo add-apt-repository "deb [http://dell.archive.canonical.com/](http://dell.archive.canonical.com/) noble somerville"
$ ubuntu-drivers list #install (sudo apt install) all the packages listed here - they depend on your hardware
...
libcamhal0
...
$ sudo apt install libcamhal0
_______________________________________________

For more: [https://wiki.ubuntu.com/IntelMIPICamera#Ubuntu_LTS_24.04](https://wiki.ubuntu.com/IntelMIPICamera#Ubuntu_LTS_24.04)

---

