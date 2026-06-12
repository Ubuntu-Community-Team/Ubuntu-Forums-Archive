---
title: "External displays not working with Lenovo W520, NVidia Quadro 1000M, NVidia Optimus"
date: 2018-07-17
forum: Hardware
---

### Post by unix001 on 2018-07-17
I am under the quest to get the NVIDIA Optimus working for the Lenovo W520 laptop under Ubuntu 18.04. My main purpose is to use the laptop for AI development. I have managed to complete the whole installation of the nvidia packages, but I am having troubles to connect an external display (HP 23er). It is also worthy to mention that the laptop works all right with the same external display using nouveau drivers, and that this issue with VGA displays appears to be pervasive in all linux distributions.


After several trial and error attempts, in which I have formatted the computer several times to reinstall Ubuntu 18.04 many times, I have been unable to find any solution. I have been reading in several forums solutions for other distros and older ubuntu versions as well. I have also tried to install the latest driver directly from NVIDIA, but it gave me this error, [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053) , most likely related to the fact that I accepted overriding the package [COLOR=#333333][FONT=monospace]libglvnd.[/FONT][/COLOR]
I have also tried bumblebee, with similar results.


So, this is the process I have followed after a clean install: 


1 - Removed any old nvidia installation that there might be (just in case) with "apt purge nvidia*"
2 - Added noveau drivers to a blacklist in /etc/modprobe.d/blacklist-nvidia-nouveau.conf:
    blacklist nouveau
    blacklist lbm-nouveau
    options nouveau modeset=0
    alias nouveau off
    alias lbm-nouveau off
3 - Disabled the nouveau kernel with "echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf"


4 - Built the new kernel with "sudo update-initramfs -u"
5 - "reboot"


After this, I can see with the NVIDIA xserver settings GUI that the X Server Display Configuration detects "Prime Display". There is a message, saying that PRIME displays cannot be controlled with nvidia-settings and must be controlled with an external RandR. The detect display button does not appear to work. The GUI gives me an option to choose between PRIME DISPLAY and X Screen 0, but there is no much difference.


So, I try "xrandr -q" with the VGA cable connected, and it prompts: "VGA-1-1 disconnected (normal left inverted right x axis y axis)"


You can find below other useful information that I can see with other commands.


```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

```

```
uname -a
Linux thinkpad 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
lspci -k | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Lenovo 2nd Generation Core Processor Family Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915


01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [Quadro 1000M] (rev a1)
    Subsystem: Lenovo GF108GLM [Quadro 1000M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```

```
 glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro 1000M/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 390.77
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 390.77
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 390.77
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

```



```
sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GF108GLM [Quadro 1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:38 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:6000(size=64) memory:c0000-dffff

```

/etc/X11/xorg.conf is empty. The BIOS option for the graphics card is set to OPTIMUS. 


I would be very grateful if someone could give me a hand to figure it out what I am doing wrong, or how can I get the external monitor working. Let me know if you need further information. 


Thank you very much in advance. 








[ATTACH=CONFIG]280433[/ATTACH][ATTACH=CONFIG]280434[/ATTACH]

---

### Post by sohoming on 2018-07-18
I have the same problem on my Dell M4800.... (Quadro K2100M). I can't fix it, too.

---

### Post by wildmanne39 on 2018-07-18
Hello and welcome to the forum sohoming, if you need support please create your own thread and do not post in someone else's.

Thanks

---

### Post by unix001 on 2018-07-19
Just in case it helps. I forgot mentioning that seting in the BIOS the display to Discrete mode only (and disabling the detection of optimus technology) makes it work. The solution I am looking for is that in which optimus runs fine (preferrably using prime-select).

---

### Post by derastov on 2018-09-12
Setting the BIOS mode to "Discrete" also worked for me, however after I undock and suspend my laptop, when it wakes up without an external display it shows a black screen and doesn't react to keyboard commands. What made it reliably work for me in Optimus mode was switching to LightDM. I also renamed my xorg.conf just in case.

For reference, here are two very detailed threads outlining some other potential solutions: [https://devtalk.nvidia.com/default/topic/1035768/linux/ubuntu-18-04-can-t-see-second-monitor/](https://devtalk.nvidia.com/default/topic/1035768/linux/ubuntu-18-04-can-t-see-second-monitor/), [https://devtalk.nvidia.com/default/topic/1032482/optimus-on-ubuntu-18-04-is-a-step-backwards-but-i-found-the-first-good-solution/](https://devtalk.nvidia.com/default/topic/1032482/optimus-on-ubuntu-18-04-is-a-step-backwards-but-i-found-the-first-good-solution/)

---

