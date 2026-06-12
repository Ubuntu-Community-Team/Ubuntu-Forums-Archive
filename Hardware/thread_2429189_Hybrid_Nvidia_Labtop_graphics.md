---
title: "Hybrid Nvidia Labtop graphics"
date: 2019-10-14
forum: Hardware
---

### Post by mediamakerman on 2019-10-14
I am having trouble adding a driver to use the nvidia graphics card on a laptop that has hybrid graphics or dual cards.

Below is the computer I am attempting to install an Unbuntu based system on and the model of computer below on the makers support webpage.

[https://www.dell.com/support/home/us/en/04/product-support/servicetag/0-OVBUVUtXMHJDQ0toWi8wbGpjZFJidz090/overview](https://www.dell.com/support/home/us/en/04/product-support/servicetag/0-OVBUVUtXMHJDQ0toWi8wbGpjZFJidz090/overview)

Even after following the steps from the URL below the screen on the machine shuts down after the boot screen with the power still on with the unit.

[https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/](https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/)

Below is the commands typed in to the terminal and thank you for your help.

```
mediamaker@MediaMakerMint:~$ sudo lshw -C display
[sudo] password for mediamaker:                     
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 5500
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:a9000000-a9ffffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:50 memory:aa000000-aaffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:ab000000-ab07ffff
mediamaker@MediaMakerMint:~$ apt search nvidia-driver
p   nvidia-driver-390               - NVIDIA driver metapackage                 
p   nvidia-driver-390:i386          - NVIDIA driver metapackage                 
p   nvidia-driver-418               - Transitional package for nvidia-driver-430
p   nvidia-driver-430               - NVIDIA driver metapackage                 
v   nvidia-driver-binary            -                                           
v   nvidia-driver-binary:i386       -      
mediamaker@MediaMakerMint:~$ apt-cache search nvidia-driver
nvidia-384 - Transitional package for nvidia-driver-390
nvidia-384-dev - Transitional package for nvidia-driver-390
nvidia-driver-390 - NVIDIA driver metapackage
nvidia-headless-390 - NVIDIA headless metapackage
nvidia-headless-no-dkms-390 - NVIDIA headless metapackage - no DKMS
xserver-xorg-video-nvidia-390 - NVIDIA binary Xorg driver
nvidia-340 - NVIDIA binary driver - version 340.107
nvidia-driver-418 - Transitional package for nvidia-driver-430
nvidia-driver-430 - NVIDIA driver metapackage
nvidia-headless-430 - NVIDIA headless metapackage
nvidia-headless-no-dkms-430 - NVIDIA headless metapackage - no DKMS
xserver-xorg-video-nvidia-430 - NVIDIA binary Xorg driver
mediamaker@MediaMakerMint:~$ sudo apt install nvidia-driver-390
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390
  libnvidia-encode-390 libnvidia-fbc1-390 libnvidia-gl-390 libnvidia-ifr1-390
  nvidia-compute-utils-390 nvidia-dkms-390 nvidia-kernel-common-390 nvidia-kernel-source-390
  nvidia-utils-390 xserver-xorg-video-nvidia-390
Recommended packages:
  nvidia-settings nvidia-prime libnvidia-compute-390:i386 libnvidia-decode-390:i386
  libnvidia-encode-390:i386 libnvidia-ifr1-390:i386 libnvidia-fbc1-390:i386 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390
  libnvidia-encode-390 libnvidia-fbc1-390 libnvidia-gl-390 libnvidia-ifr1-390
  nvidia-compute-utils-390 nvidia-dkms-390 nvidia-driver-390 nvidia-kernel-common-390
  nvidia-kernel-source-390 nvidia-utils-390 xserver-xorg-video-nvidia-390
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.2 MB of archives.
After this operation, 200 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-cfg1-390 amd64 390.116-0ubuntu0.18.04.1 [71.9 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-common-390 all 390.116-0ubuntu0.18.04.1 [12.0 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-compute-390 amd64 390.116-0ubuntu0.18.04.1 [20.6 MB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-decode-390 amd64 390.116-0ubuntu0.18.04.1 [1,122 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-encode-390 amd64 390.116-0ubuntu0.18.04.1 [54.2 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-fbc1-390 amd64 390.116-0ubuntu0.18.04.1 [43.2 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-gl-390 amd64 390.116-0ubuntu0.18.04.1 [14.3 MB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-ifr1-390 amd64 390.116-0ubuntu0.18.04.1 [70.8 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-compute-utils-390 amd64 390.116-0ubuntu0.18.04.1 [70.3 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-kernel-source-390 amd64 390.116-0ubuntu0.18.04.1 [8,432 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-kernel-common-390 amd64 390.116-0ubuntu0.18.04.1 [12.2 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-dkms-390 amd64 390.116-0ubuntu0.18.04.1 [28.1 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-utils-390 amd64 390.116-0ubuntu0.18.04.1 [327 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 xserver-xorg-video-nvidia-390 amd64 390.116-0ubuntu0.18.04.1 [1,616 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 nvidia-driver-390 amd64 390.116-0ubuntu0.18.04.1 [394 kB]
Fetched 47.2 MB in 18s (2,650 kB/s)                                                               
Selecting previously unselected package libnvidia-cfg1-390:amd64.
(Reading database ... 291236 files and directories currently installed.)
Preparing to unpack .../00-libnvidia-cfg1-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-cfg1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-common-390.
Preparing to unpack .../01-libnvidia-common-390_390.116-0ubuntu0.18.04.1_all.deb ...
Unpacking libnvidia-common-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-compute-390:amd64.
Preparing to unpack .../02-libnvidia-compute-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-compute-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-decode-390:amd64.
Preparing to unpack .../03-libnvidia-decode-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-decode-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-encode-390:amd64.
Preparing to unpack .../04-libnvidia-encode-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-encode-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-fbc1-390:amd64.
Preparing to unpack .../05-libnvidia-fbc1-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-fbc1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-gl-390:amd64.
Preparing to unpack .../06-libnvidia-gl-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-gl-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package libnvidia-ifr1-390:amd64.
Preparing to unpack .../07-libnvidia-ifr1-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-ifr1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-compute-utils-390.
Preparing to unpack .../08-nvidia-compute-utils-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-compute-utils-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-kernel-source-390.
Preparing to unpack .../09-nvidia-kernel-source-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-kernel-source-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-kernel-common-390.
Preparing to unpack .../10-nvidia-kernel-common-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-kernel-common-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-dkms-390.
Preparing to unpack .../11-nvidia-dkms-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-dkms-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-utils-390.
Preparing to unpack .../12-nvidia-utils-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-utils-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package xserver-xorg-video-nvidia-390.
Preparing to unpack .../13-xserver-xorg-video-nvidia-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking xserver-xorg-video-nvidia-390 (390.116-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-driver-390.
Preparing to unpack .../14-nvidia-driver-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-driver-390 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-kernel-source-390 (390.116-0ubuntu0.18.04.1) ...
Setting up libnvidia-fbc1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up libnvidia-compute-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-kernel-common-390 (390.116-0ubuntu0.18.04.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-4.15.0-54-generic
cryptsetup: WARNING: Invalid source device /swapfile
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
Setting up libnvidia-cfg1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up xserver-xorg-video-nvidia-390 (390.116-0ubuntu0.18.04.1) ...
Setting up libnvidia-decode-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-compute-utils-390 (390.116-0ubuntu0.18.04.1) ...
Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory
Adding system user `nvidia-persistenced' (UID 122) ...
Adding new group `nvidia-persistenced' (GID 129) ...
Adding new user `nvidia-persistenced' (UID 122) with group `nvidia-persistenced' ...
Not creating home directory `/nonexistent'.
Setting up libnvidia-common-390 (390.116-0ubuntu0.18.04.1) ...
Setting up libnvidia-encode-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-utils-390 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-dkms-390 (390.116-0ubuntu0.18.04.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-4.15.0-54-generic
cryptsetup: WARNING: Invalid source device /swapfile
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-390.116 DKMS files...
Building for 4.15.0-54-generic 4.15.0-65-generic
Building for architecture x86_64
Building initial module for 4.15.0-54-generic
Secure Boot not enabled on this system.
Done.


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-54-generic/kernel/drivers/char/drm/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-54-generic/kernel/drivers/char/drm/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-54-generic/kernel/drivers/char/drm/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-54-generic/kernel/drivers/char/drm/


depmod...


DKMS: install completed.
Building initial module for 4.15.0-65-generic
Secure Boot not enabled on this system.
Done.


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-65-generic/kernel/drivers/char/drm/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-65-generic/kernel/drivers/char/drm/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-65-generic/kernel/drivers/char/drm/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-65-generic/kernel/drivers/char/drm/


depmod...


DKMS: install completed.
Setting up libnvidia-gl-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up libnvidia-ifr1-390:amd64 (390.116-0ubuntu0.18.04.1) ...
Setting up nvidia-driver-390 (390.116-0ubuntu0.18.04.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-65-generic
cryptsetup: WARNING: Invalid source device /swapfile
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
```


Rebooted computer only to have no screen to come on. The device manager does not see the nvidia card in the GUI, however the command line seems to detect it. Wonder if their is is way to force the GUI to see that the card is their or a file I could install for this card from a .deb file?

 ```
 product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
```
Could it be a bug in the Linux Mint OS desktop Gui?

---

### Post by mediamakerman on 2019-10-14
Secure boot is off too, so not sure what else would be the problem? Thank you for time.

---

### Post by wildmanne39 on 2019-10-14
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

