---
title: "Broadcom Driver fails to install."
date: 2010-11-20
forum: Hardware
---

### Post by isoscelesrectangle on 2010-11-20
Running Linux Mint 9 KDE on a Studio 1458. Installing the broadcom drivers for my brcm 43224 or something like that. No dice. Here's my jockey.log output. The driver installed flawlessly in Vanilla Ubuntu Lucid, Maverick, and Linux Mint 10RC GNOME. Is there anything I'm doing wrong? 
```
Setting up linux-libc-dev (2.6.32-25.45) ...
Setting up libc-dev-bin (2.11.1-0ubuntu7.5) ...
Setting up libc6-dev (2.11.1-0ubuntu7.5) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up manpages-dev (3.23-1) ...
Setting up patch (2.6-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic

2010-11-20 13:58:45,392 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-11-20 13:58:45,393 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-11-20 13:58:45,468 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-11-20 13:58:53,957 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-11-20 13:58:54,359 DEBUG: fglrx is not the alternative in use
2010-11-20 13:58:54,395 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-11-20 13:58:54,520 DEBUG: fglrx is not the alternative in use
2010-11-20 13:58:54,548 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

ifconfig: 
```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:83:cb:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7400 (7.4 KB)  TX bytes:7400 (7.4 KB)

usb1      Link encap:Ethernet  HWaddr 32:2e:54:f0:c8:a3  
          inet addr:192.168.42.61  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::302e:54ff:fef0:c8a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17411 errors:3 dropped:0 overruns:0 frame:3
          TX packets:16251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22173713 (22.1 MB)  TX bytes:2420743 (2.4 MB)
```
Anyone out there who had this issue?

---

### Post by isoscelesrectangle on 2010-11-21
umm... bump.

---

