---
title: "horrible screen after nVidia driver updated"
date: 2010-06-16
forum: Hardware
---

### Post by fwoncn on 2010-06-16
Hi, my laptop with an Nvidia graphic card have Ubuntu 10.04 installed. 
    Here's my problem:
    Yesterday I performed an update on the nvidia-current (to version 195.36.24) and shut it down. When I power on my machine today everything is alright until the login screen. The monitor's space had been separated into four and each contained the whole content of the login screen, what's more, a huge wide white bar was across the middle of the monitor.:confused: And after I logged in, the problem remained. I tried to open Nvidia setting program but the words were too small to recognize. Then I removed the driver in System -> Administration -> Hardware Drivers and did reboot. Now I'm working in the low resolution and it makes me headache. And of course, all 3D effects are disabled.
    How can I let the new version work correctly or how can I downgrade to the previous version which worked for me?

Here are the results of some commands I can think of now 
```
$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                     173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-modaliases                     195.36.24-0ubuntu1~10.04                        Transitional package for nvidia-185-modalias
ii  nvidia-96-modaliases                      96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.23                                          Find obsolete NVIDIA drivers
rc  nvidia-current                            195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases                 195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-kernel-common                      20080825+1ubuntu2                               NVIDIA binary kernel module common files
```

```
$ xrandr 
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0
```

```
$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.PLfVFcK_w9E
  Hardware Class: framebuffer
  Model: "NVIDIA MCP79 Board - mcp75lo "
  Vendor: "NVIDIA Corporation"
  Device: "MCP79 Board - mcp75lo "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x034b: 1360x768 (+1360), 8 bits
  Mode 0x034c: 1360x768 (+2720), 16 bits
  Mode 0x034d: 1360x768 (+5440), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by fwoncn on 2010-06-16
Hi, now I'm trying to install from the installer downloaded from nvidia [official site]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/195.36.15/NVIDIA-Linux-x86_64-195.36.15-pkg2.run&lang=us&type=GeForce") (I purposely choose an earlier version) rather than update from the repository. I'll report back if it works.

---

### Post by dino99 on 2010-06-16
remove into synaptic: nvidia-kernel-common

sudo rm -f /etc/X11/xorg.conf
sudo update-initramfs -u

---

### Post by fwoncn on 2010-06-16
Thank you, but after switch back to old version driver everything is fine:guitar:
here are the steps I took:

[LIST=1]
[*]remove nvidia* in Synaptic
[*]download the driver from nvidia's site and make the file runnable, note that they provide both 32-bit(NVIDIA-Linux-x86-195.36.XX-pkg1.run) and 64-bit(NVIDIA-Linux-x86_64-195.36.XX-pkg2.run) for every version
[*]```
sudo /etc/init.d/gdm stop
```
[*]Alt+F1, then login as root
[*]```
rmmod nvidia; rm -r -f /lib/modules/2.6.XX-X-generic/kernel/drivers/video/nvidia*
```
[*]```
./NVIDIA-Linux-x86_64-195.36.15-pkg2.run
``` then operate according to the prompts that show up
[*]reboot
[/LIST]
the attachment is the picture I took of the horrible screen before I fix this problem. now it's normal.

The only question I have is: if the kernel is updated in the future, will something going wrong?

---

