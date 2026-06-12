---
title: "ubuntu 14.04 (32bit) server version install driver for GTX 750 TI"
date: 2016-04-26
forum: Hardware
---

### Post by zjhxmjl on 2016-04-26
Hi,guys!
          i try to install  driver for GTX 750 TI on ubuntu  14.04 (32bit) server version and I've had a success before! Probably as follows:
guides1:[http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)
guides2:[http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)
```

sudo add-apt-repository ppa:xorg-edgers/ppasudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install nvidia-355
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
sudo vim /etc/modprobe.d/blacklist.conf
add at the end this lines


    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv
sudo vim /etc/default/grub
find


    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


    and change it to


    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"


sudo update-grub


```
But now I tried many times without success,my system can not detect this video card?why?because kernel or other reason?
then i try to install driver from bin,so i download NVIDIA-Linux-x86-361.28.run
followed this guide:[http://tleyden.github.io/blog/2014/10/25/cuda-6-dot-5-on-aws-gpu-instance-running-ubuntu-14-dot-04/](http://tleyden.github.io/blog/2014/10/25/cuda-6-dot-5-on-aws-gpu-instance-running-ubuntu-14-dot-04/)
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic
sudo apt-get install linux-image-extra-virtual

```
I always get this prompt:
[ATTACH=CONFIG]268638[/ATTACH]

so any suggestion will be grateful!thanks.
this is my system info:
```
zjhxmjl@ubuntu:/etc/apt$ lsb_release -a && uname -rNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
4.2.0-27-generic
zjhxmjl@ubuntu:/etc/apt$ lspci -vnn | grep -i VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0283]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
    Subsystem: Dell Device [1028:0283]
    Flags: bus master, fast devsel, latency 0



```

this is my nvidia-installer.log
```
[   18.707259] init: lightdm main process (1024) terminated with status 127[   18.799979] init: plymouth-ready (startup) main process (197) terminated with status 1
[  376.165575] nvidia: module license 'NVIDIA' taints kernel.
[  376.165580] Disabling lock debugging due to kernel taint
[  376.177739] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[  376.183926] NVRM: No NVIDIA graphics adapter found!
[  376.184029] NVRM: NVIDIA init module failed!
[  506.073760] NVRM: No NVIDIA graphics adapter found!
[  506.073846] NVRM: NVIDIA init module failed!
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by mörgæs on 2016-04-26
Hi, welcome to the fora.
The lspci output does not show signs of Nvidia hardware. What exactly do you mean by

> **zjhxmjl said:**
> I've had a success before
?

---

### Post by zjhxmjl on 2016-04-26
yeah,I mean, before reinstall the system, once a successful!now i use the same way,but can not succeed!maybe i make a mistake?

---

### Post by Bucky Ball on 2016-04-26
*Thread moved to **Hardware**.*

> **mörgæs said:**
> The lspci output does not show signs of Nvidia hardware.

^^^
This.

Welcome. You don't have an NVidia GPU so not sure what you're trying to solve. You have this:

```
Intel Corporation 4 Series Chipset Integrated Graphics
```

Your laptop isn't working fine with the Intel graphics already or something else is the problem?

PS: If you know you have that Nvidia card in the machine, you might want to check it is in properly as there is no sign of it here. Check it is seated and connected properly and then give the output of this.

```
sudo lshw -C video
```

---

### Post by zjhxmjl on 2016-05-22
I  have to  install centos  7 to solve the problem  finally!:(

---

