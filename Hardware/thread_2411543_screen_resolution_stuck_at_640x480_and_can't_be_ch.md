---
title: "screen resolution stuck at 640x480 and can't be changed"
date: 2019-01-31
forum: Hardware
---

### Post by momut1 on 2019-01-31
Hello everyone, 

I just updated from ubuntu 16.04 to 18.04 and was flabbergasted by my inability to change my screen resolution. I tried adding *nomodeset* , removing it, basically everything I could muster. Can anyone assist me?

```
inxi -G
``` RESULT:

```
Graphics:  Card: NVIDIA GP104GL
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 256 bits)
           version: 3.3 Mesa 18.0.5
```

```
inxi -F
```RESULT:

```
System:    Host: d01ri1701916 Kernel: 4.15.0-45-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: FUJITSU product: N/A serial: N/A
           Mobo: FUJITSU model: D3517-A1 v: S26361-D3517-A1 serial: N/A
           UEFI [Legacy]: FUJITSU // American Megatrends v: V5.0.0.12 R1.14.0 for D3517-A1x date: 10/11/2017
CPU:       Quad core Intel Xeon E3-1240 v6 (-MT-MCP-) 
           cache: 8192 KB
           clock speeds: max: 4100 MHz 1: 1600 MHz
           2: 1600 MHz 3: 1600 MHz 4: 1600 MHz 5: 1600 MHz
           6: 1600 MHz 7: 1600 MHz 8: 1600 MHz
Graphics:  Card: NVIDIA GP104GL
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 256 bits)
           version: 3.3 Mesa 18.0.5
Audio:     Card-1 NVIDIA GP104 High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel
           Sound: ALSA v: k4.15.0-45-generic
Network:   Card: Intel Ethernet Connection (2) I219-LM
           driver: e1000e
           IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full
           mac: 90:1b:0e:da:71:a3
Drives:    HDD Total Size: 1024.2GB (54.7% used)
           ID-1: /dev/nvme0n1 model: SAMSUNG_MZVLW1T0HMLH size: 1024.2GB
           Partition: ID-1: / size: 876G used: 461G (56%)
           fs: ext4 dev: /dev/nvme0n1p1
           ID-2: swap-1 size: 68.57GB used: 0.00GB (0%)
           fs: swap dev: /dev/nvme0n1p5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 287 Uptime: 8 min Memory: 1641.5/64279.7MB
           Client: Shell (bash) inxi: 2.3.56 
```

```
sudo nano /etc/default/grub
```RESULT:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debi$
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
GRUB_CMDLINE_LINUX=""

```

```
cat /proc/driver/nvidia/version
```RESULT:

```
NVRM version: NVIDIA UNIX x86_64 Kernel Module  390.87  Tue Aug 21 12:33:05 PDT 2018
GCC version:  gcc version 6.5.0 20181026 (Ubuntu 6.5.0-2ubuntu1~18.04) 


```

From display settings I can't select from any given screen resolution, nor do I have a scale bar. 

I don't know if this is unrelated, but when updating I decided to keep my open_ssh settings. This is because there are some docker containers running on the machine from other PCs. 

UPDATE:
From NVidia documentation it appears my hardware version (NVIDIA GP104GL[Quadro P400]) is something that the driver version (390.87) supports: [https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

Thank you!

P.S. I don't know if this is unrelated as well, but I also can't use my second monitor.

---

### Post by Autodave on 2019-01-31
Upgrading from one release to another often causes problems like this, unfortunately.   You may want to try going back one version of the driver and see if that works.  If it does, then you can certainly try the current one again.

---

### Post by CatKiller on 2019-01-31
> **momut1 said:**
> 
```
Graphics:  Card: NVIDIA GP104GL
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 256 bits)
           version: 3.3 Mesa 18.0.5
```



You aren't using the proprietary Nvidia driver, even if you think you are. Install that, and see if it helps.

---

### Post by momut1 on 2019-02-01
Ok, so it turned out it was the CUDA drivers for the GPU that were missing from the install package and that was messing with everything. Why I need to have CUDA drivers even when not using the GPU is beyond me, but fairplay, it's resolved. Thanks everybody!

---

