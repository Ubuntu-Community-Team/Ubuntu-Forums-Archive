---
title: "AMD Radeon 6700 XT"
date: 2021-04-12
forum: Hardware
---

### Post by oortael1860 on 2021-04-12
Hello Everybody,

first I want to thank all of you in this forum. Your input has helped me a lot in the past getting my needs in Ubuntu satisfied.

Recently I was lucky enough to get an AMD Radeon 6700 XT to upgrade my existing PC. I heard lots of good news about AMD's open source drivers and Ubuntu compatibility. The setup is a following:

Board:  MSI X370 SLI PLUS AMD X370 So.AM4 Dual Channel DDR4 ATX Retail 
CPU:    AMD Ryzen 7 1700 8x 3.00GHz So.AM4
RAM:    4x 8GB Samsung M378A1K43CB2-CRC DDR4-2400 DIMM CL17 Single
SSD:           500GB Samsung 960 Evo M.2 2280 NVMe PCIe 3.0 x4 32Gb/s 3D-NAND TLC Toggle 
GPU:    AMD Radeon 6700 XT (Stock)
Screen: Dell 2005FPW


Unfortunately I cannot get the latest Radeon&#8482; Software for Linux® 20.50 Highlights ([https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-50](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-50)) to work with OpenCL.

The tool "clinfo" shows me this:

```

$ clinfo 
Number of platforms                               0

```

Here some debug information (please, let me know if I should post more information), acording to the graphics troubleshooting guide ([https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure):](https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure):)


```

lspci -nnk | egrep -i '3d|aphics|display|nouveau|nvidia|radeon|trident|vesa|vga'; uname -a; Xorg -version; sudo apt-get update; sudo apt-get install mesa-utils hardinfo fbset nux-tools inxi; inxi -F; sudo fbset -i; apt-cache show xserver-xorg | grep Version; xrandr; fglrxinfo; nvidia-settings -g |head -n 30 ; sudo lshw -short; sudo lshw -C display; dpkg -l | egrep -i 'fgl|intel|mesa|mesa-utils|nvidia|nouveau|radeon|trident|video-ati'; cat /etc/lsb-release; dmesg | egrep -i  'abort|ailed|bug|error|fail|fgl|GLX|GPU|intel|missing|nouveau|NVIDIA|radeon|segment|trident|VESA|VGA|wfb|\(EE\)|\(WW\)'; cat /proc/cpuinfo | grep -I model; cat /var/log/Xorg.0.log | egrep -i 'abort|ailed|bug|display|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|radeon|segment|trident|VESA|VGA|wfb|\(EE\)|\(WW\)'; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; cat /etc/X11/xorg.conf; /usr/lib/nux/unity_support_test -p;  ubuntu-support-status || ubuntu-security-status ; sudo lsmod
28:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:73df] (rev c1)
Linux gamelinux 5.8.0-48-generic #54~20.04.1-Ubuntu SMP Sat Mar 20 13:40:25 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg              
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg        
Hit:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal InRelease  
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree      
Reading state information... Done
mesa-utils is already the newest version (8.4.0-1build1).
The following additional packages will be installed:
  hddtemp lm-sensors tree zlib1g-dev
Suggested packages:
  libcpanel-json-xs-perl | libjson-xs-perl libxml-dumper-perl fancontrol
  read-edid i2c-tools
The following NEW packages will be installed:
  fbset hardinfo hddtemp inxi lm-sensors nux-tools tree zlib1g-dev
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 963 kB of archives.
After this operation, 3.393 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/main amd64 fbset amd64 2.1-31 [118 kB]
Get:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal-updates/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu1.2 [155 kB]
Get:3 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 hardinfo amd64 0.5.1+git20180227-2 [319 kB]
Get:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 nux-tools amd64 4.0.8+18.10.20180623-0ubuntu1 [10,3 kB]
Get:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 tree amd64 1.8.0-1 [43,0 kB]
Get:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 hddtemp amd64 0.3-beta15-53 [47,7 kB]
Get:7 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 inxi all 3.0.38-1-0ubuntu1 [182 kB]
Get:8 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 lm-sensors amd64 1:3.6.0-2ubuntu1 [87,4 kB]
Fetched 963 kB in 0s (3.195 kB/s)    
Preconfiguring packages ...
Selecting previously unselected package fbset.
(Reading database ... 171469 files and directories currently installed.)
Preparing to unpack .../0-fbset_2.1-31_amd64.deb ...
Unpacking fbset (2.1-31) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../1-zlib1g-dev_1%3a1.2.11.dfsg-2ubuntu1.2_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.2) ...
Selecting previously unselected package hardinfo.
Preparing to unpack .../2-hardinfo_0.5.1+git20180227-2_amd64.deb ...
Unpacking hardinfo (0.5.1+git20180227-2) ...
Selecting previously unselected package nux-tools.
Preparing to unpack .../3-nux-tools_4.0.8+18.10.20180623-0ubuntu1_amd64.deb ...
Unpacking nux-tools (4.0.8+18.10.20180623-0ubuntu1) ...
Selecting previously unselected package tree.
Preparing to unpack .../4-tree_1.8.0-1_amd64.deb ...
Unpacking tree (1.8.0-1) ...
Selecting previously unselected package hddtemp.
Preparing to unpack .../5-hddtemp_0.3-beta15-53_amd64.deb ...
Unpacking hddtemp (0.3-beta15-53) ...
Selecting previously unselected package inxi.
Preparing to unpack .../6-inxi_3.0.38-1-0ubuntu1_all.deb ...
Unpacking inxi (3.0.38-1-0ubuntu1) ...
Selecting previously unselected package lm-sensors.
Preparing to unpack .../7-lm-sensors_1%3a3.6.0-2ubuntu1_amd64.deb ...
Unpacking lm-sensors (1:3.6.0-2ubuntu1) ...
Setting up fbset (2.1-31) ...
Setting up inxi (3.0.38-1-0ubuntu1) ...
Setting up nux-tools (4.0.8+18.10.20180623-0ubuntu1) ...
Setting up tree (1.8.0-1) ...
Setting up lm-sensors (1:3.6.0-2ubuntu1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594; /lib/systemd/system/lm-sensors.service.
Setting up zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.2) ...
Setting up hddtemp (0.3-beta15-53) ...
Setting up hardinfo (0.5.1+git20180227-2) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for systemd (245.4-4ubuntu3.6) ...
System:
  Host: gamelinux Kernel: 5.8.0-48-generic x86_64 bits: 64
  Desktop: Gnome 3.36.7 Distro: Ubuntu 20.04.2 LTS (Focal Fossa)
Machine:
  Type: Desktop System: Micro-Star product: MS-7A33 v: 2.0
  serial: <superuser/root required>
  Mobo: Micro-Star model: X370 SLI PLUS (MS-7A33) v: 2.0
  serial: <superuser/root required> UEFI: American Megatrends v: 3.H0
  date: 01/22/2019
Battery:
  ID-1: hidpp_battery_0 charge: N/A condition: N/A
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP
  L2 cache: 4096 KiB
  Speed: 2567 MHz min/max: N/A Core speeds (MHz): 1: 2567 2: 2573 3: 2561
  4: 2567 5: 2562 6: 2577 7: 2575 8: 2561 9: 2571 10: 2568 11: 2647 12: 2645
  13: 2570 14: 2576 15: 2572 16: 2583
Graphics:
  Device-1: AMD driver: amdgpu v: 5.9.10.20.50
  Display: x11 server: X.Org 1.20.9 driver: ati,fbdev
  unloaded: modesetting,radeon,vesa resolution: 1680x1050~60Hz
  OpenGL: renderer: AMD Radeon RX 6700 XT
  v: 4.6.14756 Core Profile Context 20.50
Audio:
  Device-1: AMD driver: snd_hda_intel
  Device-2: AMD Family 17h HD Audio driver: snd_hda_intel
  Device-3: GN Netcom Jabra EVOLVE LINK MS type: USB
  driver: jabra,snd-usb-audio,usbhid
  Sound Server: ALSA v: k5.8.0-48-generic
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
  driver: r8169
  IF: enp33s0 state: up speed: 1000 Mbps duplex: full mac: 4c:cc:6a:ff:6f:ac
Drives:
  Local Storage: total: 465.76 GiB used: 11.25 GiB (2.4%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 500GB
  size: 465.76 GiB
Partition:
  ID-1: / size: 228.58 GiB used: 11.22 GiB (4.9%) fs: ext4
  dev: /dev/nvme0n1p5
Sensors:
  System Temperatures: cpu: 32.8 C mobo: N/A gpu: amdgpu temp: 36 C
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 0
Info:
  Processes: 354 Uptime: 27m Memory: 31.37 GiB used: 2.03 GiB (6.5%)
  Shell: bash inxi: 3.0.38

mode "1680x1050"
    geometry 1680 1050 1680 1050 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : amdgpudrmfb
    Address     : 0
    Size        : 7299072
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 6912
    Accelerator : No
Version: 1:7.7+19ubuntu14
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050     59.88*+
   1280x1024     75.02    60.02  
   1440x900      59.88  
   1280x800      59.88  
   1152x864      75.00  
   1280x720      59.88  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
fglrxinfo: command not found

Command 'nvidia-settings' not found, but can be installed with:

sudo apt install nvidia-settings

H/W path              Device          Class          Description
================================================================
                                      system         MS-7A33 (To be filled by O.
/0                                    bus            X370 SLI PLUS (MS-7A33)
/0/0                                  memory         64KiB BIOS
/0/f                                  memory         32GiB System Memory
/0/f/0                                memory         8GiB DIMM DDR4 Synchronous
/0/f/1                                memory         8GiB DIMM DDR4 Synchronous
/0/f/2                                memory         8GiB DIMM DDR4 Synchronous
/0/f/3                                memory         8GiB DIMM DDR4 Synchronous
/0/11                                 memory         768KiB L1 cache
/0/12                                 memory         4MiB L2 cache
/0/13                                 memory         16MiB L3 cache
/0/14                                 processor      AMD Ryzen 7 1700 Eight-Core
/0/100                                bridge         Family 17h (Models 00h-0fh)
/0/100/0.2                            generic        Family 17h (Models 00h-0fh)
/0/100/1.1                            bridge         Family 17h (Models 00h-0fh)
/0/100/1.1/0                          storage        NVMe SSD Controller SM961/P
/0/100/1.1/0/0        /dev/nvme0      storage        Samsung SSD 960 EVO 500GB
/0/100/1.1/0/0/1      /dev/nvme0n1    disk           500GB NVMe namespace
/0/100/1.1/0/0/1/1    /dev/nvme0n1p1  volume         498MiB Windows NTFS volume
/0/100/1.1/0/0/1/2    /dev/nvme0n1p2  volume         99MiB Windows FAT volume
/0/100/1.1/0/0/1/3    /dev/nvme0n1p3  volume         15MiB reserved partition
/0/100/1.1/0/0/1/4    /dev/nvme0n1p4  volume         231GiB Windows NTFS volume
/0/100/1.1/0/0/1/5    /dev/nvme0n1p5  volume         233GiB EXT4 volume
/0/100/1.1/0/0/1/6    /dev/nvme0n1p6  volume         555MiB Windows NTFS volume
/0/100/1.3                            bridge         Family 17h (Models 00h-0fh)
/0/100/1.3/0                          bus            X370 Series Chipset USB 3.1
/0/100/1.3/0/0        usb1            bus            xHCI Host Controller
/0/100/1.3/0/0/2                      input          USB Receiver
/0/100/1.3/0/0/a                      multimedia     Jabra EVOLVE LINK MS
/0/100/1.3/0/1        usb2            bus            xHCI Host Controller
/0/100/1.3/0.1                        storage        X370 Series Chipset SATA Co
/0/100/1.3/0.2                        bridge         X370 Series Chipset PCIe Up
/0/100/1.3/0.2/0                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/1                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/1/0    enp33s0         network        RTL8111/8168/8411 PCI Expre
/0/100/1.3/0.2/2                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/3                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/4                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/8                      bridge         300 Series Chipset PCIe Por
/0/100/1.3/0.2/8/0                    bus            ASM2142 USB 3.1 Host Contro
/0/100/1.3/0.2/8/0/0  usb3            bus            xHCI Host Controller
/0/100/1.3/0.2/8/0/1  usb4            bus            xHCI Host Controller
/0/100/3.1                            bridge         Family 17h (Models 00h-0fh)
/0/100/3.1/0                          bridge         Navi 10 XL Upstream Port of
/0/100/3.1/0/0                        bridge         Navi 10 XL Downstream Port
/0/100/3.1/0/0/0                      display        Advanced Micro Devices, Inc
/0/100/3.1/0/0/0.1                    multimedia     Advanced Micro Devices, Inc
/0/100/7.1                            bridge         Family 17h (Models 00h-0fh)
/0/100/7.1/0                          generic        Zeppelin/Raven/Raven2 PCIe
/0/100/7.1/0.2                        generic        Family 17h (Models 00h-0fh)
/0/100/7.1/0.3                        bus            Family 17h (Models 00h-0fh)
/0/100/7.1/0.3/0      usb5            bus            xHCI Host Controller
/0/100/7.1/0.3/0/4                    input          Keyboard
/0/100/7.1/0.3/1      usb6            bus            xHCI Host Controller
/0/100/8.1                            bridge         Family 17h (Models 00h-0fh)
/0/100/8.1/0                          generic        Zeppelin/Renoir PCIe Dummy
/0/100/8.1/0.2                        storage        FCH SATA Controller [AHCI m
/0/100/8.1/0.3                        multimedia     Family 17h (Models 00h-0fh)
/0/100/14                             bus            FCH SMBus Controller
/0/100/14.3                           bridge         FCH LPC Bridge
/0/101                                bridge         Family 17h (Models 00h-1fh)
/0/102                                bridge         Family 17h (Models 00h-1fh)
/0/103                                bridge         Family 17h (Models 00h-1fh)
/0/104                                bridge         Family 17h (Models 00h-1fh)
/0/105                                bridge         Family 17h (Models 00h-1fh)
/0/106                                bridge         Family 17h (Models 00h-1fh)
/0/107                                bridge         Family 17h (Models 00h-0fh)
/0/108                                bridge         Family 17h (Models 00h-0fh)
/0/109                                bridge         Family 17h (Models 00h-0fh)
/0/10a                                bridge         Family 17h (Models 00h-0fh)
/0/10b                                bridge         Family 17h (Models 00h-0fh)
/0/10c                                bridge         Family 17h (Models 00h-0fh)
/0/10d                                bridge         Family 17h (Models 00h-0fh)
/0/10e                                bridge         Family 17h (Models 00h-0fh)
/0/1                                  system         PnP device PNP0c01
/0/2                                  system         PnP device PNP0b00
/0/3                                  system         PnP device PNP0c02
/0/4                                  printer        PnP device PNP0400
/0/5                                  communication  PnP device PNP0501
/0/6                                  system         PnP device PNP0c02
  *-display                
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:28:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:62 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fc900000-fc9fffff memory:fca00000-fca1ffff
ii  gir1.2-ibus-1.0:amd64                      1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - introspection data
ii  i965-va-driver:amd64                       2.4.0-0ubuntu1                        amd64        VAAPI driver for Intel G45 & HD Graphics family
ii  ibus                                       1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - core
ii  ibus-data                                  1.5.22-2ubuntu2.1                     all          Intelligent Input Bus - data files
ii  ibus-gtk:amd64                             1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - GTK2 support
ii  ibus-gtk3:amd64                            1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - GTK3 support
ii  intel-media-va-driver:amd64                20.1.1+dfsg1-1                        amd64        VAAPI driver for the Intel GEN8+ Graphics family
ii  intel-microcode                            3.20201110.0ubuntu0.20.04.2           amd64        Processor microcode firmware for Intel CPUs
ii  iucode-tool                                2.3.1-1                               amd64        Intel processor microcode tool
ii  libdrm-amdgpu-radeon1:amd64                1:2.4.100-1234664                     amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-amdgpu-radeon1:i386                 1:2.4.100-1234664                     i386         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-intel1:amd64                        2.4.102-1ubuntu1~20.04.1              amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                      2.4.102-1ubuntu1~20.04.1              amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                       2.4.102-1ubuntu1~20.04.1              i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                       2.4.102-1ubuntu1~20.04.1              amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                        2.4.102-1ubuntu1~20.04.1              i386         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libegl-mesa0:amd64                         20.2.6-0ubuntu0.20.04.1               amd64        free implementation of the EGL API -- Mesa vendor library
ii  libegl1-amdgpu-mesa:amd64                  1:20.2.4-1234664                      amd64        free implementation of the EGL API -- runtime
ii  libegl1-amdgpu-mesa:i386                   1:20.2.4-1234664                      i386         free implementation of the EGL API -- runtime
ii  libegl1-amdgpu-mesa-drivers:amd64          1:20.2.4-1234664                      amd64        free implementation of the EGL API -- hardware drivers
ii  libegl1-amdgpu-mesa-drivers:i386           1:20.2.4-1234664                      i386         free implementation of the EGL API -- hardware drivers
ii  libgl1-amdgpu-mesa-dri:amd64               1:20.2.4-1234664                      amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-amdgpu-mesa-dri:i386                1:20.2.4-1234664                      i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-amdgpu-mesa-glx:amd64               1:20.2.4-1234664                      amd64        free implementation of the OpenGL API -- GLX runtime
ii  libgl1-amdgpu-mesa-glx:i386                1:20.2.4-1234664                      i386         free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-dri:amd64                      20.2.6-0ubuntu0.20.04.1               amd64        free implementation of the OpenGL API -- DRI modules
ii  libglapi-amdgpu-mesa:amd64                 1:20.2.4-1234664                      amd64        free implementation of the GL API -- shared library
ii  libglapi-amdgpu-mesa:i386                  1:20.2.4-1234664                      i386         free implementation of the GL API -- shared library
ii  libglapi-mesa:amd64                        20.2.6-0ubuntu0.20.04.1               amd64        free implementation of the GL API -- shared library
ii  libgles1-amdgpu-mesa:amd64                 1:20.2.4-1234664                      amd64        free implementation of the OpenGL|ES 1.x API -- runtime
ii  libgles1-amdgpu-mesa:i386                  1:20.2.4-1234664                      i386         free implementation of the OpenGL|ES 1.x API -- runtime
ii  libgles2-amdgpu-mesa:amd64                 1:20.2.4-1234664                      amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libgles2-amdgpu-mesa:i386                  1:20.2.4-1234664                      i386         free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                         9.0.1-1build1                         amd64        Mesa OpenGL utility library (GLU)
ii  libglx-mesa0:amd64                         20.2.6-0ubuntu0.20.04.1               amd64        free implementation of the OpenGL API -- GLX vendor library
ii  libibus-1.0-5:amd64                        1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - shared library
ii  libigdgmm11:amd64                          20.1.1+ds1-1                          amd64        Intel Graphics Memory Management Library -- shared library
ii  libosmesa6-amdgpu:amd64                    1:20.2.4-1234664                      amd64        Mesa Off-screen rendering extension
ii  libosmesa6-amdgpu:i386                     1:20.2.4-1234664                      i386         Mesa Off-screen rendering extension
ii  mesa-amdgpu-omx-drivers:amd64              1:20.2.4-1234664                      amd64        Mesa OpenMAX video drivers
ii  mesa-amdgpu-va-drivers:amd64               1:20.2.4-1234664                      amd64        Mesa VA-API video acceleration drivers
ii  mesa-amdgpu-va-drivers:i386                1:20.2.4-1234664                      i386         Mesa VA-API video acceleration drivers
ii  mesa-amdgpu-vdpau-drivers:amd64            1:20.2.4-1234664                      amd64        Mesa VDPAU video acceleration drivers
ii  mesa-amdgpu-vdpau-drivers:i386             1:20.2.4-1234664                      i386         Mesa VDPAU video acceleration drivers
ii  mesa-utils                                 8.4.0-1build1                         amd64        Miscellaneous Mesa GL utilities
ii  mesa-va-drivers:amd64                      20.2.6-0ubuntu0.20.04.1               amd64        Mesa VA-API video acceleration drivers
ii  mesa-vdpau-drivers:amd64                   20.2.6-0ubuntu0.20.04.1               amd64        Mesa VDPAU video acceleration drivers
ii  mesa-vdpau-drivers:i386                    20.2.6-0ubuntu0.20.04.1               i386         Mesa VDPAU video acceleration drivers
ii  mesa-vulkan-drivers:amd64                  20.2.6-0ubuntu0.20.04.1               amd64        Mesa Vulkan graphics drivers
ii  python3-ibus-1.0                           1.5.22-2ubuntu2.1                     all          Intelligent Input Bus - introspection overrides for Python (Python 3)
ii  xserver-xorg-amdgpu-video-amdgpu           1:19.1.0-1234664                      amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-ati                     1:19.1.0-1                            amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-intel                   2:2.99.917+git20200226-1              amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                 1:1.0.16-1                            amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon                  1:19.1.0-1                            amd64        X.Org X server -- AMD/ATI Radeon display driver
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.2 LTS"
[    0.000000]   Intel GenuineIntel
[    0.005500] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20200528/tbfadt-615)
[    0.417757] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.422133] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.433573] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
[    0.443784] pci 0000:28:00.0: vgaarb: VGA device added: decodes=io+mem,owns=none,locks=none
[    0.443784] pci 0000:28:00.0: vgaarb: bridge control possible
[    0.443784] pci 0000:28:00.0: vgaarb: setting as boot device
[    0.443784] vgaarb: loaded
[    0.635835] fb0: EFI VGA frame buffer device
[    0.689316] Segment Routing with IPv6
[    0.699818] RAS: Correctable Errors collector initialized.
[    0.839615] amdkcl: module verification failed: signature and/or required key missing - tainting kernel
[    1.045376] [drm] amdgpu kernel modesetting enabled.
[    1.045377] [drm] amdgpu version: 5.9.10.20.50
[    1.045486] amdgpu: Ignoring ACPI CRAT on non-APU system
[    1.045490] amdgpu: Virtual CRAT table created for CPU
[    1.045510] amdgpu: Topology: Add CPU node
[    1.047521] fb0: switching to amdgpudrmfb from EFI VGA
[    1.047574] amdgpu 0000:28:00.0: vgaarb: deactivate vga console
[    1.047613] amdgpu 0000:28:00.0: enabling device (0006 -> 0007)
[    1.047699] amdgpu 0000:28:00.0: amdgpu: Trusted Memory Zone (TMZ) feature not supported
[    1.049141] amdgpu 0000:28:00.0: amdgpu: Fetched VBIOS from VFCT
[    1.049143] amdgpu: ATOM BIOS: 113-D5121100-101
[    1.049181] amdgpu 0000:28:00.0: amdgpu: VRAM: 12272M 0x0000008000000000 - 0x00000082FEFFFFFF (12272M used)
[    1.049182] amdgpu 0000:28:00.0: amdgpu: GART: 512M 0x0000000000000000 - 0x000000001FFFFFFF
[    1.049183] amdgpu 0000:28:00.0: amdgpu: AGP: 267894784M 0x0000008400000000 - 0x0000FFFFFFFFFFFF
[    1.049277] [drm] amdgpu: 12272M of VRAM memory ready
[    1.049279] [drm] amdgpu: 32126M of GTT memory ready.
[    1.049285] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.711435] amdgpu 0000:28:00.0: amdgpu: RAS: optional ras ta ucode is not available
[    4.735829] amdgpu 0000:28:00.0: amdgpu: RAP: optional rap ta ucode is not available
[    4.735860] amdgpu 0000:28:00.0: amdgpu: use vbios provided pptable
[    4.791302] amdgpu 0000:28:00.0: amdgpu: SMU is initialized successfully!
[    5.091356] kfd kfd: amdgpu: Allocated 3969056 bytes on gart
[    5.092005] amdgpu: Virtual CRAT table created for GPU
[    5.092126] amdgpu: Topology: Add dGPU node [0x73df:0x1002]
[    5.092128] kfd kfd: amdgpu: added device 1002:73df
[    5.092131] amdgpu 0000:28:00.0: amdgpu: SE 2, SH per SE 2, CU per SH 10, active_cu_number 40
[    5.093097] fbcon: amdgpudrmfb (fb0) is primary device
[    5.093099] amdgpu 0000:28:00.0: fb0: amdgpudrmfb frame buffer device
[    5.115906] amdgpu 0000:28:00.0: amdgpu: ring gfx_0.0.0 uses VM inv eng 0 on hub 0
[    5.115908] amdgpu 0000:28:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[    5.115909] amdgpu 0000:28:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[    5.115910] amdgpu 0000:28:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[    5.115912] amdgpu 0000:28:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[    5.115913] amdgpu 0000:28:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[    5.115914] amdgpu 0000:28:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[    5.115915] amdgpu 0000:28:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[    5.115916] amdgpu 0000:28:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[    5.115917] amdgpu 0000:28:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[    5.115918] amdgpu 0000:28:00.0: amdgpu: ring sdma0 uses VM inv eng 12 on hub 0
[    5.115920] amdgpu 0000:28:00.0: amdgpu: ring sdma1 uses VM inv eng 13 on hub 0
[    5.115921] amdgpu 0000:28:00.0: amdgpu: ring vcn_dec_0 uses VM inv eng 0 on hub 1
[    5.115922] amdgpu 0000:28:00.0: amdgpu: ring vcn_enc_0.0 uses VM inv eng 1 on hub 1
[    5.115923] amdgpu 0000:28:00.0: amdgpu: ring vcn_enc_0.1 uses VM inv eng 4 on hub 1
[    5.115924] amdgpu 0000:28:00.0: amdgpu: ring jpeg_dec uses VM inv eng 5 on hub 1
[    5.116148] amdgpu 0000:28:00.0: amdgpu: [mmhub] page fault (src_id:0 ring:158 vmid:0 pasid:0, for process  pid 0 thread  pid 0)
[    5.116151] amdgpu 0000:28:00.0: amdgpu:   in page starting at address 0x000007000000 from client 18
[    5.116153] amdgpu 0000:28:00.0: amdgpu: MMVM_L2_PROTECTION_FAULT_STATUS:0x0000073C
[    5.116155] amdgpu 0000:28:00.0: amdgpu:      Faulty UTCL2 client ID: DCEDMC (0x3)
[    5.116156] amdgpu 0000:28:00.0: amdgpu:      MORE_FAULTS: 0x0
[    5.116157] amdgpu 0000:28:00.0: amdgpu:      WALKER_ERROR: 0x6
[    5.116158] amdgpu 0000:28:00.0: amdgpu:      PERMISSION_FAULTS: 0x3
[    5.116159] amdgpu 0000:28:00.0: amdgpu:      MAPPING_ERROR: 0x1
[    5.116160] amdgpu 0000:28:00.0: amdgpu:      RW: 0x0
[    5.116781] [drm] Initialized amdgpu 3.40.0 20150101 for 0000:28:00.0 on minor 0
[    5.759797] ata5: failed to resume link (SControl 0)
[    6.799786] ata6: failed to resume link (SControl 0)
[    7.760860] systemd[1]: Mounting Kernel Debug File System...
[    7.770174] systemd[1]: Mounted Kernel Debug File System.
[    7.776411] EXT4-fs (nvme0n1p5): re-mounted. Opts: errors=remount-ro
[    8.028094] snd_hda_intel 0000:28:00.1: enabling device (0000 -> 0002)
[    8.028191] snd_hda_intel 0000:28:00.1: Force to non-snoop mode
[    8.028390] snd_hda_intel 0000:2a:00.3: enabling device (0000 -> 0002)
[    8.037323] snd_hda_intel 0000:28:00.1: bound 0000:28:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
[    8.472088] audit: type=1400 audit(1618242753.305:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=740 comm="apparmor_parser"
[    8.472091] audit: type=1400 audit(1618242753.305:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=740 comm="apparmor_parser"
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.485] (==) Automatically adding GPU devices
[    22.485] (==) Automatically binding GPU devices
[    22.486] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.486] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.486] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.486] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.486] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.491] (II) LoadModule: "glx"
[    22.491] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.493] (II) Module glx: vendor="X.Org Foundation"
[    22.493] (==) Matched vesa as autoconfigured driver 3
[    22.552] (II) LoadModule: "radeon"
[    22.552] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.554] (II) Module radeon: vendor="X.Org Foundation"
[    22.555] (II) LoadModule: "vesa"
[    22.555] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.555] (II) Module vesa: vendor="X.Org Foundation"
[    22.555] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
[    22.558] (II) VESA: driver for VESA chipsets: vesa
[    22.558] (EE) open /dev/dri/card0: No such file or directory
[    22.558] (WW) Falling back to old probe method for modesetting
[    22.558] (EE) open /dev/dri/card0: No such file or directory
[    22.558] (EE) Screen 0 deleted because of no matching config section.
[    22.558] (II) FBDEV(0): Creating default Display subsection in Screen section
[    22.558] (II) FBDEV(0): hardware: EFI VGA (video memory: 7088kB)
[    22.559] (II) UnloadModule: "radeon"
[    22.559] (II) Unloading radeon
[    22.559] (II) UnloadModule: "vesa"
[    22.559] (II) Unloading vesa
[    22.564] (II) Initializing extension GLX
[    22.564] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.650] (II) IGLX: Loaded and initialized swrast
[    22.650] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   238.928] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[   238.928] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[   238.928] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
    Release Date: 01/22/2019
        Serial services are supported (int 14h)
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: MS-7A33
    Serial Number: To be filled by O.E.M.
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: X370 SLI PLUS (MS-7A33)
    Serial Number: H416261447
    Manufacturer: Micro-Star International Co., Ltd.
    Serial Number: To be filled by O.E.M.
    Manufacturer: Advanced Micro Devices, Inc.
    Serial Number: Unknown
    Manufacturer: Samsung
    Serial Number: 1916F29F
    Manufacturer: Samsung
    Serial Number: 1917077A
    Manufacturer: Samsung
    Serial Number: 1916F357
    Manufacturer: Samsung
    Serial Number: 1916F7AC
cat: /etc/X11/xorg.conf: No such file or directory
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon RX 6700 XT
OpenGL version string:  4.6.14756 Compatibility Profile Context 20.50

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
ubuntu-support-status: command not found
1682 packages installed, of which:
1537 receive package updates with LTS until 4/2025
  85 could receive security updates with ESM Apps until 4/2030
  60 packages are from third parties

Packages from third parties are not provided by the official Ubuntu
archive, for example packages from Personal Package Archives in
Launchpad.
For more information on the packages, run 'ubuntu-security-status
--thirdparty'.

Enable Extended Security Maintenance (ESM Apps) to get 1 security
update (so far) and enable coverage of 85 packages.

This machine is not attached to an Ubuntu Advantage subscription.
See [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
Module                  Size  Used by
rpcsec_gss_krb5        40960  0
auth_rpcgss           114688  1 rpcsec_gss_krb5
nfsv4                 729088  2
nfs                   339968  2 nfsv4
lockd                 102400  1 nfs
grace                  16384  1 lockd
sunrpc                487424  8 nfsv4,auth_rpcgss,lockd,rpcsec_gss_krb5,nfs
fscache               376832  2 nfsv4,nfs
nls_iso8859_1          16384  1
edac_mce_amd           32768  0
kvm_amd                98304  0
kvm                   712704  1 kvm_amd
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
aesni_intel           372736  0
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_usb_audio         282624  2
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_usbmidi_lib        36864  1 snd_usb_audio
mc                     57344  1 snd_usb_audio
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               114688  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
rapl                   20480  0
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
joydev                 24576  0
snd_timer              40960  2 snd_seq,snd_pcm
wmi_bmof               16384  0
input_leds             16384  0
efi_pstore             16384  0
mxm_wmi                16384  0
snd                    94208  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
ccp                    98304  1 kvm_amd
k10temp                16384  0
soundcore              16384  1 snd
sch_fq_codel           20480  2
mac_hid                16384  0
parport_pc             45056  1
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               49152  1 ip_tables
autofs4                45056  2
hid_logitech_hidpp     45056  0
hid_logitech_dj        28672  0
hid_jabra              16384  0
hid_generic            16384  0
usbhid                 57344  1 hid_logitech_dj
hid                   135168  5 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp,hid_jabra
amdgpu               6004736  66
iommu_v2               20480  1 amdgpu
amd_sched              36864  1 amdgpu
amdttm                106496  1 amdgpu
amdkcl                 24576  3 amd_sched,amdttm,amdgpu
drm_kms_helper        217088  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
cec                    53248  1 drm_kms_helper
rc_core                57344  1 cec
crc32_pclmul           16384  0
drm                   552960  11 drm_kms_helper,amd_sched,amdttm,amdgpu,amdkcl
i2c_piix4              28672  0
i2c_algo_bit           16384  1 amdgpu
nvme                   45056  2
r8169                  77824  0
ahci                   40960  0
xhci_pci               20480  0
realtek                24576  1
nvme_core             110592  4 nvme
xhci_pci_renesas       20480  1 xhci_pci
libahci                36864  1 ahci
wmi                    32768  2 wmi_bmof,mxm_wmi
gpio_amdpt             20480  0
gpio_generic           20480  1 gpio_amdpt


```

Cheers
Stefan

---

### Post by mastablasta on 2021-04-13
> [COLOR=#000000][FONT=&quot]Linux gamelinux 5.8.0-48-generic
[/FONT][/COLOR]

you need kernel 5.11 or higher, because drivers are in kernel. newer kernel newer drivers. having 5.12 version would be beneficial in this case according to phoronix tests, but 5.11 will do fine as well. Phoronix test on [COLOR=#000000]Radeon 6700 XT[/COLOR]: [https://www.phoronix.com/scan.php?page=article&item=radeon-rx6700xt-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=radeon-rx6700xt-linux&num=1)

options
1. load Ubuntu 21.04 beta. the 21.04 is scheduled to come out in April this year anyway and it will have 5.11 kernel: [https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-release-features](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-release-features)

2. upgrade Ubuntu kernel:
how to:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
[https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)

3.
other option is to use a distro which already has newer kernel. maybe Manjaro?

---

### Post by oortael1860 on 2021-04-15
Hi [**[COLOR=#DD4814][B]mastablasta**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=964486")[B][COLOR=#DD4814][B],
[/B][/COLOR][/B]
thank you for your suggestions. As I will anyway upgrade in April to the latest version of Ubuntu I go with Option 1. I upgraded the 20.04 installation to 21.04 beta by using "do-release-upgrade".

Anyhow, I'm still stuck. The driver itself seems to be hard-coded to Ubuntu 20.04. Therefore I changed the OS in "/etc/os-release" to this:

```

NAME="Ubuntu" 
VERSION="20.04 (Hirsute Hippo)" 
ID=ubuntu 
ID_LIKE=debian 
PRETTY_NAME="Ubuntu Hirsute Hippo (development branch)" 
VERSION_ID="20.04" 
HOME_URL="https://www.ubuntu.com/" 
SUPPORT_URL="https://help.ubuntu.com/" 
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" 
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" 
VERSION_CODENAME=hirsute 
UBUNTU_CODENAME=hirsute

```

Then the driver at least lets me use the shipped script to install the pro variant driver with this command:

```

./amdgpu-pro-install -y --opencl=rocr,legacy

```

Unfortunately the package "amdgpu-dkms" will not compile the needed modules:

```

$ ./amdgpu-pro-install -y --opencl=rocr,legacy 
deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./ 
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease 
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease 
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B] 
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B] 
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg                             
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg                             
Get:4 file:/var/opt/amdgpu-pro-local ./ Packages [114 kB]                       
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hirsute InRelease                     
Hit:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hirsute-updates InRelease             
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security InRelease 
Hit:8 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hirsute-backports InRelease 
Reading package lists... Done 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Selected version '20.50-1234664' (localhost [all]) for 'amdgpu-pro-pin' 
The following packages were automatically installed and are no longer required: 
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 
  libelf1:i386 libexpat1:i386 libffi8ubuntu1:i386 libllvm11:i386 libmd0:i386 
  libomxil-bellagio-bin libomxil-bellagio0 libstdc++6:i386 libva2:i386 
  libvdpau1:i386 libwayland-client0:i386 libwayland-egl1:i386 
  libwayland-server0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 
  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdamage1:i386 
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386 
  libxxf86vm1:i386 mesa-vdpau-drivers:i386 vdpau-driver-all:i386 
Use 'sudo apt autoremove' to remove them. 
The following NEW packages will be installed: 
  amdgpu-pro-pin 
0 upgraded, 1 newly installed, 0 to remove and 37 not upgraded. 
Need to get 0 B/6.276 B of archives. 
After this operation, 38,9 kB of additional disk space will be used. 
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-pin 20.50-1234664 [6.276 B] 
Selecting previously unselected package amdgpu-pro-pin. 
(Reading database ... 145428 files and directories currently installed.) 
Preparing to unpack .../amdgpu-pro-pin_20.50-1234664_all.deb ... 
Unpacking amdgpu-pro-pin (20.50-1234664) ... 
Setting up amdgpu-pro-pin (20.50-1234664) ... 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 
  libelf1:i386 libexpat1:i386 libffi8ubuntu1:i386 libllvm11:i386 libmd0:i386 
  libomxil-bellagio-bin libomxil-bellagio0 libstdc++6:i386 libva2:i386 
  libvdpau1:i386 libwayland-client0:i386 libwayland-egl1:i386 
  libwayland-server0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 
  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdamage1:i386 
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386 
  libxxf86vm1:i386 mesa-vdpau-drivers:i386 vdpau-driver-all:i386 
Use 'sudo apt autoremove' to remove them. 
The following NEW packages will be installed: 
  amdgpu-pin 
0 upgraded, 1 newly installed, 0 to remove and 37 not upgraded. 
Need to get 0 B/2.736 B of archives. 
After this operation, 26,6 kB of additional disk space will be used. 
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-pin 20.50-1234664 [2.736 B] 
Selecting previously unselected package amdgpu-pin. 
(Reading database ... 145447 files and directories currently installed.) 
Preparing to unpack .../amdgpu-pin_20.50-1234664_all.deb ... 
Unpacking amdgpu-pin (20.50-1234664) ... 
Setting up amdgpu-pin (20.50-1234664) ... 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following additional packages will be installed: 
  amdgpu-core amdgpu-dkms-firmware amdgpu-lib amdgpu-pro-core comgr-amdgpu-pro 
  gst-omx-amdgpu hip-rocr-amdgpu-pro hsa-runtime-rocr-amdgpu 
  hsakmt-roct-amdgpu libdrm-amdgpu-amdgpu1 libdrm-amdgpu-amdgpu1:i386 
  libdrm-amdgpu-common libdrm-amdgpu-radeon1 libdrm-amdgpu-radeon1:i386 
  libdrm2-amdgpu libdrm2-amdgpu:i386 libegl1-amdgpu-mesa 
  libegl1-amdgpu-mesa:i386 libegl1-amdgpu-mesa-drivers 
  libegl1-amdgpu-mesa-drivers:i386 libegl1-amdgpu-pro libegl1-amdgpu-pro:i386 
  libgbm1-amdgpu libgbm1-amdgpu:i386 libgl1-amdgpu-mesa-dri 
  libgl1-amdgpu-mesa-dri:i386 libgl1-amdgpu-mesa-glx 
  libgl1-amdgpu-mesa-glx:i386 libgl1-amdgpu-pro-appprofiles 
  libgl1-amdgpu-pro-dri libgl1-amdgpu-pro-dri:i386 libgl1-amdgpu-pro-ext 
  libgl1-amdgpu-pro-glx libgl1-amdgpu-pro-glx:i386 libglapi-amdgpu-mesa 
  libglapi-amdgpu-mesa:i386 libglapi1-amdgpu-pro libglapi1-amdgpu-pro:i386 
  libgles1-amdgpu-mesa libgles1-amdgpu-mesa:i386 libgles2-amdgpu-mesa 
  libgles2-amdgpu-mesa:i386 libgles2-amdgpu-pro libgles2-amdgpu-pro:i386 
  libllvm11.0-amdgpu libllvm11.0-amdgpu:i386 libosmesa6-amdgpu 
  libosmesa6-amdgpu:i386 libxatracker2-amdgpu libxatracker2-amdgpu:i386 
  mesa-amdgpu-omx-drivers mesa-amdgpu-va-drivers mesa-amdgpu-va-drivers:i386 
  mesa-amdgpu-vdpau-drivers mesa-amdgpu-vdpau-drivers:i386 
  ocl-icd-libopencl1-amdgpu-pro opencl-rocr-amdgpu-pro 
  xserver-xorg-amdgpu-video-amdgpu 
Suggested packages: 
  libglide3 libglide3:i386 
Recommended packages: 
  libtxc-dxtn-s2tc0 | libtxc-dxtn0 libtxc-dxtn-s2tc0:i386 | libtxc-dxtn0:i386 
The following NEW packages will be installed: 
  amdgpu amdgpu-core amdgpu-dkms amdgpu-dkms-firmware amdgpu-lib amdgpu-lib32 
  amdgpu-pro amdgpu-pro-core amdgpu-pro-lib32 amdgpu-pro-rocr-opencl 
  clinfo-amdgpu-pro comgr-amdgpu-pro gst-omx-amdgpu hip-rocr-amdgpu-pro 
  hsa-runtime-rocr-amdgpu hsakmt-roct-amdgpu libdrm-amdgpu-amdgpu1 
  libdrm-amdgpu-amdgpu1:i386 libdrm-amdgpu-common libdrm-amdgpu-radeon1 
  libdrm-amdgpu-radeon1:i386 libdrm2-amdgpu libdrm2-amdgpu:i386 
  libegl1-amdgpu-mesa libegl1-amdgpu-mesa:i386 libegl1-amdgpu-mesa-drivers 
  libegl1-amdgpu-mesa-drivers:i386 libegl1-amdgpu-pro libegl1-amdgpu-pro:i386 
  libgbm1-amdgpu libgbm1-amdgpu:i386 libgl1-amdgpu-mesa-dri 
  libgl1-amdgpu-mesa-dri:i386 libgl1-amdgpu-mesa-glx 
  libgl1-amdgpu-mesa-glx:i386 libgl1-amdgpu-pro-appprofiles 
  libgl1-amdgpu-pro-dri libgl1-amdgpu-pro-dri:i386 libgl1-amdgpu-pro-ext 
  libgl1-amdgpu-pro-glx libgl1-amdgpu-pro-glx:i386 libglapi-amdgpu-mesa 
  libglapi-amdgpu-mesa:i386 libglapi1-amdgpu-pro libglapi1-amdgpu-pro:i386 
  libgles1-amdgpu-mesa libgles1-amdgpu-mesa:i386 libgles2-amdgpu-mesa 
  libgles2-amdgpu-mesa:i386 libgles2-amdgpu-pro libgles2-amdgpu-pro:i386 
  libllvm11.0-amdgpu libllvm11.0-amdgpu:i386 libosmesa6-amdgpu 
  libosmesa6-amdgpu:i386 libxatracker2-amdgpu libxatracker2-amdgpu:i386 
  mesa-amdgpu-omx-drivers mesa-amdgpu-va-drivers mesa-amdgpu-va-drivers:i386 
  mesa-amdgpu-vdpau-drivers mesa-amdgpu-vdpau-drivers:i386 
  ocl-icd-libopencl1-amdgpu-pro opencl-orca-amdgpu-pro-icd 
  opencl-rocr-amdgpu-pro vulkan-amdgpu-pro xserver-xorg-amdgpu-video-amdgpu 
0 upgraded, 67 newly installed, 0 to remove and 37 not upgraded. 
Need to get 0 B/177 MB of archives. 
After this operation, 1.254 MB of additional disk space will be used. 
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-dkms-firmware 1:5.9.10.69-1234664 [6.195 kB] 
Get:2 file:/var/opt/amdgpu-pro-local ./ amdgpu-dkms 1:5.9.10.69-1234664 [6.404 kB] 
Get:3 file:/var/opt/amdgpu-pro-local ./ amdgpu-core 20.50-1234664 [2.208 B] 
Get:4 file:/var/opt/amdgpu-pro-local ./ libdrm2-amdgpu 1:2.4.100-1234664 [38,0 kB] 
Get:5 file:/var/opt/amdgpu-pro-local ./ libdrm-amdgpu-common 1.0.0-1234664 [4.764 B] 
Get:6 file:/var/opt/amdgpu-pro-local ./ libdrm-amdgpu-amdgpu1 1:2.4.100-1234664 [23,8 kB] 
Get:7 file:/var/opt/amdgpu-pro-local ./ libdrm-amdgpu-radeon1 1:2.4.100-1234664 [23,8 kB] 
Get:8 file:/var/opt/amdgpu-pro-local ./ libllvm11.0-amdgpu 1:11.0-1234664 [18,5 MB] 
Get:9 file:/var/opt/amdgpu-pro-local ./ mesa-amdgpu-va-drivers 1:20.2.4-1234664 [2.240 kB] 
Get:10 file:/var/opt/amdgpu-pro-local ./ libglapi-amdgpu-mesa 1:20.2.4-1234664 [24,8 kB] 
Get:11 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-mesa-dri 1:20.2.4-1234664 [7.187 kB] 
Get:12 file:/var/opt/amdgpu-pro-local ./ libdrm2-amdgpu 1:2.4.100-1234664 [35,5 kB] 
Get:13 file:/var/opt/amdgpu-pro-local ./ libdrm-amdgpu-amdgpu1 1:2.4.100-1234664 [21,0 kB] 
Get:14 file:/var/opt/amdgpu-pro-local ./ libdrm-amdgpu-radeon1 1:2.4.100-1234664 [22,3 kB] 
Get:15 file:/var/opt/amdgpu-pro-local ./ libllvm11.0-amdgpu 1:11.0-1234664 [16,5 MB] 
Get:16 file:/var/opt/amdgpu-pro-local ./ mesa-amdgpu-va-drivers 1:20.2.4-1234664 [2.347 kB] 
Get:17 file:/var/opt/amdgpu-pro-local ./ libglapi-amdgpu-mesa 1:20.2.4-1234664 [24,6 kB] 
Get:18 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-mesa-dri 1:20.2.4-1234664 [7.503 kB] 
Get:19 file:/var/opt/amdgpu-pro-local ./ libxatracker2-amdgpu 1:20.2.4-1234664 [1.183 kB] 
Get:20 file:/var/opt/amdgpu-pro-local ./ libgbm1-amdgpu 1:20.2.4-1234664 [29,4 kB] 
Get:21 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-mesa 1:20.2.4-1234664 [106 kB] 
Get:22 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-mesa-drivers 1:20.2.4-1234664 [4.344 B] 
Get:23 file:/var/opt/amdgpu-pro-local ./ libgles1-amdgpu-mesa 1:20.2.4-1234664 [8.348 B] 
Get:24 file:/var/opt/amdgpu-pro-local ./ libgles2-amdgpu-mesa 1:20.2.4-1234664 [12,0 kB] 
Get:25 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-mesa-glx 1:20.2.4-1234664 [145 kB] 
Get:26 file:/var/opt/amdgpu-pro-local ./ libosmesa6-amdgpu 1:20.2.4-1234664 [3.688 kB] 
Get:27 file:/var/opt/amdgpu-pro-local ./ mesa-amdgpu-vdpau-drivers 1:20.2.4-1234664 [2.762 kB] 
Get:28 file:/var/opt/amdgpu-pro-local ./ mesa-amdgpu-omx-drivers 1:20.2.4-1234664 [2.359 kB] 
Get:29 file:/var/opt/amdgpu-pro-local ./ xserver-xorg-amdgpu-video-amdgpu 1:19.1.0-1234664 [57,9 kB] 
Get:30 file:/var/opt/amdgpu-pro-local ./ gst-omx-amdgpu 1.0.0.1-1234664 [58,6 kB] 
Get:31 file:/var/opt/amdgpu-pro-local ./ amdgpu-lib 20.50-1234664 [2.132 B] 
Get:32 file:/var/opt/amdgpu-pro-local ./ amdgpu 20.50-1234664 [1.688 B] 
Get:33 file:/var/opt/amdgpu-pro-local ./ libxatracker2-amdgpu 1:20.2.4-1234664 [999 kB] 
Get:34 file:/var/opt/amdgpu-pro-local ./ libgbm1-amdgpu 1:20.2.4-1234664 [30,5 kB] 
Get:35 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-mesa 1:20.2.4-1234664 [112 kB] 
Get:36 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-mesa-drivers 1:20.2.4-1234664 [4.344 B] 
Get:37 file:/var/opt/amdgpu-pro-local ./ libgles1-amdgpu-mesa 1:20.2.4-1234664 [8.308 B] 
Get:38 file:/var/opt/amdgpu-pro-local ./ libgles2-amdgpu-mesa 1:20.2.4-1234664 [11,9 kB] 
Get:39 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-mesa-glx 1:20.2.4-1234664 [154 kB] 
Get:40 file:/var/opt/amdgpu-pro-local ./ libosmesa6-amdgpu 1:20.2.4-1234664 [3.503 kB] 
Get:41 file:/var/opt/amdgpu-pro-local ./ mesa-amdgpu-vdpau-drivers 1:20.2.4-1234664 [2.686 kB] 
Get:42 file:/var/opt/amdgpu-pro-local ./ amdgpu-lib32 20.50-1234664 [1.828 B] 
Get:43 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-core 20.50-1234664 [5.552 B] 
Get:44 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-appprofiles 20.50-1234664 [22,0 kB] 
Get:45 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-glx 20.50-1234664 [189 kB] 
Get:46 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-pro 20.50-1234664 [27,9 kB] 
Get:47 file:/var/opt/amdgpu-pro-local ./ libgles2-amdgpu-pro 20.50-1234664 [19,5 kB] 
Get:48 file:/var/opt/amdgpu-pro-local ./ libglapi1-amdgpu-pro 20.50-1234664 [74,3 kB] 
Get:49 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-ext 20.50-1234664 [86,6 kB] 
Get:50 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-dri 20.50-1234664 [10,8 MB] 
Get:51 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro 20.50-1234664 [5.324 B] 
Get:52 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-glx 20.50-1234664 [191 kB] 
Get:53 file:/var/opt/amdgpu-pro-local ./ libegl1-amdgpu-pro 20.50-1234664 [34,4 kB] 
Get:54 file:/var/opt/amdgpu-pro-local ./ libgles2-amdgpu-pro 20.50-1234664 [34,5 kB] 
Get:55 file:/var/opt/amdgpu-pro-local ./ libglapi1-amdgpu-pro 20.50-1234664 [63,5 kB] 
Get:56 file:/var/opt/amdgpu-pro-local ./ libgl1-amdgpu-pro-dri 20.50-1234664 [11,8 MB] 
Get:57 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-lib32 20.50-1234664 [5.080 B] 
Get:58 file:/var/opt/amdgpu-pro-local ./ hsakmt-roct-amdgpu 1.0.9-1234664 [53,5 kB] 
Get:59 file:/var/opt/amdgpu-pro-local ./ hsa-runtime-rocr-amdgpu 1.2.0-1234664 [413 kB] 
Get:60 file:/var/opt/amdgpu-pro-local ./ comgr-amdgpu-pro 1.9.0-1234664 [29,3 MB] 
Get:61 file:/var/opt/amdgpu-pro-local ./ ocl-icd-libopencl1-amdgpu-pro 20.50-1234664 [13,9 kB] 
Get:62 file:/var/opt/amdgpu-pro-local ./ opencl-rocr-amdgpu-pro 20.50-1234664 [418 kB] 
Get:63 file:/var/opt/amdgpu-pro-local ./ hip-rocr-amdgpu-pro 20.50-1234664 [778 kB] 
Get:64 file:/var/opt/amdgpu-pro-local ./ clinfo-amdgpu-pro 20.50-1234664 [30,8 kB] 
Get:65 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-rocr-opencl 20.50-1234664 [5.400 B] 
Get:66 file:/var/opt/amdgpu-pro-local ./ opencl-orca-amdgpu-pro-icd 20.50-1234664 [30,6 MB] 
Get:67 file:/var/opt/amdgpu-pro-local ./ vulkan-amdgpu-pro 20.50-1234664 [7.515 kB] 
Extracting templates from packages: 100% 
Selecting previously unselected package amdgpu-dkms-firmware. 
(Reading database ... 145461 files and directories currently installed.) 
Preparing to unpack .../amdgpu-dkms-firmware_5.9.10.69-1234664_all.deb ... 
Unpacking amdgpu-dkms-firmware (1:5.9.10.69-1234664) ... 
Setting up amdgpu-dkms-firmware (1:5.9.10.69-1234664) ... 
Selecting previously unselected package amdgpu-dkms. 
(Reading database ... 145862 files and directories currently installed.) 
Preparing to unpack .../0-amdgpu-dkms_5.9.10.69-1234664_all.deb ... 
Unpacking amdgpu-dkms (1:5.9.10.69-1234664) ... 
Selecting previously unselected package amdgpu-core. 
Preparing to unpack .../1-amdgpu-core_20.50-1234664_all.deb ... 
Unpacking amdgpu-core (20.50-1234664) ... 
Selecting previously unselected package libdrm2-amdgpu:amd64. 
Preparing to unpack .../2-libdrm2-amdgpu_2.4.100-1234664_amd64.deb ... 
Unpacking libdrm2-amdgpu:amd64 (1:2.4.100-1234664) ... 
Selecting previously unselected package libdrm-amdgpu-common. 
Preparing to unpack .../3-libdrm-amdgpu-common_1.0.0-1234664_all.deb ... 
Unpacking libdrm-amdgpu-common (1.0.0-1234664) ... 
Selecting previously unselected package libdrm-amdgpu-amdgpu1:amd64. 
Preparing to unpack .../4-libdrm-amdgpu-amdgpu1_2.4.100-1234664_amd64.deb ... 
Unpacking libdrm-amdgpu-amdgpu1:amd64 (1:2.4.100-1234664) ... 
Selecting previously unselected package libdrm-amdgpu-radeon1:amd64. 
Preparing to unpack .../5-libdrm-amdgpu-radeon1_2.4.100-1234664_amd64.deb ... 
Unpacking libdrm-amdgpu-radeon1:amd64 (1:2.4.100-1234664) ... 
Selecting previously unselected package libllvm11.0-amdgpu:amd64. 
Preparing to unpack .../6-libllvm11.0-amdgpu_11.0-1234664_amd64.deb ... 
Unpacking libllvm11.0-amdgpu:amd64 (1:11.0-1234664) ... 
Selecting previously unselected package mesa-amdgpu-va-drivers:amd64. 
Preparing to unpack .../7-mesa-amdgpu-va-drivers_20.2.4-1234664_amd64.deb ... 
Unpacking mesa-amdgpu-va-drivers:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libglapi-amdgpu-mesa:amd64. 
Preparing to unpack .../8-libglapi-amdgpu-mesa_20.2.4-1234664_amd64.deb ... 
Unpacking libglapi-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Setting up amdgpu-core (20.50-1234664) ... 
Setting up libdrm2-amdgpu:amd64 (1:2.4.100-1234664) ... 
Setting up libdrm-amdgpu-common (1.0.0-1234664) ... 
Setting up libdrm-amdgpu-amdgpu1:amd64 (1:2.4.100-1234664) ... 
Setting up libdrm-amdgpu-radeon1:amd64 (1:2.4.100-1234664) ... 
Setting up libllvm11.0-amdgpu:amd64 (1:11.0-1234664) ... 
Setting up mesa-amdgpu-va-drivers:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-mesa-dri:amd64. 
(Reading database ... 148073 files and directories currently installed.) 
Preparing to unpack .../0-libgl1-amdgpu-mesa-dri_20.2.4-1234664_amd64.deb ... 
Unpacking libgl1-amdgpu-mesa-dri:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libdrm2-amdgpu:i386. 
Preparing to unpack .../1-libdrm2-amdgpu_2.4.100-1234664_i386.deb ... 
Unpacking libdrm2-amdgpu:i386 (1:2.4.100-1234664) ... 
Selecting previously unselected package libdrm-amdgpu-amdgpu1:i386. 
Preparing to unpack .../2-libdrm-amdgpu-amdgpu1_2.4.100-1234664_i386.deb ... 
Unpacking libdrm-amdgpu-amdgpu1:i386 (1:2.4.100-1234664) ... 
Selecting previously unselected package libdrm-amdgpu-radeon1:i386. 
Preparing to unpack .../3-libdrm-amdgpu-radeon1_2.4.100-1234664_i386.deb ... 
Unpacking libdrm-amdgpu-radeon1:i386 (1:2.4.100-1234664) ... 
Selecting previously unselected package libllvm11.0-amdgpu:i386. 
Preparing to unpack .../4-libllvm11.0-amdgpu_11.0-1234664_i386.deb ... 
Unpacking libllvm11.0-amdgpu:i386 (1:11.0-1234664) ... 
Selecting previously unselected package mesa-amdgpu-va-drivers:i386. 
Preparing to unpack .../5-mesa-amdgpu-va-drivers_20.2.4-1234664_i386.deb ... 
Unpacking mesa-amdgpu-va-drivers:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libglapi-amdgpu-mesa:i386. 
Preparing to unpack .../6-libglapi-amdgpu-mesa_20.2.4-1234664_i386.deb ... 
Unpacking libglapi-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Setting up libdrm2-amdgpu:i386 (1:2.4.100-1234664) ... 
Setting up libdrm-amdgpu-amdgpu1:i386 (1:2.4.100-1234664) ... 
Setting up libdrm-amdgpu-radeon1:i386 (1:2.4.100-1234664) ... 
Setting up libllvm11.0-amdgpu:i386 (1:11.0-1234664) ... 
Setting up mesa-amdgpu-va-drivers:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-mesa-dri:i386. 
(Reading database ... 148109 files and directories currently installed.) 
Preparing to unpack .../00-libgl1-amdgpu-mesa-dri_20.2.4-1234664_i386.deb ... 
Unpacking libgl1-amdgpu-mesa-dri:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libxatracker2-amdgpu:amd64. 
Preparing to unpack .../01-libxatracker2-amdgpu_20.2.4-1234664_amd64.deb ... 
Unpacking libxatracker2-amdgpu:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgbm1-amdgpu:amd64. 
Preparing to unpack .../02-libgbm1-amdgpu_20.2.4-1234664_amd64.deb ... 
Unpacking libgbm1-amdgpu:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-mesa:amd64. 
Preparing to unpack .../03-libegl1-amdgpu-mesa_20.2.4-1234664_amd64.deb ... 
Unpacking libegl1-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-mesa-drivers:amd64. 
Preparing to unpack .../04-libegl1-amdgpu-mesa-drivers_20.2.4-1234664_amd64.deb  
... 
Unpacking libegl1-amdgpu-mesa-drivers:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgles1-amdgpu-mesa:amd64. 
Preparing to unpack .../05-libgles1-amdgpu-mesa_20.2.4-1234664_amd64.deb ... 
Unpacking libgles1-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgles2-amdgpu-mesa:amd64. 
Preparing to unpack .../06-libgles2-amdgpu-mesa_20.2.4-1234664_amd64.deb ... 
Unpacking libgles2-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-mesa-glx:amd64. 
Preparing to unpack .../07-libgl1-amdgpu-mesa-glx_20.2.4-1234664_amd64.deb ... 
Unpacking libgl1-amdgpu-mesa-glx:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package libosmesa6-amdgpu:amd64. 
Preparing to unpack .../08-libosmesa6-amdgpu_20.2.4-1234664_amd64.deb ... 
Unpacking libosmesa6-amdgpu:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package mesa-amdgpu-vdpau-drivers:amd64. 
Preparing to unpack .../09-mesa-amdgpu-vdpau-drivers_20.2.4-1234664_amd64.deb .. 
. 
Unpacking mesa-amdgpu-vdpau-drivers:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package mesa-amdgpu-omx-drivers:amd64. 
Preparing to unpack .../10-mesa-amdgpu-omx-drivers_20.2.4-1234664_amd64.deb ... 
Unpacking mesa-amdgpu-omx-drivers:amd64 (1:20.2.4-1234664) ... 
Selecting previously unselected package xserver-xorg-amdgpu-video-amdgpu. 
Preparing to unpack .../11-xserver-xorg-amdgpu-video-amdgpu_19.1.0-1234664_amd64 
.deb ... 
Unpacking xserver-xorg-amdgpu-video-amdgpu (1:19.1.0-1234664) ... 
Selecting previously unselected package gst-omx-amdgpu. 
Preparing to unpack .../12-gst-omx-amdgpu_1.0.0.1-1234664_amd64.deb ... 
Unpacking gst-omx-amdgpu (1.0.0.1-1234664) ... 
Selecting previously unselected package amdgpu-lib. 
Preparing to unpack .../13-amdgpu-lib_20.50-1234664_amd64.deb ... 
Unpacking amdgpu-lib (20.50-1234664) ... 
Selecting previously unselected package amdgpu. 
Preparing to unpack .../14-amdgpu_20.50-1234664_amd64.deb ... 
Unpacking amdgpu (20.50-1234664) ... 
Selecting previously unselected package libxatracker2-amdgpu:i386. 
Preparing to unpack .../15-libxatracker2-amdgpu_20.2.4-1234664_i386.deb ... 
Unpacking libxatracker2-amdgpu:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgbm1-amdgpu:i386. 
Preparing to unpack .../16-libgbm1-amdgpu_20.2.4-1234664_i386.deb ... 
Unpacking libgbm1-amdgpu:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-mesa:i386. 
Preparing to unpack .../17-libegl1-amdgpu-mesa_20.2.4-1234664_i386.deb ... 
Unpacking libegl1-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-mesa-drivers:i386. 
Preparing to unpack .../18-libegl1-amdgpu-mesa-drivers_20.2.4-1234664_i386.deb . 
.. 
Unpacking libegl1-amdgpu-mesa-drivers:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgles1-amdgpu-mesa:i386. 
Preparing to unpack .../19-libgles1-amdgpu-mesa_20.2.4-1234664_i386.deb ... 
Unpacking libgles1-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgles2-amdgpu-mesa:i386. 
Preparing to unpack .../20-libgles2-amdgpu-mesa_20.2.4-1234664_i386.deb ... 
Unpacking libgles2-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-mesa-glx:i386. 
Preparing to unpack .../21-libgl1-amdgpu-mesa-glx_20.2.4-1234664_i386.deb ... 
Unpacking libgl1-amdgpu-mesa-glx:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package libosmesa6-amdgpu:i386. 
Preparing to unpack .../22-libosmesa6-amdgpu_20.2.4-1234664_i386.deb ... 
Unpacking libosmesa6-amdgpu:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package mesa-amdgpu-vdpau-drivers:i386. 
Preparing to unpack .../23-mesa-amdgpu-vdpau-drivers_20.2.4-1234664_i386.deb ... 
Unpacking mesa-amdgpu-vdpau-drivers:i386 (1:20.2.4-1234664) ... 
Selecting previously unselected package amdgpu-lib32. 
Preparing to unpack .../24-amdgpu-lib32_20.50-1234664_amd64.deb ... 
Unpacking amdgpu-lib32 (20.50-1234664) ... 
Selecting previously unselected package amdgpu-pro-core. 
Preparing to unpack .../25-amdgpu-pro-core_20.50-1234664_all.deb ... 
Unpacking amdgpu-pro-core (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-appprofiles. 
Preparing to unpack .../26-libgl1-amdgpu-pro-appprofiles_20.50-1234664_all.deb . 
.. 
Unpacking libgl1-amdgpu-pro-appprofiles (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-glx:amd64. 
Preparing to unpack .../27-libgl1-amdgpu-pro-glx_20.50-1234664_amd64.deb ... 
Unpacking libgl1-amdgpu-pro-glx:amd64 (20.50-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-pro:amd64. 
Preparing to unpack .../28-libegl1-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking libegl1-amdgpu-pro:amd64 (20.50-1234664) ... 
Selecting previously unselected package libgles2-amdgpu-pro:amd64. 
Preparing to unpack .../29-libgles2-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking libgles2-amdgpu-pro:amd64 (20.50-1234664) ... 
Selecting previously unselected package libglapi1-amdgpu-pro:amd64. 
Preparing to unpack .../30-libglapi1-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking libglapi1-amdgpu-pro:amd64 (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-ext:amd64. 
Preparing to unpack .../31-libgl1-amdgpu-pro-ext_20.50-1234664_amd64.deb ... 
Unpacking libgl1-amdgpu-pro-ext:amd64 (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-dri:amd64. 
Preparing to unpack .../32-libgl1-amdgpu-pro-dri_20.50-1234664_amd64.deb ... 
Unpacking libgl1-amdgpu-pro-dri:amd64 (20.50-1234664) ... 
Selecting previously unselected package amdgpu-pro. 
Preparing to unpack .../33-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking amdgpu-pro (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-glx:i386. 
Preparing to unpack .../34-libgl1-amdgpu-pro-glx_20.50-1234664_i386.deb ... 
Unpacking libgl1-amdgpu-pro-glx:i386 (20.50-1234664) ... 
Selecting previously unselected package libegl1-amdgpu-pro:i386. 
Preparing to unpack .../35-libegl1-amdgpu-pro_20.50-1234664_i386.deb ... 
Unpacking libegl1-amdgpu-pro:i386 (20.50-1234664) ... 
Selecting previously unselected package libgles2-amdgpu-pro:i386. 
Preparing to unpack .../36-libgles2-amdgpu-pro_20.50-1234664_i386.deb ... 
Unpacking libgles2-amdgpu-pro:i386 (20.50-1234664) ... 
Selecting previously unselected package libglapi1-amdgpu-pro:i386. 
Preparing to unpack .../37-libglapi1-amdgpu-pro_20.50-1234664_i386.deb ... 
Unpacking libglapi1-amdgpu-pro:i386 (20.50-1234664) ... 
Selecting previously unselected package libgl1-amdgpu-pro-dri:i386. 
Preparing to unpack .../38-libgl1-amdgpu-pro-dri_20.50-1234664_i386.deb ... 
Unpacking libgl1-amdgpu-pro-dri:i386 (20.50-1234664) ... 
Selecting previously unselected package amdgpu-pro-lib32. 
Preparing to unpack .../39-amdgpu-pro-lib32_20.50-1234664_amd64.deb ... 
Unpacking amdgpu-pro-lib32 (20.50-1234664) ... 
Selecting previously unselected package hsakmt-roct-amdgpu:amd64. 
Preparing to unpack .../40-hsakmt-roct-amdgpu_1.0.9-1234664_amd64.deb ... 
Unpacking hsakmt-roct-amdgpu:amd64 (1.0.9-1234664) ... 
Selecting previously unselected package hsa-runtime-rocr-amdgpu:amd64. 
Preparing to unpack .../41-hsa-runtime-rocr-amdgpu_1.2.0-1234664_amd64.deb ... 
Unpacking hsa-runtime-rocr-amdgpu:amd64 (1.2.0-1234664) ... 
Selecting previously unselected package comgr-amdgpu-pro:amd64. 
Preparing to unpack .../42-comgr-amdgpu-pro_1.9.0-1234664_amd64.deb ... 
Unpacking comgr-amdgpu-pro:amd64 (1.9.0-1234664) ... 
Selecting previously unselected package ocl-icd-libopencl1-amdgpu-pro:amd64. 
Preparing to unpack .../43-ocl-icd-libopencl1-amdgpu-pro_20.50-1234664_amd64.deb 
 ... 
Unpacking ocl-icd-libopencl1-amdgpu-pro:amd64 (20.50-1234664) ... 
Selecting previously unselected package opencl-rocr-amdgpu-pro:amd64. 
Preparing to unpack .../44-opencl-rocr-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking opencl-rocr-amdgpu-pro:amd64 (20.50-1234664) ... 
Selecting previously unselected package hip-rocr-amdgpu-pro. 
Preparing to unpack .../45-hip-rocr-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking hip-rocr-amdgpu-pro (20.50-1234664) ... 
Selecting previously unselected package clinfo-amdgpu-pro. 
Preparing to unpack .../46-clinfo-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking clinfo-amdgpu-pro (20.50-1234664) ... 
Selecting previously unselected package amdgpu-pro-rocr-opencl. 
Preparing to unpack .../47-amdgpu-pro-rocr-opencl_20.50-1234664_amd64.deb ... 
Unpacking amdgpu-pro-rocr-opencl (20.50-1234664) ... 
Selecting previously unselected package opencl-orca-amdgpu-pro-icd:amd64. 
Preparing to unpack .../48-opencl-orca-amdgpu-pro-icd_20.50-1234664_amd64.deb .. 
. 
Unpacking opencl-orca-amdgpu-pro-icd:amd64 (20.50-1234664) ... 
Selecting previously unselected package vulkan-amdgpu-pro:amd64. 
Preparing to unpack .../49-vulkan-amdgpu-pro_20.50-1234664_amd64.deb ... 
Unpacking vulkan-amdgpu-pro:amd64 (20.50-1234664) ... 
Setting up libxatracker2-amdgpu:amd64 (1:20.2.4-1234664) ... 
Setting up libxatracker2-amdgpu:i386 (1:20.2.4-1234664) ... 
Setting up libgbm1-amdgpu:amd64 (1:20.2.4-1234664) ... 
Setting up libgbm1-amdgpu:i386 (1:20.2.4-1234664) ... 
Setting up gst-omx-amdgpu (1.0.0.1-1234664) ... 
Setting up hsakmt-roct-amdgpu:amd64 (1.0.9-1234664) ... 
Setting up libglapi-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Setting up libglapi-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Setting up mesa-amdgpu-vdpau-drivers:amd64 (1:20.2.4-1234664) ... 
Setting up mesa-amdgpu-vdpau-drivers:i386 (1:20.2.4-1234664) ... 
Setting up libgles1-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Setting up libgles1-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Setting up amdgpu-dkms (1:5.9.10.69-1234664) ... 
Loading new amdgpu-5.9.10.69-1234664 DKMS files... 
Building for 5.11.0-13-generic 
Building for architecture x86_64 
Building initial module for 5.11.0-13-generic 
ERROR (dkms apport): kernel package linux-headers-5.11.0-13-generic is not suppo 
rted 
Error! Bad return status for module build on kernel: 5.11.0-13-generic (x86_64) 
Consult /var/lib/dkms/amdgpu/5.9.10.69-1234664/build/make.log for more informati 
on. 
dpkg: error processing package amdgpu-dkms (--configure): 
 installed amdgpu-dkms package post-installation script subprocess returned erro 
r exit status 10 
dpkg: dependency problems prevent configuration of amdgpu: 
 amdgpu depends on amdgpu-dkms (= 1:5.9.10.69-1234664); however: 
  Package amdgpu-dkms is not configured yet. 
 
dpkg: error processing package amdgpu (--configure): 
 dependency problems - leaving unconfigured 
Setting up xserver-xorg-amdgpu-video-amdgpu (1:19.1.0-1234664) ... 
No apport report written because the error message indicates its a followup erro 
r from a previous failure. 
                          Setting up mesa-amdgpu-omx-drivers:amd64 (1:20.2.4-123 
4664) ... 
Setting up libegl1-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Setting up libegl1-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Setting up libgl1-amdgpu-mesa-glx:amd64 (1:20.2.4-1234664) ... 
Setting up libgl1-amdgpu-mesa-glx:i386 (1:20.2.4-1234664) ... 
Setting up amdgpu-pro-core (20.50-1234664) ... 
Setting up libgles2-amdgpu-mesa:amd64 (1:20.2.4-1234664) ... 
Setting up libgles2-amdgpu-mesa:i386 (1:20.2.4-1234664) ... 
Setting up opencl-orca-amdgpu-pro-icd:amd64 (20.50-1234664) ... 
Setting up libgl1-amdgpu-mesa-dri:amd64 (1:20.2.4-1234664) ... 
Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.2.4-1234664) ... 
dpkg: dependency problems prevent configuration of amdgpu-pro-rocr-opencl: 
 amdgpu-pro-rocr-opencl depends on amdgpu-dkms (= 1:5.9.10.69-1234664); however: 
  Package amdgpu-dkms is not configured yet. 
 
dpkg: error processing package amdgpu-pro-rocr-opencl (--configure): 
 dependency problems - leaving unconfigured 
Setting up vulkan-amdgpu-pro:amd64 (20.50-1234664) ... 
No apport report written because the error message indicates its a followup erro 
r from a previous failure. 
                          Setting up libosmesa6-amdgpu:amd64 (1:20.2.4-1234664)  
... 
Setting up libosmesa6-amdgpu:i386 (1:20.2.4-1234664) ... 
dpkg: dependency problems prevent configuration of amdgpu-pro: 
 amdgpu-pro depends on amdgpu (= 20.50-1234664); however: 
  Package amdgpu is not configured yet. 
 
dpkg: error processing package amdgpu-pro (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              Setting up comgr-a 
mdgpu-pro:amd64 (1.9.0-1234664) ... 
Setting up hsa-runtime-rocr-amdgpu:amd64 (1.2.0-1234664) ... 
Setting up ocl-icd-libopencl1-amdgpu-pro:amd64 (20.50-1234664) ... 
Setting up clinfo-amdgpu-pro (20.50-1234664) ... 
Setting up hip-rocr-amdgpu-pro (20.50-1234664) ... 
dpkg: dependency problems prevent configuration of amdgpu-pro-lib32: 
 amdgpu-pro-lib32 depends on amdgpu (= 20.50-1234664) | amdgpu-hwe (= 20.50-1234 
664); however: 
  Package amdgpu is not configured yet. 
  Package amdgpu-hwe is not installed. 
 amdgpu-pro-lib32 depends on amdgpu-pro (= 20.50-1234664) | amdgpu-pro-hwe (= 20 
.50-1234664); however: 
  Package amdgpu-pro is not configured yet. 
  Package amdgpu-pro-hwe is not installed. 
 
dpkg: error processing package amdgpu-pro-lib32 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libglapi1-amdgpu-pro:amd64 (20.50-1234664) ... 
No apport report written because MaxReports is reached already 
                                                              Setting up libglap 
i1-amdgpu-pro:i386 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-dri:amd64 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-dri:i386 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-appprofiles (20.50-1234664) ... 
Setting up libegl1-amdgpu-pro:amd64 (20.50-1234664) ... 
Setting up libegl1-amdgpu-pro:i386 (20.50-1234664) ... 
Setting up libegl1-amdgpu-mesa-drivers:amd64 (1:20.2.4-1234664) ... 
Setting up libegl1-amdgpu-mesa-drivers:i386 (1:20.2.4-1234664) ... 
Setting up libgles2-amdgpu-pro:amd64 (20.50-1234664) ... 
Setting up libgles2-amdgpu-pro:i386 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-glx:amd64 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-glx:i386 (20.50-1234664) ... 
Setting up opencl-rocr-amdgpu-pro:amd64 (20.50-1234664) ... 
Setting up libgl1-amdgpu-pro-ext:amd64 (20.50-1234664) ... 
Setting up amdgpu-lib (20.50-1234664) ... 
Setting up amdgpu-lib32 (20.50-1234664) ... 
Processing triggers for libc-bin (2.33-0ubuntu5) ... 
Errors were encountered while processing: 
 amdgpu-dkms 
 amdgpu 
 amdgpu-pro-rocr-opencl 
 amdgpu-pro 
 amdgpu-pro-lib32 
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



Building the package again will also not help:
```

$ sudo dpkg --install amdgpu-dkms_5.9.10.69-1234664_all.deb 
(Reading database ... 148363 files and directories currently installed.) 
Preparing to unpack amdgpu-dkms_5.9.10.69-1234664_all.deb ... 
 
------------------------------ 
Deleting module version: 5.9.10.69-1234664 
completely from the DKMS tree. 
------------------------------ 
Done. 
Unpacking amdgpu-dkms (1:5.9.10.69-1234664) over (1:5.9.10.69-1234664) ... 
Setting up amdgpu-dkms (1:5.9.10.69-1234664) ... 
Loading new amdgpu-5.9.10.69-1234664 DKMS files... 
Building for 5.11.0-13-generic 
Building for architecture x86_64 
Building initial module for 5.11.0-13-generic 
ERROR (dkms apport): kernel package linux-headers-5.11.0-13-generic is not supported 
Error! Bad return status for module build on kernel: 5.11.0-13-generic (x86_64) 
Consult /var/lib/dkms/amdgpu/5.9.10.69-1234664/build/make.log for more information. 
dpkg: error processing package amdgpu-dkms (--install): 
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10 
Errors were encountered while processing: 
 amdgpu-dkms

```

The log in "/var/lib/dkms/amdgpu/5.9.10.69-1234664/build/make.log" looks like this:
```
]$ cat /var/lib/dkms/amdgpu/5.9.10.69-1234664/build/make.log 
DKMS make.log for amdgpu-5.9.10.69-1234664 for kernel 5.11.0-13-generic (x86_64) 
Do 15. Apr 13:15:26 CEST 2021 
make: Entering directory '/usr/src/linux-headers-5.11.0-13-generic' 
/var/lib/dkms/amdgpu/5.9.10.69-1234664/build/Makefile:16: *** dma_resv->seq is missing., exit....  Stop. 
make: *** [Makefile:1834: /var/lib/dkms/amdgpu/5.9.10.69-1234664/build] Error 2 
make: Leaving directory '/usr/src/linux-headers-5.11.0-13-generic'
``` 

On Github I see the same issue for PopOS also:
[https://github.com/pop-os/pop/issues/1135](https://github.com/pop-os/pop/issues/1135)

Cheers
Stefan

---

### Post by Yellow Pasque on 2021-04-15
If you want OpenCL support from the Pro driver, you're probably going to have to wait until that driver supports kernel 5.11.x (i.e. "Ubuntu 20.04.3"). Just faking the Ubuntu version in the install script may get that running, but the module build is still going to fail if there are changes to newer kernels that the driver doesn't account for.

It looks like some other folks are struggling with OpenCL on a 6700XT: [https://aur.archlinux.org/packages/opencl-amd/](https://aur.archlinux.org/packages/opencl-amd/)

---

### Post by oortael1860 on 2021-04-15
Is there a way to get OpenCL without the pro driver?

---

### Post by mastablasta on 2021-04-18
why do you need the pro? AMDGPU seems to be on par.: [https://www.phoronix.com/scan.php?page=article&item=amd-drivers-sep20&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-drivers-sep20&num=1)

as i understand it pro is needed for very specific use cases. openCL could be added by manually unpacking adding libraries. for exmaple here is one such article: [https://linuxconfig.org/install-opencl-for-the-amdgpu-open-source-drivers-on-debian-and-ubuntu](https://linuxconfig.org/install-opencl-for-the-amdgpu-open-source-drivers-on-debian-and-ubuntu)

but the basic thing is that you need driver and kernel to match and then patch the kernel with this driver (as it kind of runs on top of the AMDGPU). so for example if your card need driver that needs 5.11 kernel, then you need to match that kernel with driver. same goes for any other components (if you use X11 then that one + xserver and such have to also be supported by driver).

though here is says that 20.50 should support 20.04.1 (kernel 5.4) and 20.04.2 (kernel 5.8): [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-50](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-50)

i came to that site from: [https://www.amd.com/en/support/graphics/amd-radeon-6000-series/amd-radeon-6800-series/amd-radeon-rx-6800-xt](https://www.amd.com/en/support/graphics/amd-radeon-6000-series/amd-radeon-6800-series/amd-radeon-rx-6800-xt)

i missed that you want the AMDGPU-PRO driver in original post. since amdgpu-pro is quite specific about kernels and such and you don't want the latest AMDGPU driver, then 20.04.2 will be the way to go with kernel 5.8, according to driver website.

> Radeon&#8482; Software for Linux® 20.50 Highlights

    Provide **support for the Radeon RX 6700 XT Series** of graphics cards
    Introduce full support for RHEL / CentOS 8.3
   ** Introduce preview support for Ubuntu 20.04.2**

---

