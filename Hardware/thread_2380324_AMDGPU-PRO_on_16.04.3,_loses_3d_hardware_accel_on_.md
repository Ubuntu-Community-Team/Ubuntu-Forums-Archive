---
title: "AMDGPU-PRO on 16.04.3, loses 3d hardware accel on install"
date: 2017-12-15
forum: Hardware
---

### Post by dpcole72 on 2017-12-15
Howdy!  My Dell Latitude e5570, with 16GB RAM, 1TB storage, Intel HD530 graphics and AMD R7 M370 hybrid GPU, will seemingly install AMDGPU-PRO 17.40 onto my Ubuntu 16.04.3 partition  without issue, but post-reboot, running lspci, the Intel driver is still in effect but all my apps that use 3D acceleration - like VMWare -  lose their functionality.  GLXINFO and GLXGEARS can't find the double-buffered RGB source as well so something's gone abend for sure.

Removing the Intel driver entirely and rebooting has no effect. 

I did some checking, supposedly the R7 M3x0 series is said to be compatible.  And yet, after installing AMDGPU Pro, the AMD chipset is still not recognized as the M370 - just an older version of the 8000 series.

Anyone else having install problems with the R7 M370 mobile chipset?

Thanks!

---

### Post by sccman on 2017-12-15
Umm the best place to check would be the logs. Can you find any logs related to AMDGPU, or at least the Xorg.0.log files? If you can skim the entries from the bottom of the files up, it may give you a clue related to your issue.

The log files are in /var/log/

---

### Post by Yellow Pasque on 2017-12-16
Have you tried using the open source radeon driver with DRI_PRIME? That's probably what you should be using unless you need a feature of the Pro driver that the open source driver doesn't offer.

If you still want to use the Pro driver, did you run the install script with"--px" option and switch to the AMD card using the script AMD provides?
EDIT: example [https://askubuntu.com/a/949124](https://askubuntu.com/a/949124)

---

### Post by dpcole72 on 2017-12-17
Thanks, everyone!

I had already reformatted before thinking about viewing the logs.  But it gave me a clean slate to tinker, anyway.

I tried the open source version after reading up on Debian's site, but on reboot the computer froze on the login screen.

I reformatted, then tried amdgpu-pro (17.40) with --px parameter included...  that seemed to work, I do see the amdgpu driver running in the background.

I tried the performance mode as instructed in the other thread you linked to,  Temüjin.  I logged out then back in.  Then I started a VM.  

No problems yet so I did some command line testing with the VM up.

glxinfo | grep OpenGL and that reveals what I wanted to see - I think, I'm not sure why "extension AMDGPU" missing on display ":0.0"...  is that a problem? (same thing happens after I close down VMWare)


GLXinfo|grep output - it definitely sees thew video chipset model name:

Xlib:  extension "AMDGPU" missing on display ":0.0".
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon (TM) R7 M370
OpenGL core profile version string: 4.5.13496 Core Profile Context 17.40.3.12
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
Xlib:  extension "AMDGPU" missing on display ":0.0".
OpenGL version string: 4.5.13496 Compatibility Profile Context 17.40.3.12
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
Xlib:  extension "AMDGPU" missing on display ":0.0".
OpenGL ES profile version string: 4.5.13496 Compatibility Profile Context 17.40.3.12
OpenGL ES profile shading language version string: 4.50
OpenGL ES profile extensions:

$


Is the "extension AMDGPU missing" a problem?  It almost looks as if it's running off the AMD driver (yay, discrete RAM!)

Thanks!



Other info:





lspci -k output:

00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: Dell Skylake Integrated Graphics
	Kernel driver in use: i915
	Kernel modules: i915
.
.
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev 81)
	Subsystem: Dell Mars [Radeon HD 8670A/8670M/8750M]
	Kernel driver in use: amdgpu
	Kernel modules: radeon, amdgpu




lshw -c video output:

  *-display               
       description: Display controller
       product: Mars [Radeon HD 8670A/8670M/8750M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:129 memory:d0000000-dfffffff memory:ef200000-ef23ffff ioport:e000(size=256) memory:ef240000-ef25ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:130 memory:ee000000-eeffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff



modinfo amdgpu output:

modinfo amdgpu
filename:       /lib/modules/4.10.0-42-lowlatency/updates/dkms/amdgpu.ko
version:        17.40.3.12
license:        GPL and additional rights
description:    AMD GPU
author:         AMD linux driver team





lspci -nnk 
output:

 lspci -nnk | grep -i vga -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake Integrated Graphics [8086:191b] (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: Dell Skylake Integrated Graphics [1028:06df]
	Kernel driver in use: i915

---

### Post by Yellow Pasque on 2017-12-18
If I had to guess, you get the message about missing extension because glxinfo looks in the wrong dir before it finds the libs? As long as it finds them, you should be okay.

---

### Post by dpcole72 on 2018-01-07
That makes sense and the error isn't consistent either.  I probably could look into paths but as the system is working, I'm not going to tinker too much.  I'm just grateful and happy the chipset is recognized and utilized. 

Thanks again for your time and help!!

---

