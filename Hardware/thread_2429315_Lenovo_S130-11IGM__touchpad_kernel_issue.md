---
title: "Lenovo S130-11IGM / touchpad kernel issue ?"
date: 2019-10-16
forum: Hardware
---

### Post by poulsej on 2019-10-16
Does anyone here have this laptop with a working build running?
I've tried so many distros/flavors and really fed up with this thing.
There seems to be 3 problems..

1. Some Distros sit for hours booting
Ubuntu 18.04 and 19.04 never finish booting at all. They seem to have an issue with the internal emmc drive (I think) and sit timing out.

2. Network doesn't work
I know how to resolve this and have it working on Lubuntu 18.04 and Mint 19.2.

3. Touchpad doesn't work
It works on Lubuntu 18.04 running kernel 4.15.0.20 but when it upgrades to 4.15.0-65 the touchpad stops working.
I assume one of the minor releases between 20 and 65 broke something. The failure seems to be in the i2c_hid module.

---

### Post by #&amp;thj^% on 2019-10-16
Can you include this to help others to help you:
```
dmesg | grep i2c
```
and
```
dmesg | grep elan
```
Also could you also clear this up a bit, > "3. Touchpad doesn't work
It works on Lubuntu 18.04 running kernel 4.15.0.20 but when it upgrades to 4.15.0-65 the touchpad stops working.
I assume one of the minor releases between 20 and 65 broke something."
It is reported that kernel 4.18 supports most of your issues.

---

### Post by poulsej on 2019-10-16
So no elan but here's what it shows with 4.15.0-20....

```
root@S130-11IGM:~# dmesg | grep i2c
[    1.956816] i2c /dev entries driver
[    4.785348] i2c_hid i2c-SYNA3269:00: i2c-SYNA3269:00 supply vdd not found, using dummy regulator
[    5.707956] input: SYNA3269:00 06CB:7FB5 Touchpad as /devices/pci0000:00/0000:00:17.0/i2c_designware.0/i2c-0/i2c-SYNA3269:00/0018:06CB:7FB5.0006/input/input16
[    5.715880] hid-multitouch 0018:06CB:7FB5.0006: input,hidraw3: I2C HID v1.00 Mouse [SYNA3269:00 06CB:7FB5] on i2c-SYNA3269:00
root@S130-11IGM:~# grep i2c /var/log/Xorg.0.log
[     8.100] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:17.0/i2c_designware.0/i2c-0/i2c-SYNA3269:00/0018:06CB:7FB5.0006/input/input16/event15"
root@S130-11IGM:~# grep -i using /var/log/Xorg.0.log
[     7.521] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.521] (==) No Layout section.  Using the first Screen section.
[     7.521] (==) No screen section available. Using defaults.
    Using a default monitor configuration.
[     7.525] (++) using VT number 7
[     7.592] (II) modeset(0): using drv /dev/dri/card0
[     7.705] (II) modeset(0): Using exact sizes for initial modes
[     7.705] (II) modeset(0): Output eDP-1 using initial mode 1366x768 +0+0
[     7.705] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[     7.869] (II) Using input driver 'libinput' for 'Video Bus'
[     7.908] (II) Using input driver 'libinput' for 'Power Button'
[     7.934] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[     7.948] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[     7.967] (II) Using input driver 'libinput' for 'EasyCamera: EasyCamera'
[     8.011] (II) Using input driver 'synaptics' for 'SYNA3269:00 06CB:7FB5 Touchpad'
[     8.103] (II) Using input driver 'libinput' for 'Ideapad extra buttons'
[     8.126] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[     8.159] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[     8.159] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'


```

And here is it broken with 4.15.0-65

```
root@S130-11IGM:~# dmesg | grep i2c
[    1.944596] i2c /dev entries driver
[    5.123326] i2c_hid i2c-SYNA3269:00: i2c-SYNA3269:00 supply vdd not found, using dummy regulator
[   10.208258] i2c_hid i2c-SYNA3269:00: failed to reset device.
[   16.352055] i2c_hid i2c-SYNA3269:00: failed to reset device.
[   22.500101] i2c_hid i2c-SYNA3269:00: failed to reset device.
[   28.640264] i2c_hid i2c-SYNA3269:00: failed to reset device.
[   29.664264] i2c_hid i2c-SYNA3269:00: can't add hid device: -61
[   29.664604] i2c_hid: probe of i2c-SYNA3269:00 failed with error -61
root@S130-11IGM:~# grep -i using /var/log/Xorg.0.log
[    31.697] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.697] (==) No Layout section.  Using the first Screen section.
[    31.697] (==) No screen section available. Using defaults.
    Using a default monitor configuration.
[    31.699] (++) using VT number 7
[    31.728] (II) modeset(0): using drv /dev/dri/card0
[    31.801] (II) modeset(0): Using exact sizes for initial modes
[    31.801] (II) modeset(0): Output eDP-1 using initial mode 1366x768 +0+0
[    31.801] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.149] (II) Using input driver 'libinput' for 'Video Bus'
[    32.201] (II) Using input driver 'libinput' for 'Power Button'
[    32.234] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[    32.255] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[    32.284] (II) Using input driver 'libinput' for 'EasyCamera: EasyCamera'
[    32.334] (II) Using input driver 'libinput' for 'Ideapad extra buttons'
[    32.366] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    32.412] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'
[    32.413] (II) Using input driver 'libinput' for 'Logitech MX Anywhere 2'


```

---

### Post by poulsej on 2019-10-17
Are there any docs/guides on adding specific kernels??

---

### Post by #&amp;thj^% on 2019-10-17
Not sure how in depth you want to go but, Advanced: [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
Note the above **could** leave you with problems.
Another method is to just install the .debs: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

And still, you can add a PPA to play around with: [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa?field.series_filter=bionic](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa?field.series_filter=bionic)
More Info: [http://ubuntuhandbook.org/index.php/2018/08/uktool-tool-to-install-latest-kernels-ubuntu/](http://ubuntuhandbook.org/index.php/2018/08/uktool-tool-to-install-latest-kernels-ubuntu/)
With the PPA you will only need to install " ukuu ". 

**The way I would go is, you can upgrade kernel and keep it upgraded to future point Ubuntu releases by running**
```

sudo apt install linux-generic-hwe-18.04
```

As for now it will install the 4.18 kernel.

---

### Post by poulsej on 2019-10-18
Thanks for the links. I tried hwe-18.04 but it fails to boot. Just get's stuck at loading ramdisk.
Not sure how to see what is actually happening at this point.
Here's what's in boot.

```
root@ubuntu:/boot# ls -l
total 154992
-rw-r--r-- 1 root root  1536934 Apr 24  2018 abi-4.15.0-20-generic
-rw-r--r-- 1 root root   216807 Apr 24  2018 config-4.15.0-20-generic
-rw-r--r-- 1 root root   217362 Sep 17 17:12 config-4.15.0-65-generic
-rw-r--r-- 1 root root   224447 Sep 30 23:23 config-5.0.0-31-generic
drwx------ 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     4096 Oct 18 09:24 grub
-rw-r--r-- 1 root root 38864018 Oct 16 22:00 initrd.img-4.15.0-20-generic
-rw-r--r-- 1 root root 38925782 Oct 16 22:03 initrd.img-4.15.0-65-generic
-rw-r--r-- 1 root root 40360188 Oct 18 09:24 initrd.img-5.0.0-31-generic
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root        0 Apr 24  2018 retpoline-4.15.0-20-generic
-rw------- 1 root root  4038188 Apr 24  2018 System.map-4.15.0-20-generic
-rw------- 1 root root  4064177 Sep 17 17:12 System.map-4.15.0-65-generic
-rw------- 1 root root  4294610 Sep 30 23:23 System.map-5.0.0-31-generic
-rw------- 1 root root  8249080 Apr 24  2018 vmlinuz-4.15.0-20-generic
-rw------- 1 root root  8359576 Sep 17 17:20 vmlinuz-4.15.0-65-generic
-rw------- 1 root root  8769272 Oct  1 03:27 vmlinuz-5.0.0-31-generic

```

Here's the install output...
```

root@ubuntu:~# apt install linux-generic-hwe-18.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm6.0
Use 'apt autoremove' to remove it.
The following additional packages will be installed:
  linux-headers-5.0.0-31 linux-headers-5.0.0-31-generic linux-headers-generic-hwe-18.04 linux-image-5.0.0-31-generic linux-image-generic-hwe-18.04
  linux-modules-5.0.0-31-generic linux-modules-extra-5.0.0-31-generic thermald
Suggested packages:
  fdutils linux-hwe-doc-5.0.0 | linux-hwe-source-5.0.0 linux-hwe-tools
The following NEW packages will be installed
  linux-generic-hwe-18.04 linux-headers-5.0.0-31 linux-headers-5.0.0-31-generic linux-headers-generic-hwe-18.04 linux-image-5.0.0-31-generic
  linux-image-generic-hwe-18.04 linux-modules-5.0.0-31-generic linux-modules-extra-5.0.0-31-generic thermald
0 to upgrade, 9 to newly install, 0 to remove and 1 not to upgrade.
Need to get 67.4 MB of archives.
After this operation, 332 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-5.0.0-31-generic amd64 5.0.0-31.33~18.04.1 [13.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-5.0.0-31-generic amd64 5.0.0-31.33~18.04.1 [8,409 kB]                                   
Get:3 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-extra-5.0.0-31-generic amd64 5.0.0-31.33~18.04.1 [33.2 MB]                            
Get:4 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-generic-hwe-18.04 amd64 5.0.0.31.88 [2,428 B]                                           
Get:5 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-5.0.0-31 all 5.0.0-31.33~18.04.1 [10.8 MB]                                            
Get:6 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-5.0.0-31-generic amd64 5.0.0-31.33~18.04.1 [1,174 kB]                                 
Get:7 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-generic-hwe-18.04 amd64 5.0.0.31.88 [2,384 B]                                         
Get:8 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-generic-hwe-18.04 amd64 5.0.0.31.88 [1,884 B]                                                 
Get:9 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 thermald amd64 1.7.0-5ubuntu5 [192 kB]                                                              
Fetched 67.4 MB in 31s (2,184 kB/s)                                                                                                                                     
Selecting previously unselected package linux-modules-5.0.0-31-generic.
(Reading database ... 140101 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.0.0-31-generic_5.0.0-31.33~18.04.1_amd64.deb ...
Unpacking linux-modules-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Selecting previously unselected package linux-image-5.0.0-31-generic.
Preparing to unpack .../1-linux-image-5.0.0-31-generic_5.0.0-31.33~18.04.1_amd64.deb ...
Unpacking linux-image-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Selecting previously unselected package linux-modules-extra-5.0.0-31-generic.
Preparing to unpack .../2-linux-modules-extra-5.0.0-31-generic_5.0.0-31.33~18.04.1_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Selecting previously unselected package linux-image-generic-hwe-18.04.
Preparing to unpack .../3-linux-image-generic-hwe-18.04_5.0.0.31.88_amd64.deb ...
Unpacking linux-image-generic-hwe-18.04 (5.0.0.31.88) ...
Selecting previously unselected package linux-headers-5.0.0-31.
Preparing to unpack .../4-linux-headers-5.0.0-31_5.0.0-31.33~18.04.1_all.deb ...
Unpacking linux-headers-5.0.0-31 (5.0.0-31.33~18.04.1) ...
Selecting previously unselected package linux-headers-5.0.0-31-generic.
Preparing to unpack .../5-linux-headers-5.0.0-31-generic_5.0.0-31.33~18.04.1_amd64.deb ...
Unpacking linux-headers-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Selecting previously unselected package linux-headers-generic-hwe-18.04.
Preparing to unpack .../6-linux-headers-generic-hwe-18.04_5.0.0.31.88_amd64.deb ...
Unpacking linux-headers-generic-hwe-18.04 (5.0.0.31.88) ...
Selecting previously unselected package linux-generic-hwe-18.04.
Preparing to unpack .../7-linux-generic-hwe-18.04_5.0.0.31.88_amd64.deb ...
Unpacking linux-generic-hwe-18.04 (5.0.0.31.88) ...
Selecting previously unselected package thermald.
Preparing to unpack .../8-thermald_1.7.0-5ubuntu5_amd64.deb ...
Unpacking thermald (1.7.0-5ubuntu5) ...
Setting up thermald (1.7.0-5ubuntu5) ...
Created symlink /etc/systemd/system/dbus-org.freedesktop.thermald.service &#8594; /lib/systemd/system/thermald.service.
Created symlink /etc/systemd/system/multi-user.target.wants/thermald.service &#8594; /lib/systemd/system/thermald.service.
Setting up linux-modules-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Setting up linux-image-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.15.0-65-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.15.0-65-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-5.0.0-31-generic
I: /initrd.img is now a symlink to boot/initrd.img-5.0.0-31-generic
Setting up linux-headers-5.0.0-31 (5.0.0-31.33~18.04.1) ...
Setting up linux-headers-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.0.0-31-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j4 KVER=5.0.0-31-generic.......................................
Signing module:
 - /var/lib/dkms/rtl8821ce/v5.5.2_34066.20190614/5.0.0-31-generic/x86_64/module/8821ce.ko
Secure Boot not enabled on this system.
cleaning build area...

DKMS: build completed.

8821ce.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-31-generic/updates/dkms/

depmod...

DKMS: install completed.
   ...done.
Setting up linux-headers-generic-hwe-18.04 (5.0.0.31.88) ...
Setting up linux-modules-extra-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
Setting up linux-image-generic-hwe-18.04 (5.0.0.31.88) ...
Setting up linux-generic-hwe-18.04 (5.0.0.31.88) ...
Processing triggers for dbus (1.12.2-1ubuntu1.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for linux-image-5.0.0-31-generic (5.0.0-31.33~18.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.0.0-31-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.0.0-31-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-31-generic
Found initrd image: /boot/initrd.img-5.0.0-31-generic
Found linux image: /boot/vmlinuz-4.15.0-65-generic
Found initrd image: /boot/initrd.img-4.15.0-65-generic
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Adding boot menu entry for EFI firmware configuration
done

```

---

### Post by poulsej on 2019-10-18
So I booted 5.0.0.31 recovery and found the issue with reading the internal emmc drive. I built a usb drive with the same version which does eventually start after a huge amount of time but it can't see the emmc.
So going from 4.15.0-20 to 5.0.0.31 might fix the touchpad but introduces all kinds of pain with the emmc.

For the moment I've modified grub and using 4.15.0-20 as the default kernel.

The beginning of the kernel log in this bug report shows the exact same behaviour.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=930815](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=930815)

---

