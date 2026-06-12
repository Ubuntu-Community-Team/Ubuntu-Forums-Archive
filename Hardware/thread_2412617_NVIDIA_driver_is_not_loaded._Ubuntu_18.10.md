---
title: "NVIDIA driver is not loaded. Ubuntu 18.10"
date: 2019-02-15
forum: Hardware
---

### Post by theazgra on 2019-02-15
I have problems with Nvidia drivers, on ubuntu 18.10. 
My notebook is using both intel integrated and external GPU. (1060 max Q).

I have dual boot with windows and secure boot disabled. Some time ago I installed nvidia drivers and it worked normally. nvidia-smi was working.

This week I noticed that nvidia drivers weren't loaded, so I reinstalled them multiple times, with multiple different version: (390.87, 410.78, 415.13). I have tried installing from both command line and "Software & update" app.

```
Linux ****-dell 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

Right now I have driver version 390.87.
Things I have tried so far:
[LIST]
[*]Clean installation of multiple driver versions. Never from run file. 
[*]Blacklisting nouveau in *blacklist-nvidia-nouveau.conf*
[*]Setting WaylandEnable=false 
[/LIST]
```

lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 3e9b (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] (rev a1) (prog-if 00 [VGA controller])

nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

nvidia-settings 
ERROR: NVIDIA driver is not loaded
ERROR: Unable to load info from any available system


```

Bug report from nvidia
[ATTACH]282524[/ATTACH]

---

### Post by theazgra on 2019-02-15
So I have figured it out.

I have missed blacklist-nvidia.conf file in /etc/modprobe.d, someone mentioned that file can be also found in /lib/modprobe.d.

So I deleted that file, run 
```
sudo update-initramfs -u
```

and on next boot nvidia drivers were loaded.

---

