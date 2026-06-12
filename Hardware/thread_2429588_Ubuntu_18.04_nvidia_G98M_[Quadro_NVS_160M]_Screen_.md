---
title: "Ubuntu 18.04 nvidia G98M [Quadro NVS 160M] Screen Flicker"
date: 2019-10-20
forum: Hardware
---

### Post by Redalien0304 on 2019-10-20
Have Ubuntu 18.04 (with HWE enablement stack)  with Cinnamon Desktop on Dell Latitude E6500 with G98M [Quadro NVS 160M] graphics card.
Have Screen Flicker with whatever i do is very annoying. Have tried to switching to X.org Nouvea open source driver, all i get on on reboot is Blank clack screen??

Thanks in Advance for any Help Please

---

### Post by Redalien0304 on 2019-10-21
Bump Anyone on Nvidia Screen Flicker??

---

### Post by Autodave on 2019-10-22
Does this laptop have dual GPUs?  When I looked this up yesterday, all that I found showed that it did not have an Nvidia GPU in it.

---

### Post by Redalien0304 on 2019-10-23
not sure if it does or not? either way still do not know to get rid of Screen Flicker?

Thanks for any help

---

### Post by him610 on 2019-10-25
Please show results, within code tags, of *inxi -F*

---

### Post by Redalien0304 on 2019-10-26
```
 

craig@Latitude-E6500:~$  inxi -FSystem:    Host: Latitude-E6500 Kernel: 5.0.0-32-generic x86_64 bits: 64
           Desktop: Cinnamon 4.0.9  Distro: Ubuntu 18.04.3 LTS
Machine:   Device: portable System: Dell product: Latitude E6500 serial: N/A
           Mobo: Dell model: 0K879F serial: N/A
           BIOS: Dell v: A29 date: 06/04/2013
Battery    BAT0: charge: 45.9 Wh 100.0% condition: 45.9/57.7 Wh (80%)
           hidpp__0: charge: N/A condition: NA/NA Wh
CPU:       Dual core Intel Core2 Duo P8600 (-MCP-) cache: 3072 KB
           clock speeds: max: 2401 MHz 1: 1054 MHz 2: 1241 MHz
Graphics:  Card: NVIDIA G98M [Quadro NVS 160M]
           Display Server: x11 (X.Org 1.20.4 ) driver: nvidia
           Resolution: 1440x900@59.98hz
           OpenGL: renderer: Quadro NVS 160M/PCIe/SSE2
           version: 3.3.0 NVIDIA 340.107
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k5.0.0-32-generic
Network:   Card-1: Intel 82567LM Gigabit Network Connection driver: e1000e
           IF: enp0s25 state: down mac: 00:21:70:d7:e1:75
           Card-2: Broadcom and subsidiaries BCM4312 802.11b/g LP-PHY
           driver: wl
           IF: wlp12s0 state: up mac: 00:22:5f:60:33:ac
Drives:    HDD Total Size: 1390.3GB (46.9% used)
           ID-1: /dev/sda model: ST9750420AS size: 750.2GB
           ID-2: /dev/sdb model: Hitachi_HTS54756 size: 640.1GB
Partition: ID-1: / size: 246G used: 59G (26%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A gpu: 63C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 242 Uptime: 29 min Memory: 2095.5/3930.8MB
           Client: Shell (bash) inxi: 2.3.56 
craig@Latitude-E6500:~$ 

 
```

---

### Post by Redalien0304 on 2019-11-09
Bump Anyone??

---

### Post by Bashing-om on 2019-11-09
Redalien0304; Wonder of wonders -

It is Nvidia graphics :)

Is the Nvidia module fully installed :

What shows - for diagnostic purposes:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia
cat /var/log/gpu-manager.log

```

[INDENT][INDENT]maybe not-so-yes
[/INDENT][/INDENT]

---

### Post by Redalien0304 on 2019-11-10
No sudo kshw -C display[sudo] password for craig: 
sudo: kshw: command not found ?
I assume yo meant sudo lshw -C Display ?

```

sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: G98M [Quadro NVS 160M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:27 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:df00(size=128) memory:c0000-dffff

craig@Latitude-E6500:~$ dpkg -l | grep -i nvidia
ii  libcuda1-340                               340.107-0ubuntu0.18.04.3                     amd64        NVIDIA CUDA runtime library
ii  nouveau-firmware                           20091212-0ubuntu1                            all          Firmware for nVidia graphics cards
ii  nvidia-340                                 340.107-0ubuntu0.18.04.3                     amd64        NVIDIA binary driver - version 340.107
ii  nvidia-opencl-icd-340                      340.107-0ubuntu0.18.04.3                     amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                            390.77-0ubuntu0.18.04.1                      amd64        Tool for configuring the NVIDIA graphics driver
craig@Latitude-E6500:~$ lsmod | grep nvidia
nvidia_uvm             36864  0
nvidia              10563584  58 nvidia_uvm
drm                   483328  3 nvidia
craig@Latitude-E6500:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-32-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/5.0.0-32-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:6eb
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do
craig@Latitude-E6500:~$ 

```

---

### Post by Bashing-om on 2019-11-10
Redalien0304; Well !

Nvidia recommends the 390 version driver for that NVS card:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

I do suggest a purge of the 340 driver:
Reboot and insure that "secure boot"  is disabled in bios; then once more at the desktop run:
```

sudo apt remove --purge nvidia-*

```

and make sure that the nvidia config file(s) do not exist now:
```

ls -al /etc/X11/xorg.conf /usr/share/X11/xorg.conf.d/*.conf

```
If needed a new file will be generated.

And the tried and true:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

Reboot once more to see the effect.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Redalien0304 on 2019-11-11
Ok did Purge & Install of Nvidia driver. Boots Fine till Login screen, then cannot do anything. keyboard, mouse, is froze from what i can tell. No Keyboard Shortcuts to Terminal Work, & mouse cursor does not move.

here is terminal output:
```
craig@Latitude-E6500:~$ sudo apt remove --purge nvidia-*[sudo] password for craig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia-*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia-*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia-*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-libs-i386:i386' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-common-430' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-common-435' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-driver' for glob 'nvidia-*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia-*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia-*'
Note, selecting 'nvidia-utils' for glob 'nvidia-*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia-*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia-*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia-*'
Note, selecting 'nvidia-smi' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia-*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia-*'
Note, selecting 'nvidia-utils-430' for glob 'nvidia-*'
Note, selecting 'nvidia-utils-435' for glob 'nvidia-*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia-*'
Note, selecting 'nvidia-prime' for glob 'nvidia-*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia-*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia-*'
Note, selecting 'nvidia-dkms-430' for glob 'nvidia-*'
Note, selecting 'nvidia-dkms-435' for glob 'nvidia-*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-nsight' for glob 'nvidia-*'
Note, selecting 'nvidia-common' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-no-dkms-430' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-no-dkms-435' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia-*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia-*'
Note, selecting 'nvidia-compute-utils-430' for glob 'nvidia-*'
Note, selecting 'nvidia-compute-utils-435' for glob 'nvidia-*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia-*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-current' for glob 'nvidia-*'
Note, selecting 'nvidia-profiler' for glob 'nvidia-*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia-*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-430' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-435' for glob 'nvidia-*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia-*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia-*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia-*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia-*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia-*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia-*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia-*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia-*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-430' for glob 'nvidia-*'
Note, selecting 'nvidia-headless-435' for glob 'nvidia-*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia-*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia-*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia-*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia-*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia-*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia-*'
Note, selecting 'nvidia-304' for glob 'nvidia-*'
Note, selecting 'nvidia-310' for glob 'nvidia-*'
Note, selecting 'nvidia-313' for glob 'nvidia-*'
Note, selecting 'nvidia-319' for glob 'nvidia-*'
Note, selecting 'nvidia-325' for glob 'nvidia-*'
Note, selecting 'nvidia-331' for glob 'nvidia-*'
Note, selecting 'nvidia-334' for glob 'nvidia-*'
Note, selecting 'nvidia-337' for glob 'nvidia-*'
Note, selecting 'nvidia-340' for glob 'nvidia-*'
Note, selecting 'nvidia-343' for glob 'nvidia-*'
Note, selecting 'nvidia-346' for glob 'nvidia-*'
Note, selecting 'nvidia-349' for glob 'nvidia-*'
Note, selecting 'nvidia-352' for glob 'nvidia-*'
Note, selecting 'nvidia-355' for glob 'nvidia-*'
Note, selecting 'nvidia-358' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia-*'
Note, selecting 'nvidia-361' for glob 'nvidia-*'
Note, selecting 'nvidia-364' for glob 'nvidia-*'
Note, selecting 'nvidia-367' for glob 'nvidia-*'
Note, selecting 'nvidia-375' for glob 'nvidia-*'
Note, selecting 'nvidia-378' for glob 'nvidia-*'
Note, selecting 'nvidia-381' for glob 'nvidia-*'
Note, selecting 'nvidia-384' for glob 'nvidia-*'
Note, selecting 'nvidia-387' for glob 'nvidia-*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia-*'
Note, selecting 'nvidia-390' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia-*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-source-430' for glob 'nvidia-*'
Note, selecting 'nvidia-kernel-source-435' for glob 'nvidia-*'
Note, selecting 'nvidia-settings' for glob 'nvidia-*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia-*'
Package 'nvidia-304' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-compute-utils-435' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-dkms-435' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-driver-435' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-435' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-435' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-common-435' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-kernel-source-435' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
Package 'nvidia-utils-435' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libcuda1-340 libxnvctrl0 ocl-icd-libopencl1 pkg-config
  screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-340* nvidia-opencl-icd-340* nvidia-settings*
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 305 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 258884 files and directories currently installed.)
Removing nvidia-340 (340.107-0ubuntu0.18.04.3) ...
Stopping nvidia-persistenced
nvidia-persistenced: no process found
Done.
Removing all DKMS Modules
Done.
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libGL.so to /usr/lib/x86_64-linux-gnu/libGL.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so to /usr/lib/x86_64-linux-gnu/libGL.so.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libEGL.so.1 to /usr/lib/x86_64-linux-gnu/libEGL.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libEGL.so.1 to /usr/lib/x86_64-linux-gnu/libEGL.so.1.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libEGL.so.1 to /usr/lib/i386-linux-gnu/libEGL.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libEGL.so.1 to /usr/lib/i386-linux-gnu/libEGL.so.1.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libEGL.so to /usr/lib/x86_64-linux-gnu/libEGL.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libEGL.so to /usr/lib/x86_64-linux-gnu/libEGL.so.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libEGL.so to /usr/lib/i386-linux-gnu/libEGL.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libEGL.so to /usr/lib/i386-linux-gnu/libEGL.so.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so to /usr/lib/x86_64-linux-gnu/libGLESv2.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so to /usr/lib/x86_64-linux-gnu/libGLESv2.so.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGLESv2.so to /usr/lib/i386-linux-gnu/libGLESv2.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGLESv2.so to /usr/lib/i386-linux-gnu/libGLESv2.so.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so.2 to /usr/lib/x86_64-linux-gnu/libGLESv2.so.2.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so.2 to /usr/lib/x86_64-linux-gnu/libGLESv2.so.2.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGLESv2.so.2 to /usr/lib/i386-linux-gnu/libGLESv2.so.2.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGLESv2.so.2 to /usr/lib/i386-linux-gnu/libGLESv2.so.2.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340'
diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340'
diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340
Removing 'diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340'
INFO:Disable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing nvidia-opencl-icd-340 (340.107-0ubuntu0.18.04.3) ...
Removing nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-32-generic
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
(Reading database ... 258575 files and directories currently installed.)
Purging configuration files for nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Purging configuration files for nvidia-340 (340.107-0ubuntu0.18.04.3) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-opencl-icd-340 (340.107-0ubuntu0.18.04.3) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-32-generic
craig@Latitude-E6500:~$ ls -al /etc/X11/xorg.conf /usr/share/X11/xorg.conf.d/*.conf
-rw-r--r-- 1 root root 1389 Sep  1 17:23 /etc/X11/xorg.conf
-rw-r--r-- 1 root root   92 May 29 03:19 /usr/share/X11/xorg.conf.d/10-amdgpu.conf
-rw-r--r-- 1 root root 1350 May  2  2019 /usr/share/X11/xorg.conf.d/10-quirks.conf
-rw-r--r-- 1 root root   92 May 29 03:19 /usr/share/X11/xorg.conf.d/10-radeon.conf
-rw-r--r-- 1 root root  945 Nov 27  2018 /usr/share/X11/xorg.conf.d/40-libinput.conf
craig@Latitude-E6500:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:3 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu bionic InRelease
Hit:4 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:5 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:7 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu bionic InRelease       
Hit:8 http://archive.ubuntu.com/ubuntu bionic-backports InRelease              
Hit:9 http://ppa.launchpad.net/hamishmb/myppa/ubuntu bionic InRelease          
Hit:10 http://archive.ubuntu.com/ubuntu bionic-security InRelease       
Hit:11 http://ppa.launchpad.net/mkusb/ppa/ubuntu bionic InRelease              
Hit:12 http://archive.ubuntu.com/ubuntu bionic-updates InRelease               
Hit:13 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease         
Reading package lists... Done                      
craig@Latitude-E6500:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libcuda1-340 libxnvctrl0 ocl-icd-libopencl1 pkg-config
  screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libsgutils2-2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.8 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libsgutils2-2 amd64 1.42-2ubuntu1.18.04.1 [59.8 kB]
Fetched 59.8 kB in 1s (84.3 kB/s)      
(Reading database ... 258572 files and directories currently installed.)
Preparing to unpack .../libsgutils2-2_1.42-2ubuntu1.18.04.1_amd64.deb ...
Unpacking libsgutils2-2 (1.42-2ubuntu1.18.04.1) over (1.42-2ubuntu1) ...
Setting up libsgutils2-2 (1.42-2ubuntu1.18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
craig@Latitude-E6500:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  nvidia-opencl-icd-340 nvidia-settings
The following NEW packages will be installed:
  nvidia-340 nvidia-opencl-icd-340 nvidia-settings
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.7 MB of archives.
After this operation, 305 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 nvidia-340 amd64 340.107-0ubuntu0.18.04.3 [51.9 MB]
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 nvidia-opencl-icd-340 amd64 340.107-0ubuntu0.18.04.3 [8,841 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 nvidia-settings amd64 390.77-0ubuntu0.18.04.1 [944 kB]
Fetched 61.7 MB in 28s (2,167 kB/s)                                            
Selecting previously unselected package nvidia-340.
(Reading database ... 258572 files and directories currently installed.)
Preparing to unpack .../nvidia-340_340.107-0ubuntu0.18.04.3_amd64.deb ...
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so to /usr/lib/x86_64-linux-gnu/libGL.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libEGL.so.1 to /usr/lib/x86_64-linux-gnu/libEGL.so.1.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libEGL.so.1 to /usr/lib/i386-linux-gnu/libEGL.so.1.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libEGL.so to /usr/lib/x86_64-linux-gnu/libEGL.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libEGL.so to /usr/lib/i386-linux-gnu/libEGL.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so to /usr/lib/x86_64-linux-gnu/libGLESv2.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGLESv2.so to /usr/lib/i386-linux-gnu/libGLESv2.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so.2 to /usr/lib/x86_64-linux-gnu/libGLESv2.so.2.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGLESv2.so.2 to /usr/lib/i386-linux-gnu/libGLESv2.so.2.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.distrib by nvidia-340'
Adding 'diversion of /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/x86_64-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340'
Adding 'diversion of /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1 to /usr/lib/i386-linux-gnu/libGLESv1_CM.so.1.distrib by nvidia-340'
Unpacking nvidia-340 (340.107-0ubuntu0.18.04.3) ...
Selecting previously unselected package nvidia-opencl-icd-340.
Preparing to unpack .../nvidia-opencl-icd-340_340.107-0ubuntu0.18.04.3_amd64.deb ...
Unpacking nvidia-opencl-icd-340 (340.107-0ubuntu0.18.04.3) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_390.77-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Setting up nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Setting up nvidia-340 (340.107-0ubuntu0.18.04.3) ...
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 119) ...
Adding new group `nvidia-persistenced' (GID 129) ...
Adding new user `nvidia-persistenced' (UID 119) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-340-340.107 DKMS files...
Building for 5.0.0-32-generic
Building for architecture x86_64
Building initial module for 5.0.0-32-generic
Done.


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-32-generic/updates/dkms/


nvidia_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-32-generic/updates/dkms/


depmod......


DKMS: install completed.
Setting up nvidia-opencl-icd-340 (340.107-0ubuntu0.18.04.3) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-32-generic
craig@Latitude-E6500:~$ 

```

So now i cannot login on that in that partition. I can still Access it from my other Partition
Luckily i Have another Install of Cinnamon on a Different Partition.

---

### Post by Bashing-om on 2019-11-11
Redalien0304; Huh ??

The system re-installing the old 340 version driver is presently a mystery to me - The system I expected to choose the 390 version driver.

Also in the 18.04 release I did not expect /etc/X11/xorg.conf to exist, as the config has changed to /usr/share/X11/xorg.conf.d/ .

I also do not see that the old config file was removed.

Is an OEM driver install at play here ( A NO NO ); 
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


what shows:
```

sudo find / -name "NVIDIA-Linux-*"

```

Secure boot disabled in bios ? While we do trust the driver install, the system is doing its job and will not install 3rd party software.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by Redalien0304 on 2019-11-11
No Secure Boot. Secure boot you Mean EFI? This laptop doe not have EFI.
[COLOR=#000000]Boots Fine till Login screen, then cannot do anything. keyboard, mouse, is froze from what i can tell. No Keyboard Shortcuts to Terminal Work, & mouse cursor does not move.[/COLOR]

---

### Post by mc4man on 2019-11-15
> **Bashing-om said:**
> Redalien0304; Huh ??

The system re-installing the old 340 version driver is presently a mystery to me - The system I expected to choose the 390 version driver.

Actually that card can only use the legacy driver (it was released in 2008), seen here
[https://www.nvidia.com/Download/driverResults.aspx/135161/en-us](https://www.nvidia.com/Download/driverResults.aspx/135161/en-us)
(- when searching it is as shown in screen...

Now i don't always believe  nvidia or ubuntu drivers but in this case probably correct  (for example my 755m shouldn't use the 4.30/4.40 driver but it does quite fine..

Maybe try doing a fresh install with a 18.04.1 image (4.15 kernel no HWE..) , maybe it'll treat you better..

(- if you want to try the 390 it couldn't get worse..., do a purge followed by autoremove 1st. before installing, maybe also a reboot into nouveau

---

### Post by Redalien0304 on 2019-11-16
Possibly not sure not sure if i want to go that route yet?
Is it possible to Repair This 1st?
I cannot login because keyboard & mouse appear to be frozen?
I can ONLY log into Root from Advanced Repair options.
which i do not know what to do from There??

---

