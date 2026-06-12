---
title: "AMD A10 7870k (Kaveri) driver support"
date: 2019-04-11
forum: Hardware
---

### Post by arieleoar on 2019-04-11
Hi everyone!

I've a question, here i got an AMD's APU A10 7870k which is supported by default by mesa drivers and don't need any installation of proprietary drivers, but looking trough the specs page in amd official page it says that the integrated gpu has support for vulkan api.
Recently i've upgraded the mesa drivers to 19 with the padoka ppa and installed the latest mesa-vulkan-drivers but when i run *vulkaninfo* i keep getting:

> 
===========
VULKAN INFO
===========

Vulkan Instance Version: 1.1.70

/build/vulkan-UL09PJ/vulkan-1.1.70+dfsg1/demos/vulkaninfo.c:2700: failed with VK_ERROR_INITIALIZATION_FAILED



so reading through some forums the recommendation is to use AMDGPU DRM instead RADEON DRM included by default, but the fact is that if the driver AMDGPU has to be installed from proprietary i've not found it in the amd official web and only points to crimson fglrx deprecated drivers.

And the cuestion is, does someone has more information about this apu-gpu support? someone knows how to activate vulkan support?

(The finality of this question is for using DXVK with wine so it can use dx10, 11 and 12 instructions).

My actual setup is:
Ubuntu 18.04.2 LTS
Kernel 4.15.0-47-lowlatency
Mesa 19
APU AMD A10 7870K with Radeon R7 Graphics (Kaveri)

> 
sudo lshw -c video
  *-display                 
       descripción: VGA compatible controller
       producto: Kaveri [Radeon R7 Graphics]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 1
       información del bus: pci@0000:00:01.0
       versión: d4
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
       configuración: driver=radeon latency=0
       recursos: irq:41 memoria:c0000000-cfffffff memoria:d0000000-d07fffff ioport:f000(size=256) memoria:feb00000-feb3ffff memoria:c0000-dffff


---

### Post by arieleoar on 2019-04-12
So, i've been looking in some forums that to enable amdgpu DRM one must add commands to grub default configuration located in /etc/default/grub.
Then i've modified them and managed to boot my pc *but* i can only login with wayland. Whatever, it's seeing nice and managed to activate vulkan support, so i've tested it and works flawlessly.

To the point, the modifications in grub are:

> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.cik_support=0 amdgpu.cik_support=1 radeon.si_support=0 amdgpu.si_support=1"


And the output of lshw:

> 
sudo lshw -c video
  *-display                 
       descripción: VGA compatible controller
       producto: Kaveri [Radeon R7 Graphics]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 1
       información del bus: pci@0000:00:01.0
       versión: d4
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
       configuración: driver=amdgpu latency=0
       recursos: irq:43 memoria:c0000000-cfffffff memoria:d0000000-d07fffff ioport:f000(size=256) memoria:feb00000-feb3ffff memoria:c0000-dffff


And finally i've tested vulkan with [https://github.com/srmojuze/Refresh2025/releases](https://github.com/srmojuze/Refresh2025/releases), not meant to be like glxgears but is usefull to test vulkan

The there is another question, now that i'm using wayland some apps and programs can't open "display :0", what this means? sorry the question, but i've never used wayland so i'dont know how it works.

---

### Post by mega1232 on 2019-05-03
[**[COLOR=#000000]arieleoar[/COLOR]**]("https://ubuntuforums.org/member.php?u=1930994")       Thank you so much, very much helped.  GPU AMD 7850 CPU i5-3470

---

### Post by arieleoar on 2019-05-05
Hi Again!

@mega1232 you are welcome!

Then i've been messing with the session managers to discover that when i wanted to run X11 it would look back to Radeon Drm and find nothing so resuming (tooks me days):

* i've blacklisted radeon module in /etc/modprobe.d/blacklist.conf using "blacklist radeon" line
* Then renamed the /usr/share/X11/xorg.conf.d files named with radeon to .conf.old (for backup)

So, restarting again i got to the user selection screen and opened x session smoothly. I've gone through this work because when the kernel did the last update to 4-15-0-48 from -47 made things worse, it doesn't even opened wayland nor x11.

Regards!

---

### Post by mega1232 on 2019-05-09
[**[COLOR=#000000]arieleoar[/COLOR]**]("https://ubuntuforums.org/member.php?u=1930994") 
[LEFT][COLOR=#212121][FONT=arial]Thank you once again for sharing useful instructions. This is very necessary for beginners like me and other people. Good luck.[/FONT][/COLOR][/LEFT]

---

