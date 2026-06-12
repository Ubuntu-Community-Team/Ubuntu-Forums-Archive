---
title: "FirePro w5000 Missing Driver"
date: 2021-08-13
forum: Hardware
---

### Post by arcane-coder on 2021-08-13
I would appreciate some guidance/advice/direction in setting up w5000 with Ubuntu 20.04 lts. I am 12+ hours on this problem and stuck I have been using linux distros like Fedora and Mint for a couple years. I am new to Ubuntu and I have never installed a discrete gpu before.

```
X8SIE:~$sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Pitcairn LE GL [FirePro W5000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fb4c0000-fb4fffff ioport:c000(size=256) memory:fb4a0000-fb4bffff
  *-display
       description: VGA compatible controller
       product: MGA G200eW WPCM450
       vendor: Matrox Electronics Systems Ltd.
       physical id: 3
       bus info: pci@0000:05:03.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=mgag200 latency=64 maxlatency=32 mingnt=16
       resources: irq:23 memory:fa000000-faffffff memory:fb7fc000-fb7fffff memory:fb800000-fbffffff memory:c0000-dffff

```

```
X8SIE:~$ inxi -Fxz
System:
  Kernel: 5.11.0-7620-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Supermicro model: X8SIE v: 0123456789 
  serial: <filter> BIOS: American Megatrends v: 1.2a 
  date: 06/27/2012 
CPU:
  Topology: Quad Core model: Intel Xeon X3470 bits: 64 
  type: MT MCP arch: Nehalem rev: 5 L2 cache: 8192 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 46930 
  Speed: 2267 MHz min/max: 1200/2933 MHz Core speeds (MHz): 
  1: 2267 2: 2689 3: 2602 4: 1566 5: 2588 6: 1353 7: 2349 8: 1948 
Graphics:
  Device-1: AMD Pitcairn LE GL [FirePro W5000] vendor: Dell 
  driver: N/A bus ID: 01:00.0 
  Device-2: Matrox Systems MGA G200eW WPCM450 vendor: Super Micro 
  driver: mgag200 v: kernel bus ID: 05:03.0 
  Display: wayland server: X.Org 1.20.11 driver: mga 
  unloaded: fbdev,intel,modesetting,vesa 
  resolution: 1280x1024~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 10.0.0 128 bits) 
  v: 3.3 Mesa 20.0.5 direct render: Yes 
Audio:
  Device-1: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio 
  [Radeon HD 7000 Series] 
  vendor: Dell driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.11.0-7620-generic 
Network:
  Device-1: Intel 82574L Gigabit Network vendor: Super Micro 
  driver: e1000e v: kernel port: dc00 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: Intel 82574L Gigabit Network vendor: Super Micro 
  driver: e1000e v: kernel port: ec00 bus ID: 04:00.0 
  IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 119.24 GiB used: 15.44 GiB (12.9%) 
  ID-1: /dev/sda vendor: Micron model: M600 MTFDDAY128MBF 
  size: 119.24 GiB temp: 41 C 
Partition:
  ID-1: / size: 116.38 GiB used: 15.44 GiB (13.3%) fs: ext4 
  dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 47.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 242 Uptime: 1h 14m Memory: 9.72 GiB 
  used: 1.44 GiB (14.9%) Init: systemd runlevel: 5 Compilers: 
  gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
```

```
X8SIE:~$inxi -G
Graphics:
  Device-1: AMD Pitcairn LE GL [FirePro W5000] driver: N/A 
  Device-2: Matrox Systems MGA G200eW WPCM450 driver: mgag200 
  v: kernel 
  Display: wayland server: X.Org 1.20.11 driver: mga 
  unloaded: fbdev,intel,modesetting,vesa 
  resolution: 1280x1024~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 10.0.0 128 bits) 
  v: 3.3 Mesa 20.0.5 

```

```
X8SIE:~$ sudo apt install dkms 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.8.1-5ubuntu2).
dkms set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Removing old amdgpu-5.6.0.15-1098277 DKMS files...

------------------------------
Deleting module version: 5.6.0.15-1098277
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.11.0-7620-generic
Building for architecture x86_64
Building initial module for 5.11.0-7620-generic
ERROR (dkms apport): kernel package linux-headers-5.11.0-7620-generic is not supported
Error! Bad return status for module build on kernel: 5.11.0-7620-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                     Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
sh: 0: getcwd() failed: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
X8SIE:~/Downloads/fglrx-15.302.2301$ ./amd-driver-installer-15.302.2301-x86.x86_64.run 
Created directory fglrx-install.wujCk1
Verifying archive integrity... All good.
Uncompressing AMD Proprietary Driver-15.302.2301...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Display does not support owner-change; copy/paste will be broken!
# Option &#8220;-e&#8221; is deprecated and might be removed in a later version of gnome-terminal.
# Use &#8220;-- &#8221; to terminate the options and put the command line to execute after it.
=====================================================================
 AMD  Proprietary Driver Installer/Packager 
=====================================================================

error: Detected X Server version 'XServer _64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib32:XServer _64a:none:5.11.0-7620-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.wujCk1
```

Thanks for reading all this. I have tried a lot more than the above. I even [mistakenly] installed and attempted to use system76-amd! I am at wit's end and just want to give up. Anyone have any suggestions? I am hesitant to downgrade to linux kernel 5.6, but if that and/or ubuntu 18.04 are necessary, I will do that. I also tried booting unsuccesfully from a ubuntu 20.04 lts iso usb stick, but the kernel threw fatal erros such as "radeon 0000:01:00.0: failed VCE resume (-22)." which prevented booting to the installer shell. I can try booting an ubuntu 18.04 lts iso, and see if that works, before downgrading. I also think it might be worth trying Pop_os! iso on a thumb drive. 

I am open to suggestions, even really stupid ones right now. I'm going to cry myself to sleep in the fetal position meanwhile.

---

### Post by arcane-coder on 2021-08-13
```
X8SIE:~$ sudo apt upgrade dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.8.1-5ubuntu2).
Calculating upgrade... Done
The following packages will be upgraded:
  amdgpu-pro-pin python3-distupgrade ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 138 kB/144 kB of archives.
After this operation, 6,144 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-pin 21.10-1263777 [6,272 B]
Get:2 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-gtk all 1:20.04.36 [9,360 B]
Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-core all 1:20.04.36 [23.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 python3-distupgrade all 1:20.04.36 [104 kB]
Fetched 138 kB in 0s (340 kB/s)              
(Reading database ... 175452 files and directories currently installed.)
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a20.04.36_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:20.04.36) over (1:20.04.35) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a20.04.36_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:20.04.36) over (1:20.04.35) ...
Preparing to unpack .../python3-distupgrade_1%3a20.04.36_all.deb ...
Unpacking python3-distupgrade (1:20.04.36) over (1:20.04.35) ...
Preparing to unpack .../amdgpu-pro-pin_21.10-1263777_all.deb ...
Unpacking amdgpu-pro-pin (21.10-1263777) over (20.20-1098277) ...
Setting up python3-distupgrade (1:20.04.36) ...
Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Removing old amdgpu-5.6.0.15-1098277 DKMS files...

------------------------------
Deleting module version: 5.6.0.15-1098277
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.11.0-25-generic 5.11.0-7620-generic
Building for architecture x86_64
Building initial module for 5.11.0-25-generic
Error! Bad return status for module build on kernel: 5.11.0-25-generi
c (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more
 information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess re
turned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-release-upgrader-core (1:20.04.36) ...
No apport report written because the error message indicates its a fo
llowup error from a previous failure.
                                     Setting up amdgpu-pro-pin (21.10
-1263777) ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-d
oc ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-p
in ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-p
ro ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-p
ro-core ...
Installing new version of config file /etc/apt/preferences.d/amf-amdg
pu-pro ...
Installing new version of config file /etc/apt/preferences.d/appprofi
les-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/opencl-o
rca-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/opengl-a
mdgpu ...
Installing new version of config file /etc/apt/preferences.d/vulkan-a
mdgpu-pro ...
Setting up ubuntu-release-upgrader-gtk (1:20.04.36) ...
Processing triggers for man-db (2.9.1-1) ...
Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
X8SIE:~$ sudo apt upgrade amdgpu 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amdgpu is already the newest version (20.20-1098277).
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libopencl1-amdgpu-pro
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  ocl-icd-libopencl1-amdgpu-pro
The following packages will be upgraded:
  amdgpu-pin amdgpu-pro-core clinfo-amdgpu-pro
  opencl-orca-amdgpu-pro-icd
4 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/30.7 MB of archives.
After this operation, 3,482 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-pin 21.10-1263777 [2,712 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ amdgpu-pro-core 21.10-1263777 [5,548 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ ocl-icd-libopencl1-amdgpu-pro 21.10-1263777 [13.9 kB]
Get:4 file:/var/opt/amdgpu-pro-local ./ clinfo-amdgpu-pro 21.10-1263777 [30.8 kB]
Get:5 file:/var/opt/amdgpu-pro-local ./ opencl-orca-amdgpu-pro-icd 21.10-1263777 [30.6 MB]
(Reading database ... 175459 files and directories currently installed.)
Preparing to unpack .../amdgpu-pin_21.10-1263777_all.deb ...
Unpacking amdgpu-pin (21.10-1263777) over (20.20-1098277) ...
Preparing to unpack .../amdgpu-pro-core_21.10-1263777_all.deb ...
Unpacking amdgpu-pro-core (21.10-1263777) over (20.20-1098277) ...
Selecting previously unselected package ocl-icd-libopencl1-amdgpu-pro:amd64.
Preparing to unpack .../ocl-icd-libopencl1-amdgpu-pro_21.10-1263777_amd64.deb ...
Unpacking ocl-icd-libopencl1-amdgpu-pro:amd64 (21.10-1263777) ...
dpkg: error processing archive /var/opt/amdgpu-pro-local/./ocl-icd-libopencl1-amdgpu-pro_21.10-1263777_amd64.deb (--unpack):
 trying  to overwrite '/opt/amdgpu-pro/lib/x86_64-linux-gnu/libOpenCL.so.1',  which is also in package libopencl1-amdgpu-pro:amd64 20.20-109
8277
Preparing to unpack .../clinfo-amdgpu-pro_21.10-1263777_amd64.deb ...
Unpacking clinfo-amdgpu-pro (21.10-1263777) over (20.20-1098277) ...
Preparing to unpack .../opencl-orca-amdgpu-pro-icd_21.10-1263777_amd6
4.deb ...
Unpacking opencl-orca-amdgpu-pro-icd:amd64 (21.10-1263777) over (20.2
0-1098277) ...
Errors were encountered while processing:
 /var/opt/amdgpu-pro-local/./ocl-icd-libopencl1-amdgpu-pro_21.10-1263
777_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
X8SIE:~$ sudo apt upgrade amdgpu-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 clinfo-amdgpu-pro : Depends: ocl-icd-libopencl1-amdgpu-pro but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

```
X8SIE:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libopencl1-amdgpu-pro
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  ocl-icd-libopencl1-amdgpu-pro
The following NEW packages will be installed:
  ocl-icd-libopencl1-amdgpu-pro
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/13.9 kB of archives.
After this operation, 60.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/opt/amdgpu-pro-local ./ ocl-icd-libopencl1-amdgpu-pro 21.10-1263777 [13.9 kB]
(Reading database ... 175460 files and directories currently installed.)
Preparing to unpack .../ocl-icd-libopencl1-amdgpu-pro_21.10-1263777_amd64.deb ...
Unpacking ocl-icd-libopencl1-amdgpu-pro:amd64 (21.10-1263777) ...
dpkg: error processing archive /var/opt/amdgpu-pro-local/./ocl-icd-libopencl1-amdgpu-pro_21.10-1263777_amd64.deb (--unpack):
 trying  to overwrite '/opt/amdgpu-pro/lib/x86_64-linux-gnu/libOpenCL.so.1',  which is also in package libopencl1-amdgpu-pro:amd64 20.20-1098277
Errors were encountered while processing:
 /var/opt/amdgpu-pro-local/./ocl-icd-libopencl1-amdgpu-pro_21.10-1263777_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
X8SIE:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 clinfo-amdgpu-pro : Depends: ocl-icd-libopencl1-amdgpu-pro but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

```
X8SIE:~$ sudo apt purge amdgpu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 clinfo-amdgpu-pro : Depends: ocl-icd-libopencl1-amdgpu-pro but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

```
X8SIE:~$ sudo apt update
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg              
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg         
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:5 http://us.archive.ubuntu.com/ubuntu focal InRelease           
Hit:6 http://archive.canonical.com/ubuntu focal InRelease           
Get:7 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Hit:8 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease
Hit:9 https://download.sublimetext.com apt/stable/ InRelease        
Get:10 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:11 http://ppa.launchpad.net/system76-dev/stable/ubuntu focal InRelease [17.5 kB]
Fetched 346 kB in 1s (238 kB/s)                                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

```
X8SIE:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 clinfo-amdgpu-pro : Depends: ocl-icd-libopencl1-amdgpu-pro but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by arcane-coder on 2021-08-13
I'm going to try solutions I found at [https://community.amd.com/]("https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676") and elsewhere. I will report if I find a solution that works.

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of clinfo-amdgpu-pro:
 clinfo-amdgpu-pro depends on ocl-icd-libopencl1-amdgpu-pro; however:
  Package ocl-icd-libopencl1-amdgpu-pro:amd64 is not installed.

dpkg: error processing package clinfo-amdgpu-pro (--configure):
 dependency problems - leaving unconfigured
Setting up amdgpu-pin (21.10-1263777) ...
Installing new version of config file /etc/apt/preferences.d/amdgpu ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-core ...
Installing new version of config file /etc/apt/preferences.d/amdgpu-dkms ...
Installing new version of config file /etc/apt/preferences.d/gst-omx-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/libdrm-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/libdrm-amdgpu-common ...
Installing new version of config file /etc/apt/preferences.d/llvm-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/mesa-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/vulkan-amdgpu ...
Installing new version of config file /etc/apt/preferences.d/xserver-xorg-amdgpu-video-amdgpu ...
Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Removing old amdgpu-5.6.0.15-1098277 DKMS files...

------------------------------
Deleting module version: 5.6.0.15-1098277
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.11.0-25-generic 5.11.0-7620-generic
Building for architecture x86_64
Building initial module for 5.11.0-25-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms-firmware.0.crash'
Error! Bad return status for module build on kernel: 5.11.0-25-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up amdgpu-pro-core (21.10-1263777) ...
Setting up opencl-orca-amdgpu-pro-icd:amd64 (21.10-1263777) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Errors were encountered while processing:
 clinfo-amdgpu-pro
 amdgpu-dkms
 amdgpu

```

---

