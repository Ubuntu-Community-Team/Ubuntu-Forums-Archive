---
title: "Enable Nvidia AGP Fast Writes &#1080; Side Band Addressing"
date: 2009-12-10
forum: Hardware
---

### Post by AndreiF on 2009-12-10
I need to write this article after reading [http://ubuntuforums.org/showthread.php?t=140989](http://ubuntuforums.org/showthread.php?t=140989)


It's not actual for hardy, jaunty and later ubuntu versions that use dkms for build kernel module. My OS is Ubuntu Jaunty 9.04

OK

First of all:
```
cat /proc/driver/nvidia/agp/*

Fast Writes:     Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000017:0x1f000114
Host Bridge:     PCI device 8086:2570
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f004217:0x00000114
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
```

So FW are supported, FW is Disabled.

Now you should stop your desktop manager and use tty console.

```
dkms status
nvidia, 96.43.10, 2.6.28-15-generic, i686: installed (original_module exists)
```

```
sudo dkms uninstall -m nvidia -u 96.43.10
```

```
sudo rm -r /var/lib/dkms/nvidia/kernel
```

```
sudo rm -r /var/lib/dkms/nvidia/96.43.10/2.6.*
```

```
sudo rm -r /var/lib/dkms/nvidia/96.43.10/build/
```

```
sudo nano /var/lib/dkms/nvidia/96.43.10/source/os-registry.c
```

find (use Ctrl+W) "agpfw" and "agpsba"

if SBA supported in your card replace ```
static int NVreg_EnableAGPSBA = 0;
``` with ```
static int NVreg_EnableAGPSBA = 1;
```

and ```
static int NVreg_EnableAGPFW = 0;
``` with ```
static int NVreg_EnableAGPFW = 1;
```

than

```
sudo dkms build -m nvidia -u 96.43.10
```

```
sudo dkms install -m nvidia -u 96.43.10
```

now

```
cat /proc/driver/nvidia/agp/*
Fast Writes:     Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000017:0x1f000114
Host Bridge:     PCI device 8086:2570
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f004217:0x00000114
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Disabled
```

---

