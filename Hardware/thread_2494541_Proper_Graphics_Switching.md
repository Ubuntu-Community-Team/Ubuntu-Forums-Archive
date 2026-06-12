---
title: "Proper Graphics Switching"
date: 2024-01-19
forum: Hardware
---

### Post by TenPlus1 on 2024-01-19
Does a plugin or tool exist that allows the user to easily switch between graphics cards and properly disable or suspend whichever one is not in use ???

Many laptops come with Intel or AMD by default with an additional Nvidia card for power-use, but I have never seen an easy way to switch between them easily on linux.

---

### Post by #&amp;thj^% on 2024-01-19
I feel like I'm walking into a "I already know that" but i will take my chance to help.
```
apt show nvidia-prime
Package: nvidia-prime
Version: 0.8.17.2
Priority: optional
Section: admin
Origin: Ubuntu
Maintainer: Alberto Milone <alberto.milone@canonical.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 50.2 kB
Provides: hybrid-graphics
Depends: python3:any
Conflicts: hybrid-graphics
Breaks: ubuntu-drivers-common (<< 1:0.2.89)
Replaces: hybrid-graphics
Task: ubuntu-mate-core, ubuntu-mate-desktop
Download-Size: 10.4 kB
APT-Manual-Installed: no
APT-Sources: http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
Description: Tools to enable NVIDIA's Prime
 This is a set of tools which will enable
 NVIDIA's Prime on MUXless systems.

```
And you can as well mask the unused GPU via systemd.
I have AMD on mine as well as nVidia.
```
prime-select query
intel

```
```
systemctl | grep -e nvidia -e masked
&#9679; sys-bus-pci-drivers-nvidia.device                                                                                                                         masked active plugged   /sys/bus/pci/drivers/nvidia
  nvidia-persistenced.service                                                                                                                               loaded active running   NVIDIA Persistence Daemon


```
As far as a point and click On Off toggle, I'm afraid nothing like that exists yet.
```
sudo prime-select nvidia
Info: selecting the nvidia profile
Deleting /lib/modprobe.d/nvidia-runtimepm.conf
Updating the initramfs. Please wait for the operation to complete:
Done
```
```
prime-select query
nvidia

```
I'm guessing you already knew all the above though.

---

### Post by MAFoElffen on 2024-01-20
My Workstation is a bit more complex and no-one else in their right-mind would do this, because it is very much out of the ordinary.

What you are describing is "possible", but not "plausible". Should I explain that statement?

My workstation has many graphics and hardware options, where I use things there in different ways, for different things I want to do... To do that, there is no flip of a switch or toggle. It requires the hardware to be configured differently for each scenario by two methods:

Method one takes a multi-boot through the grub2 menu, which boot's different instances of installed OS'es configured different ways.

Method two takes plugging in different drives into my drive bays, and using the BIOS to boot to those drives, to boot an OS which takes over total control of the hardware (vSphere/vCenter)...

Both take a whole lot of prep work to setup, and to maintain. Like I just explained to someone else earlier today, that machine is the result of 14 years of my Workstation Test-Bench evolution, trial and errors.

Most people setup their PC (once) to be static, and stable.

"Just because something is possible doesn't make it a good idea." That adaptability and flexibility comes with a cost.

---

