---
title: "Poor video performance on Kaby Lake processor"
date: 2017-04-30
forum: Hardware
---

### Post by ianberg on 2017-04-30
This problem may broach hardware, configuration and multimedia, but I feel it fits best here, if not I am sorry.  My machine is a Gigabyte BRIX S (GB-BKi3HA-7100) with the F4 version of bios installed. Ubuntu is installed to an SSD (fresh install 17.04). 

I downloaded some test videos and video playback on 1080 is slightly choppy, and 4k barely plays at all. I understand the Kaby-lake processor in this machine should have no problems playing even 10-bit HEVC video, but I'm lucky if it plays 1fps. A different NUC with nearly identical specs has no problem ([link]("http://nucblog.net/2017/02/nuc7i3bnh-review-linux-htpc-conclusions/")) 

I've tried hooking the computer to my monitor and my TV and the results are the same. The drivers dialog says that the proprietary drivers are in use.  I can use the display normally and there's no artifacts or choppiness when moving windows around or when I run glxgears. Youtube seems to play okay except for the tearing/choppiness that I notice.

 I am very stuck. Please help me. If you need any details or problem determination I will do it.

```
X.Org X Server 1.19.3
Release Date: 2017-03-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-70-generic x86_64 Ubuntu
Current Operating System: Linux mediaman 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-20-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
Build Date: 28 March 2017  06:16:52AM
xorg-server 2:1.19.3-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty-backports InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version (8.3.0-4).
mesa-utils set to manually installed.
nux-tools is already the newest version (4.0.8+17.04.20170213-0ubuntu1).
nux-tools set to manually installed.
The following package was automatically installed and is no longer required:
  iucode-tool
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  gawk hddtemp libsigsegv2 lm-sensors net-tools
Suggested packages:
  gawk-doc ksensors fancontrol read-edid i2c-tools
The following NEW packages will be installed
  fbset gawk hardinfo hddtemp inxi libsigsegv2 lm-sensors net-tools
0 to upgrade, 8 to newly install, 0 to remove and 0 not to upgrade.
Need to get 1,214 kB of archives.
After this operation, 4,425 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/main amd64 libsigsegv2 amd64 2.10-5 [14.1 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/main amd64 gawk amd64 1:4.1.4+dfsg-1 [401 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/main amd64 fbset amd64 2.1-28 [114 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/universe amd64 hardinfo amd64 0.5.1-1.4ubuntu3 [220 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/main amd64 net-tools amd64 1.60+git20161116.90da8a0-1ubuntu1 [194 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/universe amd64 hddtemp amd64 0.3-beta15-52 [52.8 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/universe amd64 inxi all 2.3.8-0ubuntu1 [132 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/universe amd64 lm-sensors amd64 1:3.4.0-4 [85.5 kB]
Fetched 1,214 kB in 6s (201 kB/s)                                              
Preconfiguring packages ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 208390 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-5_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-5) ...
Setting up libsigsegv2:amd64 (2.10-5) ...
Selecting previously unselected package gawk.
(Reading database ... 208398 files and directories currently installed.)
Preparing to unpack .../0-gawk_1%3a4.1.4+dfsg-1_amd64.deb ...
Unpacking gawk (1:4.1.4+dfsg-1) ...
Selecting previously unselected package fbset.
Preparing to unpack .../1-fbset_2.1-28_amd64.deb ...
Unpacking fbset (2.1-28) ...
Selecting previously unselected package hardinfo.
Preparing to unpack .../2-hardinfo_0.5.1-1.4ubuntu3_amd64.deb ...
Unpacking hardinfo (0.5.1-1.4ubuntu3) ...
Selecting previously unselected package net-tools.
Preparing to unpack .../3-net-tools_1.60+git20161116.90da8a0-1ubuntu1_amd64.deb ...
Unpacking net-tools (1.60+git20161116.90da8a0-1ubuntu1) ...
Selecting previously unselected package hddtemp.
Preparing to unpack .../4-hddtemp_0.3-beta15-52_amd64.deb ...
Unpacking hddtemp (0.3-beta15-52) ...
Selecting previously unselected package inxi.
Preparing to unpack .../5-inxi_2.3.8-0ubuntu1_all.deb ...
Unpacking inxi (2.3.8-0ubuntu1) ...
Selecting previously unselected package lm-sensors.
Preparing to unpack .../6-lm-sensors_1%3a3.4.0-4_amd64.deb ...
Unpacking lm-sensors (1:3.4.0-4) ...
Setting up hardinfo (0.5.1-1.4ubuntu3) ...
Setting up hddtemp (0.3-beta15-52) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Setting up gawk (1:4.1.4+dfsg-1) ...
Processing triggers for bamfdaemon (0.5.3+17.04.20170406-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Setting up lm-sensors (1:3.4.0-4) ...
Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594; /lib/systemd/system/lm-sensors.service.
Setting up inxi (2.3.8-0ubuntu1) ...
Processing triggers for systemd (232-21ubuntu3) ...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Setting up net-tools (1.60+git20161116.90da8a0-1ubuntu1) ...
Setting up fbset (2.1-28) ...
Processing triggers for ureadahead (0.100.0-19) ...
System:    Host: mediaman Kernel: 4.10.0-20-generic x86_64 (64 bit)
           Desktop: Gnome Distro: Ubuntu 17.04
Machine:   Device: laptop Mobo: GIGABYTE model: MFLP3AP-00 v: 1.x
           UEFI: American Megatrends v: F4 date: 02/20/2017
CPU:       Dual core Intel Core i3-7100U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2400 MHz 1: 1424 MHz 2: 790 MHz 3: 731 MHz
           4: 763 MHz
Graphics:  Card: Intel Device 5916
           Display Server: X.Org 1.19.3 driver: intel
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 17.0.3
Audio:     Card Intel Device 9d71 driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-20-generic
Network:   Card-1: Intel Ethernet Connection I219-LM driver: e1000e
           IF: enp0s31f6 state: down mac: 1c:1b:0d:8f:9e:11
           Card-2: Intel Device 24fb driver: iwlwifi
           IF: wlp2s0 state: up speed: N/A duplex: N/A mac: 30:e3:7a:92:8a:10
Drives:    HDD Total Size: 120.0GB (13.1% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 120.0GB
Partition: ID-1: / size: 102G used: 7.2G (8%) fs: ext4 dev: /dev/dm-0
           ID-2: swap-1 size: 8.46GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 46.5C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 213 Uptime: 11 min Memory: 1152.1/7858.3MB
           Client: Shell (bash) inxi: 2.3.8 

mode "1920x1080"
    geometry 1920 1080 1920 1080 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : inteldrmfb
    Address     : 0xc0240000
    Size        : 8294400
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 7680
    Accelerator : No
Version: 1:7.7+16ubuntu3
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 520mm x 290mm
   1920x1080     60.00*   50.00    59.94    30.00    24.00    29.97    23.98  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
fglrxinfo: command not found
The program 'nvidia-settings' is currently not installed. You can install it by typing:
sudo apt install nvidia-settings
H/W path         Device     Class          Description
======================================================
                            system         GB-BKi3(H)A-7100 (Default string)
/0                          bus            MFLP3AP-00
/0/0                        memory         64KiB BIOS
/0/3d                       memory         8GiB System Memory
/0/3d/0                     memory         4GiB SODIMM DDR4 Synchronous 2133 MHz
/0/3d/1                     memory         4GiB SODIMM DDR4 Synchronous 2133 MHz
/0/41                       memory         128KiB L1 cache
/0/42                       memory         512KiB L2 cache
/0/43                       memory         3MiB L3 cache
/0/44                       processor      Intel(R) Core(TM) i3-7100U CPU @ 2.40
/0/100                      bridge         Intel Corporation
/0/100/2                    display        Intel Corporation
/0/100/14                   bus            Sunrise Point-LP USB 3.0 xHCI Control
/0/100/14/0      usb1       bus            xHCI Host Controller
/0/100/14/0/4               input          Wired Keyboard 600
/0/100/14/0/7               communication  Bluetooth wireless interface
/0/100/14/1      usb2       bus            xHCI Host Controller
/0/100/14.2                 generic        Sunrise Point-LP Thermal subsystem
/0/100/16                   communication  Sunrise Point-LP CSME HECI #1
/0/100/17                   storage        Sunrise Point-LP SATA Controller [AHC
/0/100/1c                   bridge         Intel Corporation
/0/100/1c/0                 bus            ASM1142 USB 3.1 Host Controller
/0/100/1c/0/0    usb3       bus            xHCI Host Controller
/0/100/1c/0/0/2             input          USB Receiver
/0/100/1c/0/1    usb4       bus            xHCI Host Controller
/0/100/1c.5                 bridge         Sunrise Point-LP PCI Express Root Por
/0/100/1c.5/0    wlp2s0     network        Intel Corporation
/0/100/1f                   bridge         Intel Corporation
/0/100/1f.2                 memory         Memory controller
/0/100/1f.3                 multimedia     Intel Corporation
/0/100/1f.4                 bus            Sunrise Point-LP SMBus
/0/100/1f.6      enp0s31f6  network        Ethernet Connection I219-LM
/0/1             scsi0      storage        
/0/1/0.0.0       /dev/sda   disk           120GB Samsung SSD 850
/0/1/0.0.0/1                volume         511MiB Windows FAT volume
/0/1/0.0.0/2     /dev/sda2  volume         111GiB LVM Physical Volume
/1                          power          To Be Filled By O.E.M.
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:132 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
ii  gir1.2-ibus-1.0:amd64                                            1.5.14-2ubuntu1                             amd64        Intelligent Input Bus - introspection data
ii  i965-va-driver:amd64                                             1.7.3-1                                     amd64        VAAPI driver for Intel G45 & HD Graphics family
ii  ibus                                                             1.5.14-2ubuntu1                             amd64        Intelligent Input Bus - core
ii  ibus-gtk:amd64                                                   1.5.14-2ubuntu1                             amd64        Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3:amd64                                                  1.5.14-2ubuntu1                             amd64        Intelligent Input Bus - GTK+3 support
ii  intel-gpu-tools                                                  1.17-1                                      amd64        tools for debugging the Intel graphics driver
rc  intel-microcode                                                  3.20161104.1                                amd64        Processor microcode firmware for Intel CPUs
ii  iucode-tool                                                      2.1.1-1                                     amd64        Intel processor microcode tool
ii  libcilkrts5:amd64                                                6.3.0-12ubuntu2                             amd64        Intel Cilk Plus language extensions (runtime)
ii  libdrm-intel1:amd64                                              2.4.76-1                                    amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                                            2.4.76-1                                    amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                                             2.4.76-1                                    amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libegl1-mesa:amd64                                               17.0.3-1ubuntu1                             amd64        free implementation of the EGL API -- runtime
ii  libgl1-mesa-dri:amd64                                            17.0.3-1ubuntu1                             amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                                            17.0.3-1ubuntu1                             amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                                              17.0.3-1ubuntu1                             amd64        free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                                              17.0.3-1ubuntu1                             amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                                               9.0.0-2.1build1                             amd64        Mesa OpenGL utility library (GLU)
ii  libibus-1.0-5:amd64                                              1.5.14-2ubuntu1                             amd64        Intelligent Input Bus - shared library
ii  libmpx2:amd64                                                    6.3.0-12ubuntu2                             amd64        Intel memory protection extensions (runtime)
ii  libtxc-dxtn-s2tc:amd64                                           1.0+git20151227-2                           amd64        Texture compression library for Mesa
ii  libwayland-egl1-mesa:amd64                                       17.0.3-1ubuntu1                             amd64        implementation of the Wayland EGL platform -- runtime
ii  mesa-utils                                                       8.3.0-4                                     amd64        Miscellaneous Mesa GL utilities
ii  mesa-va-drivers:amd64                                            17.0.3-1ubuntu1                             amd64        Mesa VA-API video acceleration drivers
ii  mesa-vdpau-drivers:amd64                                         17.0.3-1ubuntu1                             amd64        Mesa VDPAU video acceleration drivers
ii  mesa-vulkan-drivers:amd64                                        17.0.3-1ubuntu1                             amd64        Mesa Vulkan graphics drivers
ii  mir-client-platform-mesa5:amd64                                  0.26.2+17.04.20170322.1-0ubuntu2            amd64        Display server for Ubuntu - client platform library for Mesa
ii  mir-platform-graphics-mesa-kms12:amd64                           0.26.2+17.04.20170322.1-0ubuntu2            amd64        Display server for Ubuntu - platform library for KMS Mesa
ii  mir-platform-graphics-mesa-x12:amd64                             0.26.2+17.04.20170322.1-0ubuntu2            amd64        Display server for Ubuntu - platform library for X11 Mesa
ii  xserver-xorg-video-ati                                           1:7.9.0-0ubuntu1                            amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-intel                                         2:2.99.917+git20170309-0ubuntu1             amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                                       1:1.0.14-0ubuntu1                           amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon                                        1:7.9.0-0ubuntu1                            amd64        X.Org X server -- AMD/ATI Radeon display driver
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
[    0.000000]   Intel GenuineIntel
[    0.000000] ACPI: HPET 0x000000008AB40830 000038 (v01 INTEL  KBL-ULT  00000001 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x000000008AB40868 000E3B (v02 INTEL  Ther_Rvp 00001000 INTL 20160422)
[    0.000000] ACPI: SSDT 0x000000008AB416A8 00090B (v02 INTEL  xh_rvp07 00000000 INTL 20160422)
[    0.000000] ACPI: UEFI 0x000000008AB41FB8 000042 (v01 INTEL  EDK2     00000002      01000013)
[    0.000000] ACPI: LPIT 0x000000008AB42EE0 000094 (v01 INTEL  KBL-ULT  00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x000000008AB42F78 00029F (v02 INTEL  sensrhub 00000000 INTL 20160422)
[    0.000000] ACPI: SSDT 0x000000008AB43218 00357E (v02 INTEL  PtidDevc 00001000 INTL 20160422)
[    0.000000] ACPI: DBGP 0x000000008AB46798 000034 (v01 INTEL           00000002 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x000000008AB467D0 000054 (v00 INTEL           00000002 MSFT 0000005F)
[    0.000000] ACPI: DMAR 0x000000008AB46860 0000A8 (v01 INTEL  KBL      00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x000000008AB46908 000183 (v01 Intel  IntelRMT 00001000 INTL 20160422)
[    0.000000] ACPI: ASF! 0x000000008AB46A90 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] Reserving Intel graphics memory at 0x000000008c000000-0x000000008fffffff
[    0.100211] smpboot: CPU0: Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz (family: 0x6, model: 0x8e, stepping: 0x9)
[    0.100254] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.160088] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.169712] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.188816] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.197431] pci 0000:00:02.0: vgaarb: setting as boot VGA device
[    0.197432] pci 0000:00:02.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.197435] pci 0000:00:02.0: vgaarb: bridge control possible
[    0.197435] vgaarb: loaded
[    0.904274] fb0: EFI VGA frame buffer device
[    0.904279] intel_idle: MWAIT substates: 0x11142120
[    0.904279] intel_idle: v0.4.1 model 0x8E
[    0.904468] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.185350] intel_pstate: Intel P-state driver initializing
[    2.185505] intel_pstate: HWP enabled
[    2.203933] intel_pmc_core 0000:00:1f.2: enabling device (0000 -> 0002)
[    2.206810] Segment Routing with IPv6
[    2.287475] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    2.287476] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    2.537778] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    2.538791] fb: switching to inteldrmfb from EFI VGA
[    2.538914] [drm] Replacing VGA console driver
[    2.553626] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.822580] [drm] failed to retrieve link info, disabling eDP
[    3.534281] fbcon: inteldrmfb (fb0) is primary device
[    3.534361] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.981084] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    4.111272] Bluetooth: HCI UART protocol Intel registered
[    4.174313] Bluetooth: hci0: read Intel version: 370810225019140f1d
[    4.174314] Bluetooth: hci0: Intel device is already patched. patch num: 1d
[    4.230092] Intel(R) Wireless WiFi driver for Linux
[    4.230093] Copyright(c) 2003- 2015 Intel Corporation
[    4.233522] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3168-26.ucode failed with error -2
[    4.233541] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3168-25.ucode failed with error -2
[    4.233553] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3168-24.ucode failed with error -2
[    4.233564] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3168-23.ucode failed with error -2
[    4.269631] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[    4.347136] intel_rapl: Found RAPL domain package
[    4.347137] intel_rapl: Found RAPL domain core
[    4.347138] intel_rapl: Found RAPL domain uncore
[    4.347139] intel_rapl: Found RAPL domain dram
[    4.348970] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.461648] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.508087] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input8
[    4.508154] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input9
[    4.508216] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[    4.508277] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
model		: 142
model name	: Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz
model		: 142
model name	: Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz
model		: 142
model name	: Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz
model		: 142
model name	: Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.125] (**) |   |-->Device "Intel Graphics"
[     5.125] (==) Automatically adding GPU devices
[     5.125] (==) Automatically binding GPU devices
[     5.125] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.125] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.125] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.125] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.125] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.142] (II) LoadModule: "glx"
[     5.143] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.148] (II) Module glx: vendor="X.Org Foundation"
[     5.148] (II) LoadModule: "intel"
[     5.148] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.150] (II) Module intel: vendor="X.Org Foundation"
[     5.150] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[     5.150] (II) intel: Driver for Intel(R) HD Graphics
[     5.150] (II) intel: Driver for Intel(R) Iris(TM) Graphics
[     5.150] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics
[     5.151] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20161121
[     5.151] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20170309-0ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[     5.151] (II) intel(0): SNA compiled for use with valgrind
[     5.152] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 620
[     5.152] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[     5.152] (II) intel(0): Creating default Display subsection in Screen section
[     5.152] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.152] (==) intel(0): RGB weight 888
[     5.152] (==) intel(0): Default visual is TrueColor
[     5.152] (**) intel(0): Option "AccelMethod" "sna"
[     5.152] (**) intel(0): Option "DRI" "3"
[     5.152] (**) intel(0): Option "TearFree" "true"
[     5.152] (II) intel(0): Output DP1 has no monitor section
[     5.153] (II) intel(0): Enabled output DP1
[     5.153] (II) intel(0): Output HDMI1 has no monitor section
[     5.153] (II) intel(0): Enabled output HDMI1
[     5.153] (II) intel(0): Output DP2 has no monitor section
[     5.153] (II) intel(0): Enabled output DP2
[     5.153] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     5.153] (II) intel(0): Output VIRTUAL1 has no monitor section
[     5.153] (II) intel(0): Enabled output VIRTUAL1
[     5.153] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 0
[     5.153] (**) intel(0): TearFree enabled
[     5.153] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.153] (==) intel(0): DPI set to (96, 96)
[     5.155] (II) intel(0): SNA initialized with Kabylake (gen9) backend
[     5.155] (==) intel(0): Backing store enabled
[     5.155] (==) intel(0): Silken mouse enabled
[     5.155] (II) intel(0): HW Cursor enabled
[     5.156] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.156] (==) intel(0): DPMS enabled
[     5.156] (==) intel(0): Display hotplug detection enabled
[     5.156] (II) intel(0): [DRI2] Setup complete
[     5.156] (II) intel(0): [DRI2]   DRI driver: i965
[     5.156] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[     5.156] (II) intel(0): direct rendering: DRI2 DRI3 enabled
[     5.156] (II) intel(0): hardware support for Present enabled
[     5.175] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.175] (II) AIGLX: enabled GLX_ARB_create_context
[     5.175] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     5.175] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[     5.175] (II) AIGLX: enabled GLX_INTEL_swap_event
[     5.175] (II) AIGLX: enabled GLX_SGI_swap_control
[     5.175] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     5.175] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     5.175] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[     5.175] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     5.175] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     5.175] (II) AIGLX: Loaded and initialized i965
[     5.175] (II) GLX: Initialized DRI2 GL provider for screen 0
[     5.178] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[     5.192] (II) intel(0): Setting screen physical size to 508 x 285
[     5.412] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event10)
[     5.412] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event11)
[     5.413] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[     5.414] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[     6.713] (--) intel(0): HDMI max TMDS frequency 300000KHz
[     6.786] (--) intel(0): HDMI max TMDS frequency 300000KHz
[     6.836] (--) intel(0): HDMI max TMDS frequency 300000KHz
[     7.140] (--) intel(0): HDMI max TMDS frequency 300000KHz
[    14.855] (--) intel(0): HDMI max TMDS frequency 300000KHz
[   648.529] (--) intel(0): HDMI max TMDS frequency 300000KHz
[   683.421] (--) intel(0): HDMI max TMDS frequency 300000KHz
[   684.105] (--) intel(0): HDMI max TMDS frequency 300000KHz
	Release Date: 02/20/2017
		Serial services are supported (int 14h)
	Manufacturer: GIGABYTE
	Product Name: GB-BKi3(H)A-7100
	Serial Number: Default string
	Manufacturer: GIGABYTE
	Product Name: MFLP3AP-00
	Serial Number: Default string
	Manufacturer: Default string
	Serial Number: Default string
	Port Type: Serial Port 16550A Compatible
	Manufacturer: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Manufacturer: Kingston
	Serial Number: C10400A9
	Manufacturer: Kingston
	Serial Number: BE0400AB
	Manufacturer: Intel(R) Corporation
	Serial Number: To Be Filled By O.E.M.
		Debug Use USB(Disabled:Serial)
cat: /etc/X11/xorg.conf: No such file or directory
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 620 (Kabylake GT2) 
OpenGL version string:  3.0 Mesa 17.0.3

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
Support status summary of 'mediaman':

You have 2089 packages (92.6%) supported until January 2018 (9m)

You have 0 packages (0.0%) that can not/no longer be downloaded
You have 166 packages (7.4%) that are unsupported


Run with --show-unsupported, --show-supported or --show-all to see more details
Module                  Size  Used by
ccm                    20480  1
rfcomm                 77824  2
cmac                   16384  1
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    90112  1
binfmt_misc            20480  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
nls_iso8859_1          16384  1
snd_soc_skl            65536  0
snd_soc_skl_ipc        49152  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          36864  3
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm_intel             200704  0
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
kvm                   593920  1 kvm_intel
arc4                   16384  2
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
iwlmvm                368640  0
ghash_clmulni_intel    16384  0
mac80211              782336  1 iwlmvm
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
pcbc                   16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
iwlwifi               229376  1 iwlmvm
aesni_intel           167936  4
snd                    77824  19 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
input_leds             16384  0
joydev                 20480  0
aes_x86_64             20480  1 aesni_intel
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
btusb                  45056  0
btrtl                  16384  1 btusb
mei_me                 40960  0
soundcore              16384  1 snd
shpchp                 36864  0
mei                   102400  1 mei_me
intel_pch_thermal      16384  0
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
bluetooth             557056  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_pad              180224  0
acpi_als               16384  0
mac_hid                16384  0
kfifo_buf              16384  1 acpi_als
industrialio           69632  2 acpi_als,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
i915                 1449984  116
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
e1000e                249856  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  7 i915,drm_kms_helper
ptp                    20480  1 e1000e
ahci                   36864  2
pps_core               20480  1 ptp
libahci                32768  1 ahci
video                  40960  1 i915
i2c_hid                20480  0
pinctrl_sunrisepoint    28672  0
hid                   114688  3 i2c_hid,hid_generic,usbhid
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   73728  0
```

---

### Post by Autodave on 2017-04-30
Whew.....my eyes are tired. :-) It appears as though you have an Nvidia video card installed, but no driver for it. Right? If so, let's get a driver in there and see what happens.  Go to *Settings -> **Software & Updates -> Additional drivers *and let that search for the best option. Choose what it recommends and install it. Reboot (and don't be afraid if you get some kinda weird screen either shutting down or logging back in). Report back!

---

### Post by ianberg on 2017-04-30
Yeah! sorry about that. I wasn't sure what to cut out!

In that dialog it says
```
 Unknown: Unknown
Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary).

```
I disable it and rebooted and retried but it's the same. I've re-enabled it now.

---

### Post by ianberg on 2017-04-30
By the way this NUC has onboards graphics. Intel® HD Graphics 620. No sight of nvidia AFAIK.

---

### Post by Yellow Pasque on 2017-04-30
So what player are you trying to use and what video output do you have it configured for?

Look at vainfo and vdpauinfo to check video decode accel support:
```
sudo apt-get install vdpauinfo vainfo
vainfo
vdpauinfo
```

---

### Post by ianberg on 2017-05-01
I've tried mpv media player, VLC, Gnome Mplayer,... they all yield similar results. I think VLC is the only one that allows to configure output and its set to automatic.  

When I choose vdpau output in VLC it's just a black screen. I have checked that it is installed though.

```
display: :0   screen: 0
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
Error creating VDPAU device: 1
```

```
libva info: VA-API version 0.39.4
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.39 (libva 1.7.3)
vainfo: Driver version: Intel i965 driver for Intel(R) Kabylake - 1.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileH264MultiviewHigh      :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileH264StereoHigh         :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD
      VAProfileJPEGBaseline           :	VAEntrypointEncPicture
      VAProfileVP8Version0_3          :	VAEntrypointVLD
      VAProfileVP8Version0_3          :	VAEntrypointEncSlice
      VAProfileHEVCMain               :	VAEntrypointVLD
      VAProfileHEVCMain               :	VAEntrypointEncSlice
      VAProfileHEVCMain10             :	VAEntrypointVLD
      VAProfileHEVCMain10             :	VAEntrypointEncSlice
      VAProfileVP9Profile0            :	VAEntrypointVLD
      VAProfileVP9Profile0            :	VAEntrypointEncSlice
      VAProfileVP9Profile2            :	VAEntrypointVLD
```

---

### Post by ianberg on 2017-05-01
I should probably add I'm not great at this stuff; I am trying but there's a lot to take in.

I can provide details from mediainfo about the files I'm having trouble with but I don't want to spam the thread with loads of useless info though - What would be needed?

---

### Post by Yellow Pasque on 2017-05-01
> Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory

Maybe you could try to install libvdpau-va-gl1 package, and use VDPAU output in mplayer/mpv to see how that performs.

---

### Post by ianberg on 2017-05-02
I ran through all the output options in VLC and found that for OpenGL GLX XCB seemed to stop the problem with the jutter/tearing/halting on 1080p videos. For 4k everything remained the same though.

4k video.

DirectFB - no video output
GNU/Linux framebuffer video output -  no video output
ASCII &#8211; I can see ASCII but performance is really bad, I think
OpenGL video output (experimental) &#8211; same lagginess but now with extra artifacts on screen.
OpenGL for embedded systems. - Pixellation reminds me of impressionism. Screen cuts in half occasionally.
YUV video output &#8211; no output
OpenGLX video output &#8211; Same.
X11 video output &#8211; same lagginess.

1080 video.
I notice when playing a frametest video that when video shows it seems to almost skip back a frame, or halt.
OpenGL GLX XCB seems to give noticeablly smoother performance.

---

### Post by ianberg on 2017-05-02
I installed the package you mentioned and now when selecting that as the output in VLC I get really weird performance playing 1080p videos. It shows the opening splash screen on the video and it loops several times and seems to overlay the rest of the video as it starts and things get garbled. It's not blank any more though.

4k doesn't run using this as the output.

---

### Post by ianberg on 2017-05-04
Thanks for your help so far. Since installing the recommended package I can now view the videos in mpv, kind of. They no longer judder, but are 5-10 frames a second, still noticeably jerky. MPlayer and VLC won't play the videos (vlc is set to VDPAU).

vdpauinfo gives output suggesting that my hardware doesn't support anything, but is that because it is supported through va-api?

```
$ vainfo
libva info: VA-API version 0.39.4
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.39 (libva 1.7.3)
vainfo: Driver version: Intel i965 driver for Intel(R) Kabylake - 1.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileH264MultiviewHigh      :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileH264StereoHigh         :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD
      VAProfileJPEGBaseline           :	VAEntrypointEncPicture
      VAProfileVP8Version0_3          :	VAEntrypointVLD
      VAProfileVP8Version0_3          :	VAEntrypointEncSlice
      VAProfileHEVCMain               :	VAEntrypointVLD
      VAProfileHEVCMain               :	VAEntrypointEncSlice
      VAProfileHEVCMain10             :	VAEntrypointVLD
      VAProfileHEVCMain10             :	VAEntrypointEncSlice
      VAProfileVP9Profile0            :	VAEntrypointVLD
      VAProfileVP9Profile0            :	VAEntrypointEncSlice
      VAProfileVP9Profile2            :	VAEntrypointVLD
```
```
$ vdpauinfo

display: :0   screen: 0
libva info: VA-API version 0.39.4
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
API version: 1
Information string: OpenGL/VAAPI backend for VDPAU

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 
422     4096  4096  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 
444     4096  4096  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                          --- not supported ---
MPEG2_SIMPLE                   --- not supported ---
MPEG2_MAIN                     --- not supported ---
H264_BASELINE                  51 16384  2048  2048
H264_MAIN                      51 16384  2048  2048
H264_HIGH                      51 16384  2048  2048
VC1_SIMPLE                     --- not supported ---
VC1_MAIN                       --- not supported ---
VC1_ADVANCED                   --- not supported ---
MPEG4_PART2_SP                 --- not supported ---
MPEG4_PART2_ASP                --- not supported ---
DIVX4_QMOBILE                  --- not supported ---
DIVX4_MOBILE                   --- not supported ---
DIVX4_HOME_THEATER             --- not supported ---
DIVX4_HD_1080P                 --- not supported ---
DIVX5_QMOBILE                  --- not supported ---
DIVX5_MOBILE                   --- not supported ---
DIVX5_HOME_THEATER             --- not supported ---
DIVX5_HD_1080P                 --- not supported ---
H264_CONSTRAINED_BASELINE      51 16384  2048  2048
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  
R8G8B8A8         16384 16384    y  
R10G10B10A2      16384 16384    y  
B10G10R10A2      16384 16384    y  
A8               16384 16384    y  

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             -
DEINTERLACE_TEMPORAL_SPATIAL     -
INVERSE_TELECINE                 -
NOISE_REDUCTION                  -
SHARPNESS                        -
LUMA_KEY                         -
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              -  
VIDEO_SURFACE_HEIGHT             -  
CHROMA_TYPE                      -  
LAYERS                           -  

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 -  
CSC_MATRIX                       -  
NOISE_REDUCTION_LEVEL            -  
SHARPNESS_LEVEL                  -  
LUMA_KEY_MIN_LUMA                -  
LUMA_KEY_MAX_LUMA                -  


```

Xorg.log shows that the correct drivers are in use... I think.

```
 grep -iE 'vdpau|dri driver' /var/log/Xorg.0.log
[     4.674] (II) intel(0): [DRI2]   DRI driver: i965
[     4.674] (II) intel(0): [DRI2]   VDPAU driver: va_gl

```

I played a file in mplayer with --untimed to get the stats

```
mplayer --untimed '/home/mediaman/Downloads/sample-Elysium.2013.2160p.mkv' 
Playing: /home/mediaman/Downloads/sample-Elysium.2013.2160p.mkv
 (+) Video --vid=1 (*) 'Elysium (2013) - Release for ULTRAHDCLUB' (hevc)
 (+) Audio --aid=1 --alang=eng (*) 'DTS-HD MA 7.1 - Blu-ray CEE' (dts)
File tags:
 Title: Elysium (2013)
[ffmpeg/video] hevc: Invalid default display window
AO: [pulse] 48000Hz 7.1 8ch s16
VO: [opengl] 3840x1606 yuv420p10
AV: 00:00:01 / 00:01:02 (2%) A-V:  0.441
[COLOR="#DAA520"]
Audio/Video desynchronisation detected! Possible reasons include too slow
hardware, temporary CPU spikes, broken drivers, and broken files. Audio
position will not match to the video (see A-V status field).[/COLOR]

AV: 00:00:16 / 00:01:02 (26%) A-V:  5.913


Exiting... (Quit)

```

I really don't think that the video is beyond the capabilities of the hardware. A NUC reviewer reviewing a different NUC (but with practically identical hardware) said it played AOK. Still looking for pointers, as it's still unwatchable :)

---

### Post by Yellow Pasque on 2017-05-04
Yeah, it looks like libvdpau_va_gl only supports h264. Really, you shouldn't have to use that anyway, unless you're dealing with a program that only supports VDPAU.

Something's definitely wrong if you can't play 1080p smoothly using VA-API directly.

---

### Post by ianberg on 2017-05-05
Sorry if I didn't make it clear, but 1080p now works OK. I only have problems with 4k. Now certain 4k files seem to play OK, but I assume they're getting decoded in software, which is why some are too intensive to play.

The only format I seem to have problems with now are a 4k 10 bit HEVC file (which should still present no problems)

Apparently hardware decoding needs to be enabled in mpv and is not enabled by default.

If I run this:
```
mpv --hwdec=vaapi-copy filepath
```

(vaapi doesn't give as smooth performance as vaapi-copy. vdpau just produces an awful mess on screen)

then output is smooth as hell,... apart from one test video. This includes x265, x264, and 4k up to 25fps.

The one problem format is this 10bit HEVC file at 60fps. Note that when I run it in mpv with --hwdec=vaapi-copy then it's much smoother, but still not as smooth as I'd like. It's definitely not 60fps. Output below.

```

mediaman@mediaman:~/Downloads$ mpv --hwdec=vaapi-copy '4K HEVC 59.940 Broadcast Capture Sample.mkv' 
Playing: 4K HEVC 59.940 Broadcast Capture Sample.mkv
 (+) Video --vid=1 (*) (hevc)
 (+) Audio --aid=1 --alang=kor (*) (aac)
libva info: VA-API version 0.39.4
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
libva info: VA-API version 0.39.4
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
AO: [pulse] 48000Hz stereo 2ch float
Using hardware decoding (vaapi-copy).
VO: [opengl] 3840x2160 nv12
(Paused) AV: 00:00:04 / 00:01:00 (7%) A-V:  0.009 Dropped: 144


Exiting... (Quit)

```

```
Video
ID                                       : 1
Format                                   : HEVC
Format/Info                              : High Efficiency Video Coding
Format profile                           : Main 10@L5.1@Main
Codec ID                                 : V_MPEGH/ISO/HEVC
Duration                                 : 1 min 0 s
Bit rate                                 : 25.0 Mb/s
Width                                    : 3 840 pixels
Height                                   : 2 160 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 59.940 (60000/1001) FPS
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 10 bits
Bits/(Pixel*Frame)                       : 0.050
Stream size                              : 179 MiB (98%)
Default                                  : Yes
Forced                                   : No

```

I've also literally just noticed that in VLC under codecs you can choose your method of hardware acceleration. It was set to auto. There's also dummy, vdpau, vaapi via X11 and vaapi via DRM. vdpau plays one frame then the screen turns grey. Both vaapi options play one frame and freeze.

---

### Post by Yellow Pasque on 2017-05-05
> **ianberg said:**
> Now certain 4k files seem to play OK, but I assume they're getting decoded in software, which is why some are too intensive to play.

I don't see any reason to make that assumption based on the mpv output, which states hardware decoding.

> vaapi doesn't give as smooth performance as vaapi-copy

Hmm. It should be the other way around. Maybe a verbose log would give you a clue (or maybe not).

```
mpv --hwdec=vaapi --log-file=mpvlog.txt 'videoname'
```

---

### Post by ianberg on 2017-05-06
[http://paste.ubuntu.com/24524143/](http://paste.ubuntu.com/24524143/)
[http://paste.ubuntu.com/24524147/](http://paste.ubuntu.com/24524147/)

Main one below, some extras above.

```
[   0.003][v][cplayer] Command line options: '--hwdec=vaapi' '--log-file=mpvlog.txt' '/home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv'
[   0.003][v][cplayer] mpv 0.24.0 (C) 2000-2017 mpv/MPlayer/mplayer2 projects
[   0.003][v][cplayer]  built on UNKNOWN
[   0.003][v][cplayer] ffmpeg library versions:
[   0.003][v][cplayer]    libavutil       55.34.101
[   0.003][v][cplayer]    libavcodec      57.64.101
[   0.003][v][cplayer]    libavformat     57.56.101
[   0.003][v][cplayer]    libswscale      4.2.100
[   0.003][v][cplayer]    libavfilter     6.65.100
[   0.003][v][cplayer]    libswresample   2.3.100
[   0.003][v][cplayer] ffmpeg version: 3.2.4-1build2
[   0.003][v][cplayer] 
[   0.003][v][cplayer] Configuration: ./waf configure --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --confdir=/etc/mpv --zshdir=/usr/share/zsh/vendor-completions --enable-cdda --enable-sdl2 --enable-sndio --enable-zsh-comp --enable-libmpv-shared --enable-encoding --disable-build-date
[   0.003][v][cplayer] List of enabled features: alsa any-gl asm atomics audio-input c11-tls cdda cplayer debug-build dlopen drm dvbin dvdnav dvdread egl-drm egl-helpers egl-x11 encoding fchmod gbm gbm.h gcc-tls gl gl-wayland gl-x11 glibc-thread-name glob gnuc iconv is_ffmpeg jack jpeg lcms2 libass libass-osd libav libavcodec libavdevice libbluray libdl libm libmpv-shared librt libsmbclient libv4l2 linux-fstatfs lua nanosleep optimize oss-audio oss-audio-native plain-gl posix posix-or-mingw posix-spawn pthreads pulse rubberband sdl2 shm sndio sse4-intrinsics standard-gl stdatomic subprocess termios tv tv-v4l2 uchardet vaapi vaapi-drm vaapi-egl vaapi-glx vaapi-hwaccel vaapi-hwaccel-old vaapi-wayland vaapi-x-egl vaapi-x11 vdpau vdpau-gl-x11 vdpau-hwaccel videodev vt.h wayland x11 xext xinerama xrandr xss xv zlib zsh-comp
[   0.003][v][cplayer] Setting option 'hwdec' = 'vaapi' (flags = 8)
[   0.003][v][cplayer] Setting option 'log-file' = 'mpvlog.txt' (flags = 8)
[   0.004][v][global] user path: 'mpvlog.txt' -> 'mpvlog.txt'
[   0.004][v][osc] Loading lua script @osc.lua...
[   0.005][v][global] config path: 'scripts' -/-> '/home/mediaman/.config/mpv/scripts'
[   0.005][v][global] config path: 'scripts' -/-> '/home/mediaman/.mpv/scripts'
[   0.005][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.005][v][osc] loading mp.defaults
[   0.005][v][osc] loading @osc.lua
[   0.008][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/mediaman/.config/mpv/lua-settings/osc.conf'
[   0.008][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/mediaman/.mpv/lua-settings/osc.conf'
[   0.008][v][global] config path: 'lua-settings/osc.conf' -/-> '/etc/mpv/lua-settings/osc.conf'
[   0.008][v][osc] lua-settings/osc.conf not found. 
[   0.009][v][cplayer] Run command: define-section, flags=0, args=[showhide, mouse_move script-binding osc/__keybinding1
[   0.009][v][cplayer] mouse_leave script-binding osc/__keybinding2
[   0.009][v][cplayer] , force]
[   0.009][v][cplayer] Run command: enable-section, flags=0, args=[showhide, allow-hide-cursor+allow-vo-dragging]
[   0.009][v][cplayer] Run command: define-section, flags=0, args=[input, mouse_btn0 script-binding osc/__keybinding3
[   0.009][v][cplayer] shift+mouse_btn0 script-binding osc/__keybinding4
[   0.009][v][cplayer] mouse_btn2 script-binding osc/__keybinding5
[   0.009][v][cplayer] mouse_btn0_dbl ignore
[   0.009][v][cplayer] shift+mouse_btn0_dbl ignore
[   0.009][v][cplayer] mouse_btn2_dbl ignore
[   0.009][v][cplayer] , force]
[   0.009][v][cplayer] Run command: enable-section, flags=0, args=[input, ]
[   0.009][v][cplayer] Run command: define-section, flags=0, args=[input_osc, del script-binding osc/__keybinding6
[   0.009][v][cplayer] , default]
[   0.009][v][cplayer] Run command: enable-section, flags=0, args=[input_osc, allow-hide-cursor+allow-vo-dragging]
[   0.009][v][cplayer] Run command: define-section, flags=0, args=[input_forced_osc, , force]
[   0.009][v][cplayer] Run command: enable-section, flags=0, args=[input_forced_osc, allow-hide-cursor+allow-vo-dragging]
[   0.009][v][cplayer] Done loading @osc.lua.
[   0.009][v][ytdl_hook] Loading lua script @ytdl_hook.lua...
[   0.009][v][global] config path: 'scripts' -/-> '/home/mediaman/.config/mpv/scripts'
[   0.009][v][global] config path: 'scripts' -/-> '/home/mediaman/.mpv/scripts'
[   0.009][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.009][v][ytdl_hook] loading mp.defaults
[   0.010][v][cplayer] Run command: disable-section, flags=0, args=[input]
[   0.010][v][global] config path: 'fonts' -/-> '/home/mediaman/.config/mpv/fonts'
[   0.010][v][global] config path: 'fonts' -/-> '/home/mediaman/.mpv/fonts'
[   0.010][v][global] config path: 'fonts' -/-> '/etc/mpv/fonts'
[   0.010][v][osd/libass] Shaper: FriBidi 0.19.7 (SIMPLE) HarfBuzz-ng 1.4.2 (COMPLEX)
[   0.010][v][global] config path: 'subfont.ttf' -/-> '/home/mediaman/.config/mpv/subfont.ttf'
[   0.010][v][global] config path: 'subfont.ttf' -/-> '/home/mediaman/.mpv/subfont.ttf'
[   0.010][v][global] config path: 'subfont.ttf' -/-> '/etc/mpv/subfont.ttf'
[   0.010][v][global] config path: 'fonts.conf' -/-> '/home/mediaman/.config/mpv/fonts.conf'
[   0.010][v][global] config path: 'fonts.conf' -/-> '/home/mediaman/.mpv/fonts.conf'
[   0.010][v][global] config path: 'fonts.conf' -/-> '/etc/mpv/fonts.conf'
[   0.010][v][osd/libass] Setting up fonts...
[   0.010][v][ytdl_hook] loading @ytdl_hook.lua
[   0.011][v][cplayer] Run command: hook-add, flags=0, args=[on_load, 1, 10]
[   0.011][v][cplayer] Run command: hook-add, flags=0, args=[on_preloaded, 2, 10]
[   0.011][v][cplayer] Done loading @ytdl_hook.lua.
[   0.011][v][global] config path: 'scripts' -/-> '/home/mediaman/.config/mpv/scripts'
[   0.012][v][global] config path: 'scripts' -/-> '/home/mediaman/.mpv/scripts'
[   0.012][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.012][v][global] config path: 'watch_later' -> '/home/mediaman/.config/mpv/watch_later'
[   0.012][i][cplayer] Playing: /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.012][v][cplayer] Running hook: ytdl_hook/on_load
[   0.023][v][osd/libass] Using font provider fontconfig
[   0.023][v][osd/libass] Done.
[   0.024][v][cplayer] Run command: hook-ack, flags=0, args=[on_load]
[   0.024][v][ifo] Opening /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.025][v][ifo_dvdnav] Opening /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.025][v][bdmv/bluray] Opening /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.025][v][file] Opening /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.025][v][file] Stream opened successfully.
[   0.025][v][demux] Trying demuxers for level=normal.
[   0.027][v][mkv] Found the head...
[   0.027][v][mkv] + a segment...
[   0.027][v][mkv] Parsing seek head...
[   0.027][v][mkv] |+ segment information...
[   0.027][v][mkv] | + muxing app: libebml v1.3.4 + libmatroska v1.4.5
[   0.027][v][mkv] | + writing app: mkvmerge v9.3.1 ('Mask Machine') 64bit
[   0.027][v][mkv] | + timecode scale: 1000000
[   0.027][v][mkv] | + duration: 60.070s
[   0.027][v][mkv] | + segment uid 99 f0 b3 f3 6a 7a 33 72 8c 4f 95 9f 8a 5b 5b 53
[   0.027][v][mkv] |+ segment tracks...
[   0.027][v][mkv] | + a track...
[   0.027][v][mkv] |  + Track number: 1
[   0.027][v][mkv] |  + Track type: Video
[   0.027][v][mkv] |  + Video track
[   0.027][v][mkv] |   + Display width: 3840
[   0.027][v][mkv] |   + Display height: 2160
[   0.027][v][mkv] |   + Pixel width: 3840
[   0.027][v][mkv] |   + Pixel height: 2160
[   0.027][v][mkv] |  + Codec ID: V_MPEGH/ISO/HEVC
[   0.027][v][mkv] |  + CodecPrivate, length 133
[   0.027][v][mkv] |  + Language: und
[   0.027][v][mkv] |  + Default duration: 16.683ms ( = 59.940 fps)
[   0.027][v][mkv] | + a track...
[   0.027][v][mkv] |  + Track number: 2
[   0.027][v][mkv] |  + Track type: Audio
[   0.027][v][mkv] |  + Audio track
[   0.027][v][mkv] |   + Sampling frequency: 48000.000000
[   0.027][v][mkv] |   + Channels: 2
[   0.027][v][mkv] |  + Codec ID: A_AAC
[   0.027][v][mkv] |  + CodecPrivate, length 2
[   0.027][v][mkv] |  + Language: kor
[   0.027][v][mkv] |  + Default duration: 21.333ms ( = 46.875 fps)
[   0.027][v][mkv] |+ found cluster
[   0.027][v][mkv] Deferring reading cues.
[   0.027][v][mkv] Seeking to 190333877 to read header element 0x1254c367.
[   0.027][v][mkv] All headers are parsed!
[   0.027][v][demux] Detected file format: Matroska
[   0.027][v][cplayer] Opening done: /home/mediaman/Downloads/4K HEVC 59.940 Broadcast Capture Sample.mkv
[   0.028][v][find_files] Loading external files in /home/mediaman/Downloads/
[   0.028][v][global] config path: 'sub/' -/-> '/home/mediaman/.config/mpv/sub/'
[   0.028][v][global] config path: 'sub/' -/-> '/home/mediaman/.mpv/sub/'
[   0.028][v][global] config path: 'sub/' -/-> '/etc/mpv/sub/'
[   0.028][v][global] config path: 'audio/' -/-> '/home/mediaman/.config/mpv/audio/'
[   0.028][v][global] config path: 'audio/' -/-> '/home/mediaman/.mpv/audio/'
[   0.028][v][global] config path: 'audio/' -/-> '/etc/mpv/audio/'
[   0.028][v][cplayer] Running hook: ytdl_hook/on_preloaded
[   0.028][v][cplayer] Run command: hook-ack, flags=0, args=[on_preloaded]
[   0.028][i][cplayer]  (+) Video --vid=1 (*) (hevc)
[   0.028][i][cplayer]  (+) Audio --aid=1 --alang=kor (*) (aac)
[   0.028][v][vo/opengl] Initializing OpenGL backend 'wayland'
[   0.028][v][vo/opengl/wayland] failed to connect to a wayland server: check if a wayland compositor is running
[   0.028][v][vo/opengl] Initializing OpenGL backend 'x11probe'
[   0.028][v][vo/opengl/x11] X11 opening display: :0
[   0.031][v][vo/opengl/x11] X11 running at 3840x2160 (":0" => local display)
[   0.031][v][vo/opengl/x11] Detected wm supports NetWM.
[   0.031][v][vo/opengl/x11] Detected wm supports FULLSCREEN state.
[   0.031][v][vo/opengl/x11] Detected wm supports ABOVE state.
[   0.031][v][vo/opengl/x11] Detected wm supports BELOW state.
[   0.031][v][vo/opengl/x11] Display 0 (DP2): [0, 0, 3840, 2160] @ 60.000000 FPS
[   0.031][v][vo/opengl/x11] Current display FPS: 60.000000
[   0.040][v][vo/opengl] GLX chose FB config with ID 0x98
[   0.040][v][vo/opengl] GLX chose visual with ID 0xd1
[   0.041][v][vo/opengl] Creating OpenGL 3.3 context...
[   0.042][v][vo/opengl] GL_VERSION='4.5 (Core Profile) Mesa 17.0.3'
[   0.042][v][vo/opengl] Detected desktop OpenGL 4.5.
[   0.042][v][vo/opengl] GL_VENDOR='Intel Open Source Technology Center'
[   0.042][v][vo/opengl] GL_RENDERER='Mesa DRI Intel(R) HD Graphics 620 (Kabylake GT2) '
[   0.042][v][vo/opengl] GL_SHADING_LANGUAGE_VERSION='4.50'
[   0.043][v][vo/opengl] Loaded extension GLX_SGI_swap_control.
[   0.043][v][vo/opengl] Loaded extension GLX_SGI_video_sync.
[   0.043][v][vo/opengl] No vdpau support found - probing more things.
[   0.043][v][vo/opengl/x11] uninit ...
[   0.044][v][vo/opengl] Initializing OpenGL backend 'x11egl'
[   0.044][v][vo/opengl/x11] X11 opening display: :0
[   0.045][v][vo/opengl/x11] X11 running at 3840x2160 (":0" => local display)
[   0.045][v][vo/opengl/x11] Detected wm supports NetWM.
[   0.046][v][vo/opengl/x11] Detected wm supports FULLSCREEN state.
[   0.046][v][vo/opengl/x11] Detected wm supports ABOVE state.
[   0.046][v][vo/opengl/x11] Detected wm supports BELOW state.
[   0.046][v][vo/opengl/x11] Display 0 (DP2): [0, 0, 3840, 2160] @ 60.000000 FPS
[   0.046][v][vo/opengl/x11] Current display FPS: 60.000000
[   0.051][v][vo/opengl] EGL_VERSION=1.4 (DRI2)
[   0.051][v][vo/opengl] EGL_VENDOR=Mesa Project
[   0.051][v][vo/opengl] EGL_CLIENT_APIS=OpenGL OpenGL_ES 
[   0.051][v][vo/opengl] Trying to create Desktop OpenGL context.
[   0.051][v][vo/opengl] chose visual 0x20
[   0.052][v][vo/opengl] GL_VERSION='4.5 (Core Profile) Mesa 17.0.3'
[   0.052][v][vo/opengl] Detected desktop OpenGL 4.5.
[   0.052][v][vo/opengl] GL_VENDOR='Intel Open Source Technology Center'
[   0.052][v][vo/opengl] GL_RENDERER='Mesa DRI Intel(R) HD Graphics 620 (Kabylake GT2) '
[   0.052][v][vo/opengl] GL_SHADING_LANGUAGE_VERSION='4.50'
[   0.052][v][vo/opengl] swap_control extension missing.
[   0.054][v][vo/opengl] 16 bit texture depth: 16.
[   0.054][v][vo/opengl] Reported display depth: R=8, G=8, B=8
[   0.054][v][vo/opengl] Testing FBO format 0x805b
[   0.054][v][vo/opengl] Create FBO: 16x16 (16x16)
[   0.054][v][vo/opengl] Using FBO format 0x805b.
[   0.054][v][vo/opengl] No advanced processing required. Enabling dumb mode.
[   0.054][v][vo/opengl] Loading hwdec driver 'vaapi-egl'
[   0.054][v][vo/opengl/vaapi-egl] Trying to open a x11 VA display...
[   0.056][v][vo/opengl/vaapi-egl/vaapi] VA API version 0.39
[   0.056][v][vo/opengl/vaapi-egl/vaapi] 9 image formats available:
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   YV12
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   I420
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   NV12
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   YUY2
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   UYVY
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   422H
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   RGBX
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   BGRX
[   0.056][v][vo/opengl/vaapi-egl/vaapi]   P010
[   0.056][v][vo/opengl/vaapi-egl] using VAAPI EGL interop
[   0.056][v][vo/opengl/vaapi-egl] Supported formats:
[   0.056][v][vo/opengl/vaapi-egl]  nv12
[   0.056][v][vo/opengl] Assuming 60.000000 FPS for display sync.
[   0.056][v][vd] Container reported FPS: 59.940060
[   0.056][v][vd] Codec list:
[   0.056][v][vd]     hevc - HEVC (High Efficiency Video Coding)
[   0.056][v][vd] Opening video decoder hevc
[   0.056][v][vd] Probing 'vaapi'...
[   0.056][v][vd] Trying hardware decoding.
[   0.056][v][vd] Selected video codec: hevc (HEVC (High Efficiency Video Coding))
[   0.057][v][ad] Codec list:
[   0.057][v][ad]     aac - AAC (Advanced Audio Coding)
[   0.057][v][ad]     aac_fixed (aac) - AAC (Advanced Audio Coding)
[   0.057][v][ad] Opening audio decoder aac
[   0.057][v][ad] Requesting 1 threads for decoding.
[   0.058][v][ad] Selected audio codec: aac (AAC (Advanced Audio Coding))
[   0.058][v][cplayer] Starting playback...
[   0.058][v][vo/opengl/x11] Disabling screensaver.
[   0.060][v][vd] Pixel formats supported by decoder: vaapi_vld yuv420p10le
[   0.060][v][vd] Codec profile: Main 10 (0x2)
[   0.060][v][vaapi] Using profile 'VAProfileHEVCMain10'.
[   0.070][v][af] Audio filter chain:
[   0.070][v][af]   [in] 48000Hz stereo 2ch floatp
[   0.070][v][af]   [out] 48000Hz stereo 2ch floatp
[   0.070][v][af]   [ao] 48000Hz stereo 2ch floatp
[   0.070][v][ao] Trying audio driver 'pulse'
[   0.070][v][ao/pulse] requested format: 48000 Hz, stereo channels, floatp
[   0.072][v][ao/pulse] Library version: 10.0.0
[   0.072][v][ao/pulse] Proto: 32
[   0.072][v][ao/pulse] Server proto: 4294967295
[   0.074][v][ao/pulse] Channel layouts:
[   0.074][v][ao/pulse]  - #fl
[   0.074][v][ao/pulse]  - #fr
[   0.074][v][ao/pulse]  - #fc
[   0.074][v][ao/pulse]  - #lfe
[   0.074][v][ao/pulse]  - #bl
[   0.074][v][ao/pulse]  - #br
[   0.074][v][ao/pulse]  - #flc
[   0.074][v][ao/pulse]  - #frc
[   0.074][v][ao/pulse]  - #bc
[   0.074][v][ao/pulse]  - #sl
[   0.074][v][ao/pulse]  - #sr
[   0.074][v][ao/pulse]  - #tc
[   0.074][v][ao/pulse]  - #tfl
[   0.074][v][ao/pulse]  - #tfc
[   0.074][v][ao/pulse]  - #tfr
[   0.074][v][ao/pulse]  - #tbl
[   0.074][v][ao/pulse]  - #tbc
[   0.075][v][ao/pulse]  - #tbr
[   0.075][v][ao/pulse] result: stereo
[   0.093][v][ao/pulse] device buffer: 6000 samples.
[   0.093][v][ao/pulse] using soft-buffer of 9600 samples.
[   0.093][i][cplayer] AO: [pulse] 48000Hz stereo 2ch float
[   0.093][v][cplayer] AO: Description: PulseAudio audio output
[   0.094][v][af] Adding filter lavrresample 
[   0.094][v][af] Audio filter chain:
[   0.094][v][af]   [in] 48000Hz stereo 2ch floatp
[   0.094][v][af]   [lavrresample] 48000Hz stereo 2ch float [a]
[   0.094][v][af]   [out] 48000Hz stereo 2ch float
[   0.094][v][af]   [ao] 48000Hz stereo 2ch float
[   0.107][i][vd] Using hardware decoding (vaapi).
[   0.107][v][vd] Decoder format: 3840x2160 vaapi auto/auto/auto/limited CL=unknown
[   0.107][v][vd] Using container aspect ratio.
[   0.107][v][vf] Video filter chain:
[   0.107][v][vf]   [in] 3840x2160 vaapi bt.709/bt.709/bt.1886/limited CL=unknown
[   0.107][v][vf]   [out] 3840x2160 vaapi bt.709/bt.709/bt.1886/limited CL=unknown
[   0.107][i][cplayer] VO: [opengl] 3840x2160 vaapi
[   0.107][v][cplayer] VO: Description: Extended OpenGL Renderer
[   0.121][v][vo/opengl] Resize: 3775x2136
[   0.121][v][vo/opengl] Window size: 3775x2136
[   0.121][v][vo/opengl] Video source: 3840x2160 (1:1)
[   0.121][v][vo/opengl] Video display: (0, 0) 3840x2160 -> (0, 6) 3775x2123
[   0.121][v][vo/opengl] Video scale: 0.983073/0.982870
[   0.121][v][vo/opengl] OSD borders: l=0 t=6 r=0 b=7
[   0.121][v][vo/opengl] Video borders: l=0 t=6 r=0 b=7
[   0.121][f][vo/opengl/vaapi-egl] unsupported VA image format unknown
[   0.121][e][vo/opengl] Initializing texture for hardware decoding failed.
[   0.122][v][vo/opengl] Testing FBO format 0x805b
[   0.122][v][vo/opengl] Create FBO: 16x16 (16x16)
[   0.122][v][vo/opengl] Using FBO format 0x805b.
[   0.122][v][vo/opengl] No advanced processing required. Enabling dumb mode.
[   0.122][v][cplayer] set video colors output-levels=0 
[   0.122][v][vo/opengl] recompiling a shader program:
[   0.122][v][vo/opengl] [  1] // color conversion
[   0.122][v][vo/opengl] [  2] color.rgb = mat3(colormatrix) * color.rgb + colormatrix_c;
[   0.122][v][vo/opengl] [  3] color.a = 1.0;
[   0.122][v][vo/opengl] [  4] // color mapping
[   0.128][v][osd/libass] fontselect: (sans-serif, 400, 0) -> /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf, 0, DejaVuSans
[   0.130][v][cplayer] first video frame after restart shown
[   0.133][v][cplayer] starting audio playback
[   0.133][v][cplayer] playback restart complete
[   1.022][v][cplayer] Run command: script-binding, flags=9, args=[osc/__keybinding2]
[   1.335][v][vo/opengl] Resize: 3775x2108
[   1.335][v][vo/opengl] Window size: 3775x2108
[   1.335][v][vo/opengl] Video source: 3840x2160 (1:1)
[   1.335][v][vo/opengl] Video display: (0, 0) 3840x2160 -> (14, 0) 3747x2108
[   1.335][v][vo/opengl] Video scale: 0.975781/0.975926
[   1.335][v][vo/opengl] OSD borders: l=14 t=0 r=14 b=0
[   1.335][v][vo/opengl] Video borders: l=14 t=0 r=14 b=0
[   6.191][v][cplayer] Run command: quit, flags=9, args=[0]
[   6.191][v][cplayer] EOF code: 6  
[   6.198][v][ad] Uninit audio decoder.
[   6.198][v][af] Removing filter lavrresample 
[   6.198][v][vd] Uninit video.
[   6.207][v][vo/opengl/x11] Enabling screensaver.
[   6.207][v][cplayer] finished playback, success (reason 3)
[   6.209][i][cplayer] 
[   6.209][i][cplayer] 
[   6.209][i][cplayer] Exiting... (Quit)
[   6.210][v][ytdl_hook] Exiting...
[   6.212][v][osc] Exiting...
[   6.217][v][ao/pulse] draining...
[   6.227][v][vo/opengl] flushing shader cache
[   6.228][v][vo/opengl/x11] uninit ...
```

---

### Post by Yellow Pasque on 2017-05-06
I don't see anything that raises a red flag, but I'm no expert in reading verbose mpv logs. I hope someone else has insight for you.

---

### Post by ianberg on 2017-05-06
Yes, I hope so too.  I was thinking of asking in the mpv forums. I'm not very experienced; is there anywhere else I should be asking?

Another thing I don't understand, but someone here may. On Intel a package provides VDPAU which is actually just frontend to VAAPI. Is the output of VDPAU accurate then, in that it doesn't support HEVC_MAIN_10? Could that be a driver issue? Who can I ask about that?

---

### Post by Yellow Pasque on 2017-05-06
> **ianberg said:**
> On Intel a package provides VDPAU which is actually just frontend to VAAPI. Is the output of VDPAU accurate then, in that it doesn't support HEVC_MAIN_10? Could that be a driver issue? Who can I ask about that?

When I was googling about this the other day, I saw that the libvdpau-va-gl backend only supported h264. Sorry, I don't have the link offhand. 
It's a moot point though, since libvdpau itself has issues with HEVC 10-bit: [https://github.com/mpv-player/mpv/commit/2048ad2b8af1becddb70cad2a7adc0361b779443](https://github.com/mpv-player/mpv/commit/2048ad2b8af1becddb70cad2a7adc0361b779443)

---

