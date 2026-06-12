---
title: "Ubuntu, Kubuntu, &amp; Mint current versions black screen with nvidia drivers"
date: 2016-12-26
forum: Hardware
---

### Post by cmedley on 2016-12-26
I was running Kubuntu 15.10 before I decided to upgrade to 16.10.  After the upgrade, the nvidia drivers cause a boot to a black screen.  using nomodeset does not help.  I would use nouveau, but it fails on load as well.  I don't suspect hardware because the video works and 15.10 had no issue before I upgraded.  To get KDE back, I can ctrl-alt-F1, purge nv*, then reboot.
  
what I get from inxi before I install the nvidia drivers:
```
$ inxi -G
Graphics:  Card: NVIDIA G72 [GeForce 7300 LE]                                           
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) FAILED: nouveau 
           Resolution: 640x480@73.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 12.0.3
```

```
$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0 ==
vendor   : NVIDIA Corporation                                                           
modalias : pci:v000010DEd000001D1sv00001462sd00000345bc03sc00i00                        
model    : G72 [GeForce 7300 LE] (7300LE PCI Express Graphics Adapter)
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304 - distro non-free recommended

```


can anyone assist?

---

### Post by cmedley on 2016-12-29
No ideas?  Is there any more information I can provide?  I swapped the card out for a newer Nvidia card but I get the same results with a different driver version.  I did get the VESA driver to work.

---

